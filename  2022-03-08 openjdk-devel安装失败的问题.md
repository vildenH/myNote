# 2022-03-08 openjdk-devel安装失败的问题

---

## 背景

自己的服务需要安装新版的openjdk去避免一些jdk的bug，结果发现了一很有意思的东西

正常的安装命令

>  yum install java-1.8.0-openjdk-devel

这样的安装方式会默认安装**最新版**的openjdk，在线上服务场景这样存在风险和隐患所以希望能够指定版本安装

所以想要使用的指定版本的方法安装，命令
>  yum install java-1.8.0-openjdk-devel-1.8.0.312.b07-1.el7_9

结果报了错

```
Loaded plugins: fastestmirror, ovl, priorities
Determining fastest mirrors
Percona                                                                             | 2.9 kB  00:00:00     
base                                                                                | 3.6 kB  00:00:00     
centos-sclo-rh                                                                      | 3.0 kB  00:00:00     
epel                                                                                | 4.7 kB  00:00:00     
extras                                                                              | 2.9 kB  00:00:00     
remi-mirror                                                                         | 2.9 kB  00:00:00     
                                                                              | 2.9 kB  00:00:00     
update                                                                              | 2.9 kB  00:00:00     
(1/11): Percona/primary_db                                                          |  90 kB  00:00:00     
(2/11): base/7/x86_64/group_gz                                                      | 153 kB  00:00:00     
(3/11): epel/7/group_gz                                                             |  96 kB  00:00:00     
(4/11): extras/7/x86_64/primary_db                                                  | 246 kB  00:00:00     
(5/11): epel/7/updateinfo                                                           | 1.0 MB  00:00:01     
(6/11): remi-mirror/primary_db                                                      | 1.5 MB  00:00:00     
(7/11):  /7/primary_db                                                        | 1.5 MB  00:00:00     
(8/11): centos-sclo-rh/7/x86_64/primary_db                                          | 3.8 MB  00:00:06     
(9/11): base/7/x86_64/primary_db                                                    | 6.1 MB  00:00:08     
(10/11): epel/7/primary_db                                                          | 7.0 MB  00:00:07     
(11/11): update/7/x86_64/primary_db                                                 |  14 MB  00:00:07     
1007 packages excluded due to repository priority protections
Resolving Dependencies
--> Running transaction check
---> Package java-1.8.0-openjdk-devel.x86_64 1:1.8.0.312.b07-1.el7_9 will be installed
--> Processing Dependency: java-1.8.0-openjdk(x86-64) = 1:1.8.0.312.b07-1.el7_9 for package: 1:java-1.8.0-openjdk-devel-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libjvm.so()(64bit) for package: 1:java-1.8.0-openjdk-devel-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libjava.so()(64bit) for package: 1:java-1.8.0-openjdk-devel-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libX11.so.6()(64bit) for package: 1:java-1.8.0-openjdk-devel-1.8.0.312.b07-1.el7_9.x86_64
--> Running transaction check
---> Package java-1.8.0-openjdk.x86_64 1:1.8.0.312.b07-1.el7_9 will be installed
--> Processing Dependency: java-1.8.0-openjdk-headless(x86-64) = 1:1.8.0.312.b07-1.el7_9 for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: xorg-x11-fonts-Type1 for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libpng15.so.15(PNG15_0)(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libjpeg.so.62(LIBJPEG_6.2)(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libasound.so.2(ALSA_0.9.0rc4)(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libasound.so.2(ALSA_0.9)(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libXcomposite(x86-64) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: gtk2(x86-64) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: fontconfig(x86-64) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libpng15.so.15()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libjpeg.so.62()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libgif.so.4()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libasound.so.2()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libXtst.so.6()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libXrender.so.1()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libXi.so.6()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
--> Processing Dependency: libXext.so.6()(64bit) for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
---> Package java-1.8.0-openjdk-headless.x86_64 1:1.8.0.322.b06-1.el7_9 will be installed
--> Processing Dependency: tzdata-java >= 2021e for package: 1:java-1.8.0-openjdk-headless-1.8.0.322.b06-1.el7_9.x86_64
--> Processing Dependency: copy-jdk-configs >= 3.3 for package: 1:java-1.8.0-openjdk-headless-1.8.0.322.b06-1.el7_9.x86_64
--> Processing Dependency: pcsc-lite-libs(x86-64) for package: 1:java-1.8.0-openjdk-headless-1.8.0.322.b06-1.el7_9.x86_64
--> Processing Dependency: lksctp-tools(x86-64) for package: 1:java-1.8.0-openjdk-headless-1.8.0.322.b06-1.el7_9.x86_64
--> Processing Dependency: jpackage-utils for package: 1:java-1.8.0-openjdk-headless-1.8.0.322.b06-1.el7_9.x86_64
--> Processing Dependency: libfreetype.so.6()(64bit) for package: 1:java-1.8.0-openjdk-headless-1.8.0.322.b06-1.el7_9.x86_64
---> Package libX11.x86_64 0:1.6.7-4.el7_9 will be installed
--> Processing Dependency: libX11-common >= 1.6.7-4.el7_9 for package: libX11-1.6.7-4.el7_9.x86_64
--> Processing Dependency: libxcb.so.1()(64bit) for package: libX11-1.6.7-4.el7_9.x86_64
--> Running transaction check
---> Package alsa-lib.x86_64 0:1.1.8-1.el7 will be installed
---> Package copy-jdk-configs.noarch 0:3.3-10.el7_5 will be installed
---> Package fontconfig.x86_64 0:2.13.0-4.3.el7 will be installed
--> Processing Dependency: fontpackages-filesystem for package: fontconfig-2.13.0-4.3.el7.x86_64
--> Processing Dependency: dejavu-sans-fonts for package: fontconfig-2.13.0-4.3.el7.x86_64
---> Package freetype.x86_64 0:2.8-14.el7_9.1 will be installed
---> Package giflib.x86_64 0:4.1.6-9.el7 will be installed
--> Processing Dependency: libSM.so.6()(64bit) for package: giflib-4.1.6-9.el7.x86_64
--> Processing Dependency: libICE.so.6()(64bit) for package: giflib-4.1.6-9.el7.x86_64
---> Package gtk2.x86_64 0:2.24.31-1.el7 will be installed
--> Processing Dependency: pango >= 1.20.0-1 for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libtiff >= 3.6.1 for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXrandr >= 1.2.99.4-2 for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: atk >= 1.29.4-2 for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: hicolor-icon-theme for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: gtk-update-icon-cache for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libpangoft2-1.0.so.0()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libpangocairo-1.0.so.0()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libpango-1.0.so.0()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libgdk_pixbuf-2.0.so.0()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libcairo.so.2()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libatk-1.0.so.0()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXrandr.so.2()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXinerama.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXfixes.so.3()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXdamage.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
--> Processing Dependency: libXcursor.so.1()(64bit) for package: gtk2-2.24.31-1.el7.x86_64
---> Package java-1.8.0-openjdk.x86_64 1:1.8.0.312.b07-1.el7_9 will be installed
--> Processing Dependency: java-1.8.0-openjdk-headless(x86-64) = 1:1.8.0.312.b07-1.el7_9 for package: 1:java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9.x86_64
---> Package javapackages-tools.noarch 0:3.4.1-11.el7 will be installed
--> Processing Dependency: python-javapackages = 3.4.1-11.el7 for package: javapackages-tools-3.4.1-11.el7.noarch
--> Processing Dependency: libxslt for package: javapackages-tools-3.4.1-11.el7.noarch
---> Package libX11-common.noarch 0:1.6.7-4.el7_9 will be installed
---> Package libXcomposite.x86_64 0:0.4.4-4.1.el7 will be installed
---> Package libXext.x86_64 0:1.3.3-3.el7 will be installed
---> Package libXi.x86_64 0:1.7.9-1.el7 will be installed
---> Package libXrender.x86_64 0:0.9.10-1.el7 will be installed
---> Package libXtst.x86_64 0:1.2.3-1.el7 will be installed
---> Package libjpeg-turbo.x86_64 0:2.0.2-1 will be installed
---> Package libpng.x86_64 2:1.5.13-8.el7 will be installed
---> Package libxcb.x86_64 0:1.13-1.el7 will be installed
--> Processing Dependency: libXau.so.6()(64bit) for package: libxcb-1.13-1.el7.x86_64
---> Package lksctp-tools.x86_64 0:1.0.17-2.el7 will be installed
---> Package pcsc-lite-libs.x86_64 0:1.8.8-8.el7 will be installed
---> Package tzdata-java.noarch 0:2021e-1.el7 will be installed
---> Package xorg-x11-fonts-Type1.noarch 0:7.5-9.el7 will be installed
--> Processing Dependency: ttmkfdir for package: xorg-x11-fonts-Type1-7.5-9.el7.noarch
--> Processing Dependency: ttmkfdir for package: xorg-x11-fonts-Type1-7.5-9.el7.noarch
--> Processing Dependency: mkfontdir for package: xorg-x11-fonts-Type1-7.5-9.el7.noarch
--> Processing Dependency: mkfontdir for package: xorg-x11-fonts-Type1-7.5-9.el7.noarch
--> Running transaction check
---> Package atk.x86_64 0:2.28.1-2.el7 will be installed
---> Package cairo.x86_64 0:1.15.12-4.el7 will be installed
--> Processing Dependency: libpixman-1.so.
```

这时候发现了安装java-1.8.0-openjdk的指定版本不会报错

>  yum install java-1.8.0-openjdk-1.8.0.312.b07-1.el7_9


接着执行就能正常安装了...

> yum install java-1.8.0-openjdk-devel-1.8.0.312.b07-1.el7_9


## 还没有解决的问题

* 为什么直接安装会报错呢？
* 为什么先安装不带devel再安装devel的就能够安装成功呢？


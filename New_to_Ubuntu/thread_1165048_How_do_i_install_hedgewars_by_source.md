---
title: "How do i install hedgewars by source?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-05-20
Hedgewars is a game like worms. the way i installed it is by using the terminal:
```
sudo apt-get install hedgewars
```

However, it only gave me version 0.9.7!

I want the version 0.9.10 

here is the link for the tar file:

[http://hedgewars.org/download.html]("http://hedgewars.org/download.html")

the getdeb.net file doesn't have the latest package for Jaunty Jacklope.

The only other way is to install it by source. How do I do that?

---

### Post by halitech on 2009-05-20
from the install file after extracting the files

```
To compile and install you need:
 - Qt >= 4.4
 - FreePascal >= 2.2.0
 - SDL >= 1.2.5
 - SDL_net >= 1.2.5
 - SDL_mixer >= 1.2
 - SDL_image >= 1.2
 - SDL_ttf >= 2.0
 - CMake >= 2.4.4
 - QCA2 library

1. Configure:
$ cmake .
or
$ cmake -DCMAKE_CXX_FLAGS="flags" -DCMAKE_INSTALL_PREFIX="install prefix" -DDATA_INSTALL_DIR="data dir" .

add -DWITH_SERVER=1 to compile net server (requires Glasgow Haskell Compiler)

2. Compile:
$ make

3. Install:
# make install

That's all! Enjoy!
```

---

### Post by s.fox on 2009-05-20
Hi,

If you like worms,  have you tried Wormux?   It should be listed in synaptic package manager.  

I just thought you might want to give that a go as well.

-Ash R

---

### Post by Jazzy_Jeff on 2009-05-20
There is an Ubuntu package. It is for intrepid but it should work fine for Jaunty.

---

### Post by CLomax on 2009-05-20
[http://www.getdeb.net/app/Hedgewars](http://www.getdeb.net/app/Hedgewars)

.deb packages run just like .exe files in Windows. Enjoy.

:KS

---

### Post by shiningkenmonster on 2009-05-20
> **Ash R said:**
> Hi,

If you like worms,  have you tried Wormux?   It should be listed in synaptic package manager.  

I just thought you might want to give that a go as well.

-Ash R

yes, i have tried it. The only problem is the AI is really stupid. I gave up on it. On the internet rants, it seems like a lot of people ditched Wormux and went to hedgewars

---

### Post by shiningkenmonster on 2009-05-20
> **Jazzy_Jeff said:**
> There is an Ubuntu package. It is for intrepid but it should work fine for Jaunty.

yes, i have tried that before. It is not compatible with it. It gave me an Error to install it.

---

### Post by shiningkenmonster on 2009-05-20
> **CLomax said:**
> [http://www.getdeb.net/app/Hedgewars](http://www.getdeb.net/app/Hedgewars)

.deb packages run just like .exe files in Windows. Enjoy.

:KS

That was the link I was talking about. It only supports Intrepid, not Jaunty. It gave me an error. I couldn't install it. The only way is to find it somewhere else or install it by Source.

---

### Post by Mornedhel on 2009-05-20
Remember to uninstall the Jaunty package for hedgewars first.

You might find it easier to download the dependencies for Hedgewars with a sudo apt-get build-dep hedgewars (you will need to have some deb-src repositories enabled in your sources.list). It should download and install every library and header file you need to compile the Jaunty version of hedgewars ; with a little luck, those won't have changed between the Jaunty version and the latest source.

---

### Post by shiningkenmonster on 2009-05-20
thanks, is there a way someone can give me concrete step by step instructions?

---

### Post by Mornedhel on 2009-05-20
halitech has pointed out earlier in this thread that there are instructions on how to compile hedgewars in the tarball, as well as a list of dependencies. It seems to be cmake-driven, so you'll have to install cmake from the repositories.

The online FAQ also helps : [http://www.hedgewars.org/faq.html#n1298](http://www.hedgewars.org/faq.html#n1298)

It's meant for Debian, but it's close enough.

---

### Post by bacardiandwatermelon on 2009-05-20
I think this should work.. 

```
sudo apt-get install cmake qt4-qmake libqt4-dev libsdl1.2-dev libsdl-net1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev fpc subversion
mkdir hedgewars
cd hedgewars
svn checkout svn://svn.fireforge.net/svnroot/hedgewars/trunk/
cd trunk
cmake .
make
sudo make install
```I better add that this installs the latest trunk build..

---

### Post by shiningkenmonster on 2009-05-21
bacardiandwatermelon, oh nice. I ve just installed it. I didn't know i was installing hedgewars 0.9.11-dev

I did notice the fps were going 74-101 fps thou. which i believe it was going more higher than usual.

---

### Post by shiningkenmonster on 2009-05-21
So i decided to do:
```
sudo apt-get remove libsdl1.2debian-alsa

```

I was not aware that it was going to remove some of the programs. I just enter "Y" without loooking. It was too late, the programs were already removed.
```
kenny@kenny-netbook:~$ sudo apt-get remove libsdl1.2debian-alsa
[sudo] password for kenny: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libcaca-dev libqca2 libqt4-opengl libsbigudrv0 libqt4-assistant libaudiofile-dev libaudio-dev
  ttf-sil-andika libxerces-c2-dev librdf0 kdebase-runtime-data-common libcfitsio3 comerr-dev libqt4-test ttf-dustin
  libxine1-misc-plugins kdelibs5 libxcb-xv0 libmikmod2-dev liblualib50-dev libxerces-c28 libxmu-headers mesa-common-dev
  kde-icons-oxygen libxine1-bin libexiv2-5 libkrb5-dev librasqal1 libglu1-xorg-dev libdvbpsi4 planetpenguin-racer-extras
  kalzium-data libsqlite0-dev kdeedu-kvtml-data libqt4-xmlpatterns libsoprano4 redland-utils libvlc2 smc-data liblua50-dev
  libqt4-help lua50 ttf-sjfonts epiphany-data kdelibs5-data vlc-nox libglu1-mesa-dev tuxpaint-data libssl-dev libxcb-shape0
  libxt-dev libxmu-dev kstars-data libtiff4-dev libesd0-dev libqt4-svg netpbm xlibmesa-gl-dev frozen-bubble-data
  libstreamanalyzer0 libphonon4 libiso9660-5 libopenbabel3 libasound2-dev planetpenguin-racer-data libtiffxx0c2
  libgl1-mesa-dev liblcms1-dev libpq-dev kdelibs-bin libkadm55 libslang2-dev liblua5.1-0 tuxpaint-plugins-default
  libncurses5-dev libnetpbm10 libfreeimage3 libstreams0 vlc-data exiv2 fb-music-high libtar libboost-filesystem1.37.0 indi
  libmng-dev libqt4-scripttools libvlccore0 libxcb-shm0 soprano-daemon libvcdinfo0 kdebase-runtime-data libebml0
  tuxpaint-stamps-default holotz-castle-data libaa1-dev libboost-system1.37.0 libmatroska0 libxine1-console
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  blinken epiphany frozen-bubble gimp gstreamer0.10-plugins-bad-multiverse holotz-castle kalgebra kalzium kanagram
  kbattleship kbounce kbruch kdebase-runtime kdebase-runtime-bin-kde4 kgoldrunner khangman khelpcenter4 kmplot kstars
  ktouch ktuberling kwordquiz libcegui-mk2-1 libcegui-mk2-dev libdevil-dev libdevil1c2 libgegl-0.0-0 libkdeedu4
  libkdegames5 libmjpegtools-1.9 libplasma3 libqt4-dev libqt4-opengl-dev libqt4-webkit libsdl-console libsdl-gfx1.2-4
  libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-pango1
  libsdl-perl libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa libsmpeg-dev libsmpeg0
  libxine1 libxine1-x phonon phonon-backend-xine planetpenguin-racer smc tuxmath tuxpaint vlc
0 upgraded, 0 newly installed, 60 to remove and 0 not upgraded.
After this operation, 143MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 152528 files and directories currently installed.)
Removing blinken ...
Removing epiphany ...
Removing frozen-bubble ...
Removing gimp ...
Removing gstreamer0.10-plugins-bad-multiverse ...
Removing holotz-castle ...
Removing kalgebra ...
Removing kalzium ...
Removing kanagram ...
Removing kbattleship ...
Removing kbounce ...
Removing kbruch ...
Removing ktuberling ...
Removing kgoldrunner ...
Removing libkdegames5 ...
Removing kwordquiz ...
Removing kstars ...
Removing khangman ...
Removing libkdeedu4 ...
Removing ktouch ...
Removing kmplot ...
Removing khelpcenter4 ...
Removing smc ...
Removing libcegui-mk2-dev ...
Removing libcegui-mk2-1 ...
Removing libdevil-dev ...
Removing libdevil1c2 ...
Removing libgegl-0.0-0 ...
Removing libmjpegtools-1.9 ...
Removing libplasma3 ...
Removing libqt4-opengl-dev ...
Removing libqt4-dev ...
Removing libqt4-webkit ...
Removing libsdl-perl ...
Removing libsdl-console ...
Removing libsdl-gfx1.2-4 ...
Removing vlc ...
Removing tuxpaint ...
Removing tuxmath ...
Removing libsdl-image1.2-dev ...
Removing libsdl-image1.2 ...
Removing planetpenguin-racer ...
Removing libsdl-mixer1.2-dev ...
Removing libsdl-mixer1.2 ...
Removing libsdl-net1.2-dev ...
Removing libsdl-net1.2 ...
Removing libsdl-pango1 ...
Removing libsdl-ttf2.0-dev ...
Removing libsdl-ttf2.0-0 ...
Removing libsmpeg-dev ...
Removing libsdl1.2-dev ...
Removing phonon ...
Removing libsmpeg0 ...
Removing kdebase-runtime ...
Removing kdebase-runtime-bin-kde4 ...
Removing phonon-backend-xine ...
Removing libxine1 ...
Removing libxine1-x ...
Removing libsdl1.2debian ...
Removing libsdl1.2debian-alsa ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...

```

```
kenny@kenny-netbook:~$ sudo apt-get install libsdl1.2debian-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libcaca-dev libqca2 libqt4-opengl libsbigudrv0 libqt4-assistant libaudiofile-dev libaudio-dev
  libbabl-0.0-0 ttf-sil-andika libxerces-c2-dev librdf0 kdebase-runtime-data-common libcfitsio3 comerr-dev libqt4-test
  ttf-dustin libxine1-misc-plugins kdelibs5 libxcb-xv0 libmikmod2-dev liblualib50-dev libxerces-c28 libxmu-headers
  mesa-common-dev kde-icons-oxygen libxine1-bin libexiv2-5 libkrb5-dev librasqal1 libglu1-xorg-dev libdvbpsi4
  planetpenguin-racer-extras kalzium-data libsqlite0-dev kdeedu-kvtml-data libqt4-xmlpatterns libsoprano4 redland-utils
  libvlc2 smc-data liblua50-dev libqt4-help lua50 ttf-sjfonts epiphany-data kdelibs5-data vlc-nox libglu1-mesa-dev
  tuxpaint-data libssl-dev libxcb-shape0 libxt-dev libxmu-dev kstars-data libtiff4-dev libesd0-dev libqt4-svg netpbm
  xlibmesa-gl-dev frozen-bubble-data libstreamanalyzer0 libphonon4 libiso9660-5 libopenbabel3 libasound2-dev libgimp2.0
  planetpenguin-racer-data libtiffxx0c2 libgl1-mesa-dev liblcms1-dev libpq-dev kdelibs-bin libkadm55 libslang2-dev
  liblua5.1-0 tuxpaint-plugins-default libncurses5-dev libnetpbm10 libfreeimage3 libstreams0 vlc-data exiv2 fb-music-high
  libtar libboost-filesystem1.37.0 indi libquicktime1 libmng-dev libqt4-scripttools gimp-data libvlccore0 libxcb-shm0
  soprano-daemon libvcdinfo0 kdebase-runtime-data libebml0 tuxpaint-stamps-default holotz-castle-data libaa1-dev
  libboost-system1.37.0 libmatroska0 libxine1-console
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libsdl1.2debian-oss
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 212kB of archives.
After this operation, 516kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty/main libsdl1.2debian-oss 1.2.13-4ubuntu3 [212kB]
Fetched 212kB in 1s (117kB/s)               
Selecting previously deselected package libsdl1.2debian-oss.
(Reading database ... 146850 files and directories currently installed.)
Unpacking libsdl1.2debian-oss (from .../libsdl1.2debian-oss_1.2.13-4ubuntu3_i386.deb) ...
Setting up libsdl1.2debian-oss (1.2.13-4ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

It was okay with me. I just wanted to get hedgewars to start playing.... it didn't happen...
```
kenny@kenny-netbook:~$ hedgewars
hedgewars: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
kenny@kenny-netbook:~$ 


```

```
kenny@kenny-netbook:~$ sudo apt-get autoremove libsdl1.2debian-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libcaca-dev libqca2 libqt4-opengl libsbigudrv0 libqt4-assistant libaudiofile-dev libaudio-dev
  libbabl-0.0-0 ttf-sil-andika libxerces-c2-dev librdf0 kdebase-runtime-data-common libcfitsio3 comerr-dev libqt4-test
  ttf-dustin libxine1-misc-plugins kdelibs5 libxcb-xv0 libmikmod2-dev liblualib50-dev libxerces-c28 libxmu-headers
  mesa-common-dev kde-icons-oxygen libxine1-bin libexiv2-5 libkrb5-dev librasqal1 libglu1-xorg-dev libdvbpsi4
  planetpenguin-racer-extras kalzium-data libsqlite0-dev kdeedu-kvtml-data libqt4-xmlpatterns libsoprano4 redland-utils
  libvlc2 smc-data liblua50-dev libqt4-help lua50 ttf-sjfonts epiphany-data kdelibs5-data vlc-nox libglu1-mesa-dev
  tuxpaint-data libssl-dev libxcb-shape0 libxt-dev libxmu-dev kstars-data libtiff4-dev libesd0-dev libqt4-svg netpbm
  xlibmesa-gl-dev frozen-bubble-data libstreamanalyzer0 libphonon4 libiso9660-5 libopenbabel3 libasound2-dev libgimp2.0
  planetpenguin-racer-data libtiffxx0c2 libgl1-mesa-dev liblcms1-dev libpq-dev kdelibs-bin libkadm55 libslang2-dev
  liblua5.1-0 tuxpaint-plugins-default libncurses5-dev libnetpbm10 libfreeimage3 libstreams0 vlc-data exiv2 fb-music-high
  libtar libboost-filesystem1.37.0 indi libquicktime1 libmng-dev libqt4-scripttools gimp-data libvlccore0 libxcb-shm0
  soprano-daemon libvcdinfo0 kdebase-runtime-data libebml0 tuxpaint-stamps-default holotz-castle-data libaa1-dev
  libboost-system1.37.0 libmatroska0 libxine1-console
The following packages will be REMOVED:
  comerr-dev epiphany-data exiv2 fb-music-high frozen-bubble-data gimp-data holotz-castle-data indi kalzium-data
  kde-icons-oxygen kdebase-runtime-data kdebase-runtime-data-common kdeedu-kvtml-data kdelibs-bin kdelibs5 kdelibs5-data
  kstars-data libaa1-dev libasound2-dev libaudio-dev libaudiofile-dev libbabl-0.0-0 libboost-filesystem1.37.0
  libboost-system1.37.0 libcaca-dev libcfitsio3 libclucene0ldbl libdvbpsi4 libebml0 libesd0-dev libexiv2-5 libfreeimage3
  libgimp2.0 libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libiso9660-5 libkadm55 libkrb5-dev liblcms1-dev liblua5.1-0
  liblua50-dev liblualib50-dev libmatroska0 libmikmod2-dev libmng-dev libncurses5-dev libnetpbm10 libopenbabel3 libphonon4
  libpq-dev libqca2 libqt4-assistant libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test libqt4-xmlpatterns
  libquicktime1 librasqal1 librdf0 libsbigudrv0 libsdl1.2debian-oss libslang2-dev libsoprano4 libsqlite0-dev libssl-dev
  libstreamanalyzer0 libstreams0 libtar libtiff4-dev libtiffxx0c2 libvcdinfo0 libvlc2 libvlccore0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxerces-c2-dev libxerces-c28 libxine1-bin libxine1-console libxine1-misc-plugins libxmu-dev libxmu-headers
  libxt-dev lua50 mesa-common-dev netpbm planetpenguin-racer-data planetpenguin-racer-extras redland-utils smc-data
  soprano-daemon ttf-dustin ttf-sil-andika ttf-sjfonts tuxpaint-data tuxpaint-plugins-default tuxpaint-stamps-default
  vlc-data vlc-nox xlibmesa-gl-dev
0 upgraded, 0 newly installed, 104 to remove and 0 not upgraded.
After this operation, 501MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
kenny@kenny-netbook:~$ sudo apt-get install libsdl1.2debian-alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libcaca-dev libqca2 libqt4-opengl libsbigudrv0 libqt4-assistant libaudiofile-dev libaudio-dev
  libbabl-0.0-0 ttf-sil-andika libxerces-c2-dev librdf0 kdebase-runtime-data-common libcfitsio3 comerr-dev libqt4-test
  ttf-dustin libxine1-misc-plugins kdelibs5 libxcb-xv0 libmikmod2-dev liblualib50-dev libxerces-c28 libxmu-headers
  mesa-common-dev kde-icons-oxygen libxine1-bin libexiv2-5 libkrb5-dev librasqal1 libglu1-xorg-dev libdvbpsi4
  planetpenguin-racer-extras kalzium-data libsqlite0-dev kdeedu-kvtml-data libqt4-xmlpatterns libsoprano4 redland-utils
  libvlc2 smc-data liblua50-dev libqt4-help lua50 ttf-sjfonts epiphany-data kdelibs5-data vlc-nox libglu1-mesa-dev
  tuxpaint-data libssl-dev libxcb-shape0 libxt-dev libxmu-dev kstars-data libtiff4-dev libesd0-dev libqt4-svg netpbm
  xlibmesa-gl-dev frozen-bubble-data libstreamanalyzer0 libphonon4 libiso9660-5 libopenbabel3 libasound2-dev libgimp2.0
  planetpenguin-racer-data libtiffxx0c2 libgl1-mesa-dev liblcms1-dev libpq-dev kdelibs-bin libkadm55 libslang2-dev
  liblua5.1-0 tuxpaint-plugins-default libncurses5-dev libnetpbm10 libfreeimage3 libstreams0 vlc-data exiv2 fb-music-high
  libtar libboost-filesystem1.37.0 indi libquicktime1 libmng-dev libqt4-scripttools gimp-data libvlccore0 libxcb-shm0
  soprano-daemon libvcdinfo0 kdebase-runtime-data libebml0 tuxpaint-stamps-default holotz-castle-data libaa1-dev
  libboost-system1.37.0 libmatroska0 libxine1-console
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libsdl1.2debian-oss
The following NEW packages will be installed:
  libsdl1.2debian-alsa
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 211kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com jaunty/main libsdl1.2debian-alsa 1.2.13-4ubuntu3 [211kB]
Fetched 211kB in 1s (111kB/s)                
(Reading database ... 146858 files and directories currently installed.)
Removing libsdl1.2debian-oss ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libsdl1.2debian-alsa.
(Reading database ... 146850 files and directories currently installed.)
Unpacking libsdl1.2debian-alsa (from .../libsdl1.2debian-alsa_1.2.13-4ubuntu3_i386.deb) ...
Setting up libsdl1.2debian-alsa (1.2.13-4ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

now hedgewars still doesn't work anymore. some of my programs are deleted.
I remove the packages:
```
kenny@kenny-netbook:~$ sudo apt-get autoremove
[sudo] password for kenny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libcaca-dev libqca2 libqt4-opengl libsbigudrv0 libqt4-assistant libaudiofile-dev libaudio-dev
  libbabl-0.0-0 ttf-sil-andika libxerces-c2-dev librdf0 kdebase-runtime-data-common libcfitsio3 comerr-dev libqt4-test
  ttf-dustin libxine1-misc-plugins kdelibs5 libxcb-xv0 libmikmod2-dev liblualib50-dev libxerces-c28 libxmu-headers
  mesa-common-dev kde-icons-oxygen libxine1-bin libexiv2-5 libkrb5-dev librasqal1 libglu1-xorg-dev libdvbpsi4
  planetpenguin-racer-extras kalzium-data libsqlite0-dev kdeedu-kvtml-data libqt4-xmlpatterns libsoprano4 redland-utils
  libvlc2 smc-data liblua50-dev libqt4-help lua50 ttf-sjfonts epiphany-data kdelibs5-data vlc-nox libglu1-mesa-dev
  tuxpaint-data libssl-dev libxcb-shape0 libxt-dev libxmu-dev kstars-data libtiff4-dev libesd0-dev libqt4-svg netpbm
  xlibmesa-gl-dev frozen-bubble-data libstreamanalyzer0 libphonon4 libiso9660-5 libopenbabel3 libasound2-dev libgimp2.0
  planetpenguin-racer-data libtiffxx0c2 libgl1-mesa-dev liblcms1-dev libpq-dev kdelibs-bin libkadm55 libslang2-dev
  liblua5.1-0 tuxpaint-plugins-default libncurses5-dev libnetpbm10 libfreeimage3 libstreams0 vlc-data exiv2 fb-music-high
  libtar libboost-filesystem1.37.0 indi libquicktime1 libmng-dev libqt4-scripttools gimp-data libvlccore0 libxcb-shm0
  soprano-daemon libvcdinfo0 kdebase-runtime-data libebml0 tuxpaint-stamps-default holotz-castle-data libaa1-dev
  libboost-system1.37.0 libmatroska0 libxine1-console
The following packages will be REMOVED:
  comerr-dev epiphany-data exiv2 fb-music-high frozen-bubble-data gimp-data holotz-castle-data indi kalzium-data
  kde-icons-oxygen kdebase-runtime-data kdebase-runtime-data-common kdeedu-kvtml-data kdelibs-bin kdelibs5 kdelibs5-data
  kstars-data libaa1-dev libasound2-dev libaudio-dev libaudiofile-dev libbabl-0.0-0 libboost-filesystem1.37.0
  libboost-system1.37.0 libcaca-dev libcfitsio3 libclucene0ldbl libdvbpsi4 libebml0 libesd0-dev libexiv2-5 libfreeimage3
  libgimp2.0 libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libiso9660-5 libkadm55 libkrb5-dev liblcms1-dev liblua5.1-0
  liblua50-dev liblualib50-dev libmatroska0 libmikmod2-dev libmng-dev libncurses5-dev libnetpbm10 libopenbabel3 libphonon4
  libpq-dev libqca2 libqt4-assistant libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test libqt4-xmlpatterns
  libquicktime1 librasqal1 librdf0 libsbigudrv0 libslang2-dev libsoprano4 libsqlite0-dev libssl-dev libstreamanalyzer0
  libstreams0 libtar libtiff4-dev libtiffxx0c2 libvcdinfo0 libvlc2 libvlccore0 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxerces-c2-dev libxerces-c28 libxine1-bin libxine1-console libxine1-misc-plugins libxmu-dev libxmu-headers libxt-dev
  lua50 mesa-common-dev netpbm planetpenguin-racer-data planetpenguin-racer-extras redland-utils smc-data soprano-daemon
  ttf-dustin ttf-sil-andika ttf-sjfonts tuxpaint-data tuxpaint-plugins-default tuxpaint-stamps-default vlc-data vlc-nox
  xlibmesa-gl-dev
0 upgraded, 0 newly installed, 103 to remove and 0 not upgraded.
After this operation, 501MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 146858 files and directories currently installed.)
Removing libpq-dev ...
Removing libkrb5-dev ...
Removing comerr-dev ...
Removing epiphany-data ...
Removing exiv2 ...
Removing fb-music-high ...
Removing frozen-bubble-data ...
Removing gimp-data ...
Removing holotz-castle-data ...
Removing indi ...
Removing kalzium-data ...
Removing kde-icons-oxygen ...
Removing kdebase-runtime-data ...
Removing kdebase-runtime-data-common ...
Removing kdeedu-kvtml-data ...
Removing kstars-data ...
Removing libaa1-dev ...
Removing libasound2-dev ...
Removing libaudio-dev ...
Removing libesd0-dev ...
Removing libaudiofile-dev ...
Removing libbabl-0.0-0 ...
Removing libboost-filesystem1.37.0 ...
Removing libboost-system1.37.0 ...
Removing libcaca-dev ...
Removing libsbigudrv0 ...
Removing libcfitsio3 ...
Removing vlc-nox ...
Removing libdvbpsi4 ...
Removing libmatroska0 ...
Removing libebml0 ...
Removing libfreeimage3 ...
Removing libgimp2.0 ...
Removing libglu1-xorg-dev ...
Removing libglu1-mesa-dev ...
Removing xlibmesa-gl-dev ...
Removing libgl1-mesa-dev ...
Removing libvcdinfo0 ...
Removing libiso9660-5 ...
Removing libkadm55 ...
Removing libmng-dev ...
Removing liblcms1-dev ...
Removing liblua5.1-0 ...
Removing liblualib50-dev ...
Removing liblua50-dev ...
Removing libmikmod2-dev ...
Removing libncurses5-dev ...
Removing netpbm ...
Removing libnetpbm10 ...
Removing libopenbabel3 ...
Removing libqca2 ...
Removing libqt4-assistant ...
Removing libqt4-help ...
Removing libqt4-opengl ...
Removing libqt4-scripttools ...
Removing libqt4-test ...
Removing libqt4-xmlpatterns ...
Removing libquicktime1 ...
Removing redland-utils ...
Removing libslang2-dev ...
Removing libsqlite0-dev ...
Removing libssl-dev ...
Removing libtar ...
Removing libtiff4-dev ...
Removing libtiffxx0c2 ...
Removing libvlc2 ...
Removing libvlccore0 ...
Removing libxcb-shape0 ...
Removing libxcb-shm0 ...
Removing libxcb-xv0 ...
Removing libxerces-c2-dev ...
Removing libxerces-c28 ...
Removing libxine1-misc-plugins ...
Removing libxine1-console ...
Removing libxine1-bin ...
Removing libxmu-dev ...
Removing libxmu-headers ...
Removing libxt-dev ...
Removing lua50 ...
Removing mesa-common-dev ...
Removing planetpenguin-racer-data ...
Removing planetpenguin-racer-extras ...
Removing smc-data ...
Removing ttf-dustin ...
Updating fontconfig cache for /usr/share/fonts/truetype/dustin
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing ttf-sil-andika ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-sil-andika
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing ttf-sjfonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/sjfonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing tuxpaint-data ...
Removing tuxpaint-plugins-default ...
Removing tuxpaint-stamps-default ...
Removing vlc-data ...
Removing kdelibs5 ...
Removing kdelibs5-data ...
Removing libstreamanalyzer0 ...
Removing libexiv2-5 ...
Removing libphonon4 ...
Removing libstreams0 ...
Removing kdelibs-bin ...
Removing libsoprano4 ...
Removing libqt4-svg ...
Removing soprano-daemon ...
Removing libclucene0ldbl ...
Removing librdf0 ...
Removing librasqal1 ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for shared-mime-info ...

```

still no go...

---

### Post by bacardiandwatermelon on 2009-05-21
Aww mate looks like I gave you some bad advice... When I was getting low FPS it was stuck under 10.. All I can suggest is re install all the apps that you uninstalled.. and cmake hedgewars again... Sorry dude.

```
sudo apt-get install blinken epiphany frozen-bubble gimp gstreamer0.10-plugins-bad-multiverse holotz-castle kalgebra kalzium kanagram kbattleship kbounce kbruch kdebase-runtime kdebase-runtime-bin-kde4 kgoldrunner khangman khelpcenter4 kmplot kstars  ktouch ktuberling kwordquiz libcegui-mk2-1 libcegui-mk2-dev libdevil-dev libdevil1c2 libgegl-0.0-0 libkdeedu4  libkdegames5 libmjpegtools-1.9 libplasma3 libqt4-dev libqt4-opengl-dev libqt4-webkit libsdl-console libsdl-gfx1.2-4  libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-pango1  libsdl-perl libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa libsmpeg-dev libsmpeg0  libxine1 libxine1-x phonon phonon-backend-xine planetpenguin-racer smc tuxmath tuxpaint vlc libsdl1.2debian-alsa

```

---

### Post by Mornedhel on 2009-05-21
libsdl1.2debian-alsa and libsdl1.2debian-oss conflict with each other, so installing either would automatically remove the other.

Also, several packages (the blinken, epiphany, etc. list) depended on libsdl1.2debian-alsa OR libsdl1.2debian-oss OR libsdl1.2debian-somethingelse. When you removed libsdl1.2debian-alsa, they could not function anymore and so they were removed as well. apt-get clearly stated this when you removed libsdl1.2debian-alsa.

Had you tried apt-get install libsdl1.2debian-oss first, the dependencies would still have been satisfied and nothing would have been broken. The libsdl-mixer1.2-dev package, that provided the library hedgewars is asking for, was also removed at that time. If you want to get hedgewars to run, you will have to reinstall this package, among others.

Please check for conflicts and dependencies next time and PLEASE, PLEASE, READ ERROR MESSAGES WHEN THEY APPEAR.

---

### Post by shiningkenmonster on 2009-05-21
looks like there are too many broken packages. I was thinking of formatting and starting over.

____________________________________________

I am still confuse oh how to install a hedgewars tar.br2 file.

---

### Post by durand on 2009-05-21
Reinstalling would be the easiest thing to do here. **[COLOR="Red"]NEXT TIME, READ WHAT YOU'RE ACCEPTING INSTEAD OF BLINDLY SAYING YES![/COLOR]**

---

### Post by shiningkenmonster on 2009-05-24
This is the semi-slim down version. Its suppose to take up less memory. this is the complete newbie guide :P

```
sudo apt-get install cmake qt4-qmake libqt4-dev libsdl1.2-dev libsdl-net1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev fpc subversion
```

```
sudo apt-get clean
```

```
cd;mkdir -p svn/hedgewars;cd svn/hedgewars;svn co   svn://svn.fireforge.net/svnroot/hedgewars/trunk
```

```
cd trunk;cmake -DCMAKE_INSTALL_PREFIX="$HOME/games" -DDATA_INSTALL_DIR="$HOME/games"
```

```
cd ~/games;mkdir hedgewars;cd hedgewars;ln -s ~/svn/hedgewars/trunk/share/hedgewars/Data .;cd ~/svn/hedgewars/trunk;make install
```

```
cd ~/games/bin
```

```
./hedgewars
```

live update it. to fix all the bugs and download all the cool lastest stuff. type this in the terminal:
```
cd ~/svn/hedgewars/trunk;svn up
make install
```

to make an icon of it from the menu bar.
```
$HOME/games/bin/hedgewars
```

---

### Post by burvowski on 2009-05-25
^That worked flawlessly, thanks! Do I have to repeat every one of those everytime a new version is out, btw? Or can I start the compiling at a certain step? Thanks!

---

### Post by shiningkenmonster on 2009-05-26
when there is a new version. or you want to get the development beta kit.

```
cd ~/svn/hedgewars/trunk;svn up
make install
```

---


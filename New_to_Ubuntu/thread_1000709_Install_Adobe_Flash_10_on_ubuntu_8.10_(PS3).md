---
title: "Install Adobe Flash 10 on ubuntu 8.10 (PS3)"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by lunar on 2008-12-03
I have installed ubuntu 8.10 couple days ago on my PS3. Now I am having hard time installing adobe flash 10 plugin for firefox.
Any help? I went through lot of forums. I didnt want gnash. I think I removed it. Still Adobe flash doesnt work.

I tried installing .deb. didnt work. tried .tar.gz, copied the .so to /usr/lib/firefox-addons/ and /usr/lib/mozilla/plugins.
didnt work.
I will really appreciate your help.

---

### Post by lunar on 2008-12-03
I have installed ubuntu 8.10 couple days ago on my PS3. Now I am having hard time installing adobe flash 10 plugin for firefox.
Any help? I went through lot of forums. I didnt want gnash. I think I removed it. Still Adobe flash doesnt work.

I tried installing .deb. didnt work. tried .tar.gz, copied the .so to /usr/lib/firefox-addons/ and /usr/lib/mozilla/plugins.
didnt work.
I will really appreciate your help.

---

### Post by overdrank on 2008-12-03
Hi and please do not make multiple threads on the same issue.
Threads merged.
This topic was discussed earlier
[http://ubuntuforums.org/showthread.php?t=1000709](http://ubuntuforums.org/showthread.php?t=1000709)
It may be of some help.

---

### Post by gandaran on 2008-12-03
you have been installing a lot of flash packages! this will just mess up the system, remove all and just install (one flash package) the flashplugin-nonfree in synaptic 
if you don't know what exactly you have installed, post the output of **locate libflash** (type in terminal/console)
and also the output of 
```
about:plugins
```
this code you type in firefox url bar

---

### Post by lunar on 2008-12-03
First applogize for posting it in 2 places. Didnt know if this would fall under beginner talk or installation.

```
swati@psubuntu:~$ locate flash
/home/swati/install_flash_player_10_linux.tar.gz
/lib/modules/2.6.25-2-powerpc64-smp/kernel/arch/powerpc/kernel/rtas_flash.ko
/lib/modules/2.6.25-2-powerpc64-smp/kernel/drivers/char/ps3flash.ko
/lib/modules/2.6.25-2-powerpc64-smp/kernel/drivers/mtd/devices/mtd_dataflash.ko
/usr/bin/btcflash
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/program/libflash680lp.so
/usr/sbin/ps3-flash-util
/usr/share/flashblock
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flashblock.xpm
/usr/share/doc/flashblock
/usr/share/doc/flashblock/README.Debian
/usr/share/doc/flashblock/changelog.Debian.gz
/usr/share/doc/flashblock/copyright
/usr/share/flashblock/chrome
/usr/share/flashblock/chrome.manifest
/usr/share/flashblock/defaults
/usr/share/flashblock/install.js
/usr/share/flashblock/install.rdf
/usr/share/flashblock/chrome/flashblock.jar
/usr/share/flashblock/defaults/preferences
/usr/share/flashblock/defaults/preferences/flashblock.js
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/Human/16x16/devices/media-flash.png
/usr/share/icons/Human/22x22/devices/media-flash-cf.png
/usr/share/icons/Human/22x22/devices/media-flash.png
/usr/share/icons/Human/24x24/devices/media-flash-cf.png
/usr/share/icons/Human/24x24/devices/media-flash-ms.png
/usr/share/icons/Human/24x24/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-cf.png
/usr/share/icons/Human/48x48/devices/media-flash-ms.png
/usr/share/icons/Human/48x48/devices/media-flash.png
/usr/share/icons/Human/scalable/devices/media-flash-cf.svg
/usr/share/icons/Human/scalable/devices/media-flash-ms.svg
/usr/share/icons/Human/scalable/devices/media-flash.svg
/usr/share/icons/gnome/16x16/devices/media-flash.png
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/22x22/devices/media-flash.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/24x24/devices/media-flash.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/32x32/devices/media-flash.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/scalable/devices/media-flash.svg
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.svg
/usr/share/icons/oxygen/128x128/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/128x128/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/128x128/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/128x128/devices/media-flash.png
/usr/share/icons/oxygen/16x16/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/16x16/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/16x16/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/16x16/devices/media-flash.png
/usr/share/icons/oxygen/22x22/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/22x22/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/22x22/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/22x22/devices/media-flash.png
/usr/share/icons/oxygen/32x32/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/32x32/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/32x32/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/32x32/devices/media-flash.png
/usr/share/icons/oxygen/48x48/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/48x48/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/48x48/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/48x48/devices/media-flash.png
/usr/share/icons/oxygen/64x64/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/64x64/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/64x64/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/64x64/devices/media-flash.png
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-shockwave-flash.xml
/usr/share/mozilla-extensions/flashblock
/usr/src/linux-headers-2.6.25-2-powerpc/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.25-2-powerpc64-smp/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.25-2-powerpc64-smp/include/config/ps3/flash.h
/usr/src/linux-headers-2.6.25-2-powerpc64-smp/include/config/rtas/flash.h
/usr/src/linux-ports-headers-2.6.25-2/include/asm-arm/nwflash.h
/usr/src/linux-ports-headers-2.6.25-2/include/asm-arm/mach/flash.h
/usr/src/linux-ports-headers-2.6.25-2/include/asm-cris/axisflashmap.h
/usr/src/linux-ports-headers-2.6.25-2/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-ports-headers-2.6.25-2/include/asm-sparc/jsflash.h
/usr/src/linux-ports-headers-2.6.25-2/include/linux/mtd/flashchip.h
/usr/src/linux-ports-headers-2.6.25-2/include/linux/spi/flash.h
/var/cache/apt/archives/flashblock_1.3.10a~snapshot20080611-0ubuntu2_all.deb
/var/lib/dpkg/info/flashblock.list
/var/lib/dpkg/info/flashblock.md5sums
swati@psubuntu:~$ sudo apt-get remove swfdec-mozilla
[sudo] password for swati: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
swati@psubuntu:~$ sudo apt-get remove gnash-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnash-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 6877kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135755 files and directories currently installed.)
Removing gnash-common ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
swati@psubuntu:~$ 


```
So you see that I tried to remove gnash-common.

Now the about:plugins

```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.24.3

    File name: libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
IcedTea Web Browser Plugin

    File name: IcedTeaPlugin.so
    The IcedTea Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
```

---

### Post by overdrank on 2008-12-03
> **lunar said:**
> First applogize for posting it in 2 places. Didnt know if this would fall under beginner talk or installation.



I just thought this would be the best subforum to assist you. ;)

---

### Post by gandaran on 2008-12-03
the problem could be due to flashblock extension, disable or remove it!
are you running ubuntu 64-bits
you have adobe flash installed in the correct plugins directory but if you used the 32-bits tar.gz package to install flash on a 64-bits ubuntu it won't work, you either install the flashplugin-nonfree package or get the 64-bits beta flash from adobe.

---

### Post by lunar on 2008-12-03
Ok. I have removed the flash block. Still same result - couldnt play youtube vedios

The problem looks like adobe flash may not be installed properly.
In firefox when I go to tools->addons->plugins I dont see adobe flash there.
I see default plugin, demo print plugin, Divx web player, IcedTea Web Browser, quick time, Totem web, Windows media player.

---

### Post by gandaran on 2008-12-03
> **lunar said:**
> Ok. I have removed the flash block. Still same result - couldnt play youtube vedios

The problem looks like adobe flash may not be installed properly.
In firefox when I go to tools->addons->plugins I dont see adobe flash there.
I see default plugin, demo print plugin, Divx web player, IcedTea Web Browser, quick time, Totem web, Windows media player.
okay read my last edited post again

> are you running ubuntu 64-bits
you have adobe flash installed in the correct plugins directory but if you used the 32-bits tar.gz package to install flash on a 64-bits ubuntu it won't work, you either install the flashplugin-nonfree package or get the 64-bits beta flash from adobe.

---

### Post by philinux on 2008-12-03
Install the non free plugin

sudo apt-get install flashplugin-nonfree

then locate libflashplayer.so

It should have installed to
/usr/lib/flashplugin-nonfree

---

### Post by lunar on 2008-12-03
I tried the following before. couldn't get it installed

swati@psubuntu:/usr/lib$ ls libflashplayer.so
ls: cannot access libflashplayer.so: No such file or directory
swati@psubuntu:/usr/lib$ pwd
/usr/lib
swati@psubuntu:/usr/lib$ sudo apt-get install flashplugin-nonfree
[sudo] password for swati: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
swati@psubuntu:/usr/lib$

---

### Post by gandaran on 2008-12-03
> **lunar said:**
> I tried the following before. couldn't get it installed

swati@psubuntu:/usr/lib$ ls libflashplayer.so
ls: cannot access libflashplayer.so: No such file or directory
swati@psubuntu:/usr/lib$ pwd
/usr/lib
swati@psubuntu:/usr/lib$ sudo apt-get install flashplugin-nonfree
[sudo] password for swati: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
swati@psubuntu:/usr/lib$
check that you have ubuntu sofware channels enabled » system » administration » software scources » ubuntu software tab , tick the first 4 channels and on update tab tick the first 2 channels (security and recommended) 
run sudo apt-get update then try installing the flashplugin-nonfree again
remove every libflashplayer.so file from your system first, the flashplugin-nonfree installs the libflashplayer.so to the same plugins directory you have flash installed and this could mess things up.
and about the ubuntu, is it 32-bits or 64-bits

---

### Post by lunar on 2008-12-03
swati@psubuntu:~$ uname -ma
Linux psubuntu 2.6.25-2-powerpc64-smp #1 SMP Tue Sep 30 16:40:22 UTC 2008 ppc64 GNU/Linux

so I am thinking 64bit

ati@psubuntu:~$ sudo apt-get update
[sudo] password for swati: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg           
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid Release.gpg
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/main Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/universe Translation-en_US      
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates Release.gpg
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release 
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release              
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates Release                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                 
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid/multiverse Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) intrepid-updates/multiverse Packages
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-powerpc/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-powerpc/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-powerpc/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-powerpc/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
swati@psubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate


I have made sure the first 4 channels are ticked and 2 in in update tab.

Did the following too

swati@psubuntu:~$ sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
swati@psubuntu:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
swati@psubuntu:~$ sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
swati@psubuntu:~$ sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
swati@psubuntu:~$ sudo rm -rfd /usr/lib/nspluginwrapper

---

### Post by gandaran on 2008-12-03
you have some channels that are not connecting, don't know why, can you post the output of **gedit /etc/apt/sources.list** 
look if it's really a 64-bits ubuntu, download this 64-bits tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html), just unpack and move the libflashplayer.so file to /usr/lib/mozilla/plugins, should work with the flash just installed in this directory

---

### Post by timcredible on 2008-12-03
adobe hasn't released a version of flash for the ps3 yet.

---

### Post by timcredible on 2008-12-03
.

---

### Post by Tom--d on 2008-12-03
PS3 is not 32bit nor 64bit. Its PowerPC. Adobe have not realeased Flash for it yet.

Try Gnash (If they support the archituture).

---

### Post by lunar on 2008-12-03
ohh ok. Thank you very much for all your help. I will try to install  Gnash.

---

### Post by dreambig on 2009-01-16
Lunar, Any luck with installing Gnash on your PS3? I have just bought a PS3 and would like to watch movies on Hulu, surfthechannel and other flash based websites. The idea is free tv.

---


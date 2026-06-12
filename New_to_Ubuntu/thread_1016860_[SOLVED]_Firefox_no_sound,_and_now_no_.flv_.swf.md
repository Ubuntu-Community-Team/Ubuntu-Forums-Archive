---
title: "[SOLVED] Firefox: no sound, and now: no .flv .swf?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by LastWho on 2008-12-20
Hi
i m using Ubuntu hardy, and i had from the beginning 2 problems:[INDENT]
- cannot play Sound on both mozilla and other players (e.g amarok)

- cannot open swf files with totem movie player (but only with mozilla)

[/INDENT]So i tried to solve theses on my own like any responsible adult, and now i ve 3 problems:[INDENT]- cannot play sound in mozilla at all, even if there is no other player opened before

- Neither firefox nor totem (or any other player) can open swf files \\:D/

- firefox cannot open flv files too


[/INDENT]Now i m crying HEEEEEEEEEEEEEEEEEEELLLPPP please!! :cry:










-------------
**Other useless/usefull informations:**
from what i remember i did the following:[INDENT]- Sound configuration: System --> preferences --> Sound: i set everything as ALSA 
take a look here
[[IMG]http://img178.imageshack.us/img178/571/alsast2.th.jpg[/IMG]]("http://img178.imageshack.us/my.php?image=alsast2.jpg")


- i installed aoss and tried to open mozilla like this:
```
aoss firefox
```
- i tried the [wiki on Dmix]("http://alsa.opensrc.org/Dmix"): theses 2 tests came "+", so i stoped at the 2 step

```
alsaplayer -o alsa -d plug:dmix some.mp3 &
aplay -D plug:dmix some.wav &
alsaplayer -o alsa -d plug:dmix some.mp3 &

aoss mpg123 some.mp3
```


- I installed this package:
```
sudo aptitude install libflashsupport
```- The last thing i ve tried is this:
```
sudo apt-get remove swfdec-mozilla && sudo apt-get install --reinstall flashplugin-nonfree
```i did it just before i got this error message on firefox:
[[IMG]http://img206.imageshack.us/img206/2944/flvic8.th.jpg[/IMG]](http://img206.imageshack.us/my.php?image=flvic8.jpg)



- At last you may ask for this:
```
sudo updatedb
locate flash
cat /etc/lsb-release
uname -m
dpkg -s flashplugin-nonfree
dpkg -s swfdec-mozilla
dpkg -s mozilla-plugin-gnash
```[INDENT] voilà:
```
sudo updatedb
ucef@ucef-desktop:~$ locate flash
/etc/alternatives/firefox-flashplugin
/etc/alternatives/iceape-flashplugin
/etc/alternatives/iceweasel-flashplugin
/etc/alternatives/midbrowser-flashplugin
/etc/alternatives/mozilla-flashplugin
/etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-flashplugin
/home/ucef/.fr-15vGxb/install_flash_player_9_linux
/home/ucef/.fr-15vGxb/install_flash_player_9_linux/flashplayer-installer
/home/ucef/.fr-H8W7BA/install_flash_player_9_linux
/home/ucef/.fr-H8W7BA/install_flash_player_9_linux/libflashplayer.so
/home/ucef/.fr-JO3QNa/install_flash_player_9_linux
/home/ucef/.fr-JO3QNa/install_flash_player_9_linux/flashplayer-installer
/home/ucef/.fr-Nvv6HG/install_flash_player_9_linux
/home/ucef/.fr-Nvv6HG/install_flash_player_9_linux/libflashplayer.so
/home/ucef/.fr-T9haJk/install_flash_player_9_linux
/home/ucef/.fr-T9haJk/install_flash_player_9_linux/libflashplayer.so
/home/ucef/.ies4linux/downloads/swflash.cab
/home/ucef/.ies4linux/ie6/drive_c/windows/inf/swflash.inf
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flash.quantserve.com
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flashfabrica.com
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flash.quantserve.com/com.quantserve.sol
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flashfabrica.com/f_learning
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flashfabrica.com/f_learning/brain
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flashfabrica.com/f_learning/brain/brain01.swf
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/flashfabrica.com/f_learning/brain/brain01.swf/save_data.sol
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.dailymotion.com/flash
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.dailymotion.com/flash/dmplayer
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.dailymotion.com/flash/dmplayer/dmplayer-fr.swf
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.dailymotion.com/flash/dmplayer/dmplayer-fr.swf/dmplayer.sol
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.redtube.com/_playerx/flash
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.redtube.com/_playerx/flash/client_players
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.redtube.com/_playerx/flash/client_players/redtube
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.redtube.com/_playerx/flash/client_players/redtube/xmoov-flv-player3.swf
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.redtube.com/_playerx/flash/client_players/redtube/xmoov-flv-player3.swf/xmoov.sol
/home/ucef/.macromedia/Flash_Player/#SharedObjects/BHM58FC5/www.redtube.com/_playerx/flash/client_players/redtube/xmoov-flv-player3.swf/xmoov_redtube_original.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#content.beeg.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#documents.scribd.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#dsc.discovery.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flashfabrica.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#img103.imageshack.us
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#l.yimg.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources-p3.imeem.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#skype.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#static.searchme.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#video.google.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#widget-cdn.meebo.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.bbc.co.uk
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.blogger.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.dailymotion.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.emusic.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.france24.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.redtube.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.youtube.com
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#content.beeg.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#documents.scribd.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#dsc.discovery.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flashfabrica.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#img103.imageshack.us/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#l.yimg.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources-p3.imeem.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#skype.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#static.searchme.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#video.google.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#widget-cdn.meebo.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.bbc.co.uk/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.blogger.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.dailymotion.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.emusic.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.france24.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.redtube.com/settings.sol
/home/ucef/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.youtube.com/settings.sol
/home/ucef/.mozilla/firefox/urohwh8j.default/extensions/{3d7eb24f-2740-49df-8937-200b1cc08f8a}/chrome/flashblock.jar
/home/ucef/.mozilla/firefox/urohwh8j.default/extensions/{3d7eb24f-2740-49df-8937-200b1cc08f8a}/defaults/preferences/flashblock.js
/home/ucef/.winetrickscache/install_flash_player.exe
/home/ucef/.winetrickscache/install_flash_player_ax.exe
/home/ucef/Downloads/trivia-downloads/flash.rpm
/home/ucef/ffmpeg/libavcodec/flashsv.c
/home/ucef/ffmpeg/libavcodec/flashsv.d
/home/ucef/ffmpeg/libavcodec/flashsv.o
/home/ucef/ffmpeg/libavcodec/flashsvenc.c
/home/ucef/ffmpeg/libavcodec/flashsvenc.d
/home/ucef/ffmpeg/libavcodec/flashsvenc.o
/home/ucef/ffmpeg/libavcodec/.svn/text-base/flashsv.c.svn-base
/home/ucef/ffmpeg/libavcodec/.svn/text-base/flashsvenc.c.svn-base
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/opt/openoffice.org/basis3.0/program/libflashli.so
/usr/bin/btcflash
/usr/lib/flashplugin-nonfree
/usr/lib/libflashsupport.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/share/amsn/utils/linux/linflash
/usr/share/amsn/utils/linux/linflash/flash.so
/usr/share/amsn/utils/linux/linflash/pkgIndex.tcl
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flashblock.xpm
/usr/share/doc/flashplugin-nonfree
/usr/share/doc/libflashsupport
/usr/share/doc/flashplugin-nonfree/changelog.gz
/usr/share/doc/flashplugin-nonfree/copyright
/usr/share/doc/libflashsupport/changelog.Debian.gz
/usr/share/doc/libflashsupport/copyright
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
/usr/share/icons/crystalsvg/128x128/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/128x128/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/16x16/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/16x16/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/22x22/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/22x22/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/32x32/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/32x32/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/48x48/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/48x48/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/64x64/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/64x64/devices/compact_flash_unmount.png
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
/usr/share/lintian/overrides/flashplugin-nonfree
/usr/share/lintian/overrides/libflashsupport
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-flash-video.xml
/usr/share/mime/application/x-shockwave-flash.xml
/usr/share/mimelnk/application/x-shockwave-flash.desktop
/usr/src/linux-headers-2.6.24-16/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-16/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-16/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-16/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-16/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-16/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-16/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/scx200/docflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-19/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-19/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-19/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-19/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/scx200/docflash.h
/var/cache/flashplugin-nonfree
/var/cache/apt/archives/flashplugin-nonfree_10.0.12.36ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/flashplugin-nonfree_9.0.152.0ubuntu1~gutsy1_i386.deb
/var/cache/apt/archives/libflashsupport_1.9-0ubuntu1_i386.deb
/var/cache/flashplugin-nonfree/flashplayer10_install_linux_081108.tar.gz
/var/cache/flashplugin-nonfree/install_flash_player_10_linux.tar.gz
/var/cache/flashplugin-nonfree/install_flash_player_9.tar.gz
/var/lib/flashplugin-nonfree
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/alternatives/iceape-flashplugin
/var/lib/dpkg/alternatives/iceweasel-flashplugin
/var/lib/dpkg/alternatives/midbrowser-flashplugin
/var/lib/dpkg/alternatives/mozilla-flashplugin
/var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
/var/lib/dpkg/alternatives/xulrunner-flashplugin
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.md5sums
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.templates
/var/lib/dpkg/info/libflashsupport.list
/var/lib/dpkg/info/libflashsupport.md5sums
/var/lib/dpkg/info/libflashsupport.postinst
ucef@ucef-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
ucef@ucef-desktop:~$ uname -m
i686
ucef@ucef-desktop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 156
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.152.0ubuntu1~gutsy1
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g
Suggests: firefox, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplugin (<< 6), xfs (<< 1:1.0.1-5), flashplayer-mozilla
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: http://wiki.ubuntu.com/FlashPlayer9
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
ucef@ucef-desktop:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: purge ok not-installed
Priority: optional
Section: utils
~$ dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 308
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Source: gnash
Version: 0.8.2-0ubuntu3
Depends: gnash (= 0.8.2-0ubuntu3), libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1-21), libstdc++6 (>= 4.2.1-4), libx11-6, libxi6
Description: free SWF movie player - Plugin for Mozilla and derivatives
 Gnash is a free Flash movie player, which works either standalone, or as
 plugin for Firefox/Mozilla or Konqueror.
 .
 This package includes the plugin for Firefox/Mozilla Web Browser.
 .
 Homepage: http://www.gnu.org/software/gnash/
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Gnash SWF Player
Original-Maintainer: Miriam Ruiz <little_miry@yahoo.es>

```[/INDENT][/INDENT]

---

### Post by MyR on 2008-12-20
I recommend removing flashplugin-nonfree and installing adobe-flashplugin (it installs flash 10 rather than flash 9) available from the partner repo.
but that probably won't fix your problems.

Make sure you dont have any browsers open while installing/uninstalling flash.

I notice in your screenshot that you have the device set to OSS mixer, which is probably not what you want when manually setting everything to use ALSA. try changing that to alsa mixer and everything else to autodetect. good luck! ;]

peace

---

### Post by kansasnoob on 2008-12-20
I suggest following the steps for Hardy here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I'll also parse your info a bit closer, but psyke83 is IMHO unsurpassed in his knowledge of Pulse Audio.

---

### Post by gandaran on 2008-12-20
LastWho
don't install gnash, swfdec or any other flash except adobe flash, you must only use one flash package for firefox or you'll run into problems, you can install the flashplugin-nonfree  (adobe flash 9) from synaptic, if you find flash sound problems with this package remove it (+ the libflashsupport if you have it installed) and get the flash 10 .deb package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
if you still get flash sound issues with flash 10 then you have to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
about the .swf files, totem cannot play these files only .flv or flash videos, the same goes for vlc, they only play flash videos not shockwave
for .swf or shockwave you have to get a stand alone player like gnash or swfdec or better get the adobe stand alone flash player which only plays shockwave not flash videos.

---

### Post by LastWho on 2008-12-20
everything works like a mircle lol
one lesson: when u re a noob don't google, ask! :p

thank u so much! solved

---


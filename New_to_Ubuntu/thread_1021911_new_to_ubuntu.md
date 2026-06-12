---
title: "new to ubuntu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Drowning_Child on 2008-12-26
im looking for some help for an absolute beginner, and i mean absolute!

---

### Post by RomeReactor on 2008-12-26
Hi. It helps to give your posts more meaningful titles, such as "trouble installing printer in Ubuntu 64-bit". Please give us more information regarding your problem.

---

### Post by sayems on 2008-12-26
Install everything on Ubuntu with
***********************************
* [http://appnr.com/](http://appnr.com/)

* [http://www.playdeb.net/](http://www.playdeb.net/)

* [http://www.getdeb.net/](http://www.getdeb.net/)


Some of the things you can do after installing ubuntu on your machine .

1.Putting your repositories in order
***************************************
$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

1.Installing Multimedia codecs for GStreamer
*********************************************
sudo apt-get install faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install w32codecs

sudo apt-get install build-essential

3.Avant Window Navigator
**************************
echo "deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list

echo "deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk

4.Installing MPlayer with all codecs and dvd playing support
*************************************************************
sudo apt-get install mplayer

sudo apt-get install w32codecs

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot

sudo /usr/share/doc/libdvdread3/install-css.sh

5.RealPlayer
************
[http://www.real.com/linux/](http://www.real.com/linux/)

chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

6.Flash and Java Support
************************
sudo apt-get install flashplugin-nonfree libflashsupport

sudo apt-get install mozilla-plugin-gnash

sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

7.Installing Microsoft fonts package
*************************************
sudo apt-get install msttcorefonts

sudo fc-cache

8.Adobe Reader
**************
sudo apt-get install acroread

9.Installing VLC Player
***********************
sudo apt-get install vlc

10.Ubuntu Tweak
***************
[http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak)

11.Strata Human 1.0
*******************
[https://addons.mozilla.org/en-US/firefox/addon/8105](https://addons.mozilla.org/en-US/firefox/addon/8105)

12.Midnight Commander
*********************
sudo apt-get install mc

13.Figlet
*********
$ sudo apt-get install figlet

14.Startup Manager
******************
sudo apt-get install startupmanager

15.GParted
**********
sudo apt-get install gparted

16.NumlockX
***********
sudo apt-get install gparted


17.Hamster
**********
sudo apt-get install hamster-applet


18.Free Disk Space from APT’s Cache
***********************************
sudo apt-get autoclean

19.StackSwitch and Wallpaper Plugins with Compiz 0.7.6
******************************************************
sudo apt-get install stackswitch

20.How to Install Cursor Themes
*******************************
[http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/](http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/)

21.p7zip Adds Built-In 7-Zip Tools to Ubuntu
********************************************
sudo apt-get install p7zip

22.Convert Red Hat/Fedora Packages for Ubuntu/Debian Installation
*****************************************************************
$sudo alien -k name-of-rpm-file.rpm

23.Global Menu
**************
[http://www.downloadsquad.com/2008/02/21/get-mac-style-menus-on-ubuntu-with-global-menu/](http://www.downloadsquad.com/2008/02/21/get-mac-style-menus-on-ubuntu-with-global-menu/)

24.Enable DVD Playback in Ubuntu in Two Commands
*************************************************
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

25.Howto install gnome-do in Ubuntu Hardy
*****************************************
[http://www.ubuntugeek.com/howto-install-gnome-do-in-ubuntu-hardy-and-gutsy.html](http://www.ubuntugeek.com/howto-install-gnome-do-in-ubuntu-hardy-and-gutsy.html)

29.Turn Your Ubuntu Hardy to Mac OSX Leopard
*******************************************************
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

30.Install Google Gadgets for Linux on Ubuntu
*********************************************
[http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/](http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/)

31.(Optional) btnx Customizes a Multi-Button Mouse for Linux
************************************************************
[http://lifehacker.com/384698/btnx-customizes-a-multi+button-mouse-for-linux](http://lifehacker.com/384698/btnx-customizes-a-multi+button-mouse-for-linux)

32.Watch YouTube Clips Inside GNOME's Built-In Movie Player
*****************************************************
[http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/](http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/)

33.Custom Compiz Effects in Ubuntu 8.04
*****************************************
[http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/)

34.(Optional) Use an OS X-Style Global Menu in Ubuntu
***************************************************
[http://lifehacker.com/359571/use-an-os-x+style-global-menu-in-ubuntu](http://lifehacker.com/359571/use-an-os-x+style-global-menu-in-ubuntu)

35.Toggle Desktop Effects with Compiz-Switch
*********************************************
[http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

36.Rip DVDs in Linux the (Semi-)Easy Way
**************************************
[http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php](http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php)

37.Hide Partition Icons on GNOME Desktops
**************************************
[http://lifehacker.com/software/linux-tip/hide-partition-icons-on-gnome-desktops-316179.php](http://lifehacker.com/software/linux-tip/hide-partition-icons-on-gnome-desktops-316179.php)

38.Share a Firefox Profile Between Ubuntu and Windows
********************************************
[http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/](http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/)

39.Banshee Media Player
***************************
[http://banshee-project.org/download/](http://banshee-project.org/download/)

40.Gnome-Do
*************
[http://do.davebsd.com/](http://do.davebsd.com/)

41.Ubuntu System Panel
*********************
[http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

1.Slab (Start Menu)
*******************
[https://wiki.ubuntu.com/Slab](https://wiki.ubuntu.com/Slab)

42.Getdeb.net


43.Playdeb - The Gaming Repository for Ubuntu
*******************************************
[http://tombuntu.com/index.php/2007/10/22/the-apturl-protocol-handler-in-ubuntu-710/](http://tombuntu.com/index.php/2007/10/22/the-apturl-protocol-handler-in-ubuntu-710/)

44.Hamster Time Tracking for GNOME
*******************************
[http://tombuntu.com/index.php/2008/08/08/hamster-time-tracking-for-gnome/](http://tombuntu.com/index.php/2008/08/08/hamster-time-tracking-for-gnome/)

45.Replace the System Beep with a Compiz Effect
**********************************************
[http://tombuntu.com/index.php/2008/08/04/replace-the-system-beep-with-a-compiz-effect/](http://tombuntu.com/index.php/2008/08/04/replace-the-system-beep-with-a-compiz-effect/)

46.Free Disk Space from APT’s Cache
**********************************
[http://tombuntu.com/index.php/2008/08/01/free-disk-space-from-apts-cache/](http://tombuntu.com/index.php/2008/08/01/free-disk-space-from-apts-cache/)

47.Install Three Experimental Compiz Plugins
******************************************
[http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/](http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/)

48.Launchy Application Launcher Released for Linux
*********************************************
[http://tombuntu.com/index.php/2008/07/29/launchy-application-launcher-released-for-linux/](http://tombuntu.com/index.php/2008/07/29/launchy-application-launcher-released-for-linux/)

49.Upgrade to the Latest Compiz Fusion Release
********************************************
[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)

50.StackSwitch and Wallpaper Plugins with Compiz 0.7.6
******************************************************
[http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/](http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/)

51.Guake Drop-Down Terminal for GNOME
**************************************
[http://tombuntu.com/index.php/2008/07/24/guake-drop-down-terminal-for-gnome/](http://tombuntu.com/index.php/2008/07/24/guake-drop-down-terminal-for-gnome/)

52.Install Google Gadgets for Linux on Ubuntu
*********************************************
[http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/](http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/)

53.How to Install Cursor Themes
***********************************
[http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/](http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/)

54.Enable Commercial DVD Playback in Ubuntu
*********************************************
[http://tombuntu.com/index.php/2008/05/13/enable-commercial-dvd-playback-in-ubuntu/](http://tombuntu.com/index.php/2008/05/13/enable-commercial-dvd-playback-in-ubuntu/)

55.Install Extra GNOME Themes
*************************************
[http://tombuntu.com/index.php/2008/04/29/install-extra-gnome-themes/](http://tombuntu.com/index.php/2008/04/29/install-extra-gnome-themes/)

56.Workaround for Pink Shadows with Compiz
**********************************************
sudo ln -sf /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so

57.Vista Basic By drvdw (Desktop Themes)
*******************************************
[http://art.gnome.org/themes/metacity/1337](http://art.gnome.org/themes/metacity/1337)

58.Aurora by memo_mapc (Backgrounds/Wallpaper)
************************************************
[http://art.gnome.org/backgrounds/abstract/2519](http://art.gnome.org/backgrounds/abstract/2519)

59.OSX (GNOME Icon)
*******************
[http://www.gnome-look.org/content/show.php/OSX?content=31618](http://www.gnome-look.org/content/show.php/OSX?content=31618)

60.GNOME-colors (GNOME Icon Theme)
**********************************
[http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562](http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562)

1.Show the Computer, Home, and Trash desktop icons in GNOME
***********************************************************
Alt+F2: gconf-editor
Choose apps->nautilus->desktop.
Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.

1.KDE4 Oxygenstyle update
****************************
[http://kims-area.com/?q=node/63](http://kims-area.com/?q=node/63)
Download KDE4 Oxygen GTK theme .DEB

1.KDE Oxygenstyle Wallpaper
**************************
[http://pinheiro-kde.blogspot.com/](http://pinheiro-kde.blogspot.com/)

1.Change Gnome Panel Text Color
*******************************
$ gedit ~/.gtkrc-2.0
style "panel"
{
fg[NORMAL] = "#c6d8e1" #<--edit for panel font color
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"

# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#2ef60c" #yellow "#ffffff"
# base[PRELIGHT] = "#f60c22" #dark red "#EFEFEF"
# base[ACTIVE] = "#3c06ff" #blue "#D0D0D0"
base[SELECTED] = "#000000" #"#DAB566"
# base[INSENSITIVE] = "#d8d0b2" #biege "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Applet*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

1.Tweak Firefox 3 full screen mode
**********************************
[http://mozillalinks.org/wp/2008/06/tweak-firefox-3-full-screen-mode/](http://mozillalinks.org/wp/2008/06/tweak-firefox-3-full-screen-mode/)

1.Ubuntu Cheat Sheet
*********************
[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

1.A Day Without X
*****************
[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

1.More terminal programs you should be using … like a pro
*********************************************************
[http://kmandla.wordpress.com/2007/05/17/more-terminal-programs-you-should-be-using-like-a-pro/](http://kmandla.wordpress.com/2007/05/17/more-terminal-programs-you-should-be-using-like-a-pro/)

1.Paytube: YouTube video converter for Ubuntu Linux
*************************************************
[http://www.getdeb.net/release/3057](http://www.getdeb.net/release/3057)

1.Ultamatix: Install 101 Applications in One click including Games,codecs,applications
***********************************************************************************
[http://www.ubuntugeek.com/ultamatix-install-101-applications-in-one-click-including-gamescodecsapplications.html](http://www.ubuntugeek.com/ultamatix-install-101-applications-in-one-click-including-gamescodecsapplications.html)
Use the Synaptic Package Manager

1.Youtube-dl - Download videos from youtube in Ubuntu
*******************************************************
[http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html#more-556](http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html#more-556)


1.Ubuntu System Panel Setting
******************************

USP Bottom Text [Start]

Application Width - 230
Application Height - 500

Shortcut Height - 352
Shortcut Width - 180

System Height - 130
System Width - 200

1.Use a Screensaver as Desktop Wallpaper
*****************************************
[http://lifehacker.com/software/linux-tip/use-a-screensaver-as-desktop-wallpaper-299410.php](http://lifehacker.com/software/linux-tip/use-a-screensaver-as-desktop-wallpaper-299410.php)

1.Animated Wallpaper with Compiz Fusion on Ubuntu
[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

1.Fix for firefox crashes on flash contents when using libflashsupport in hardy
**********************************************
[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

1.The other Firefox 3 themes
******************************
[http://mozillalinks.org/wp/2008/07/the-other-firefox-3-themes/](http://mozillalinks.org/wp/2008/07/the-other-firefox-3-themes/)

Install VLC media player 0.9.2 in Ubuntu
******************************************
[http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

Customize Ubuntu A-Z
*********************
[http://ubuntuforums.org/showthread.php?t=856190&highlight=panel+background](http://ubuntuforums.org/showthread.php?t=856190&highlight=panel+background)

8 Ways to Maintain a Clean, Lean Ubuntu Machine
************************************************
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/)



Ubuntu 8.10 (Intrepid Ibex)

Authentication
**************
$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
$ wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -
$ wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | apt-key add -
apt-get update

$ sudo gedit /etc/apt/sources.list

* Replace everything with the following lines

## Intrepid Ibex
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse

## Canonical Partner
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

## Ubuntu Tweak
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main

## Emesene
deb [http://apt.emesene.org/](http://apt.emesene.org/) ./

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Google software repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

## Banshee
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

## Avant Window Navigator
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main

## GNOME DO
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main

## GScrot
deb [http://ppa.launchpad.net/gscrot/ubuntu](http://ppa.launchpad.net/gscrot/ubuntu) intrepid main

## Terminator
deb [http://ppa.launchpad.net/gnome-terminator/ubuntu](http://ppa.launchpad.net/gnome-terminator/ubuntu) intrepid main

## Compiz Fusion
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main

## Firefox
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main

## Midori
deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main

## Opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free

## Hamster
deb [http://ppa.launchpad.net/hamster.support/ubuntu](http://ppa.launchpad.net/hamster.support/ubuntu) hardy main

## VLC
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) intrepid main

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

## Screenlets
# deb [http://ppa.launchpad.net/3rd-party-screenlets-team/ubuntu](http://ppa.launchpad.net/3rd-party-screenlets-team/ubuntu) hardy main
#deb [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_8.04](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_8.04) ./

## KDE 4
#deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

## VirtualBox
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

## Pidgin
# deb [http://ppa.launchpad.net/pidgin-developers/ubuntu](http://ppa.launchpad.net/pidgin-developers/ubuntu) intrepid main
# deb [http://ppa.launchpad.net/reda.ea/ubuntu](http://ppa.launchpad.net/reda.ea/ubuntu) intrepid main

## Kernel
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) intrepid main

## PlayDeb
# deb mirror://www.getdeb.net/playdeb-mirror/intrepid/// intrepid/






Top Bookmarks:
****************
* [http://lifehacker.com/tag/ubuntu/](http://lifehacker.com/tag/ubuntu/)
* [http://synapticism.wordpress.com/2008/08/31/top-7-best-kept-linux-secrets/](http://synapticism.wordpress.com/2008/08/31/top-7-best-kept-linux-secrets/)
* [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
* [http://www.easy-ubuntu-linux.com/custom-ubuntu-repositories.html](http://www.easy-ubuntu-linux.com/custom-ubuntu-repositories.html)
* [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
* [http://tombuntu.com/](http://tombuntu.com/)
* [http://blog.lxpages.com/2007/07/11/101-ubuntu-tips-tricks-and-tutorials/](http://blog.lxpages.com/2007/07/11/101-ubuntu-tips-tricks-and-tutorials/)
* [http://www.ubuntux.org/forums/ubuntu-linux/tips-tricks-customization-0](http://www.ubuntux.org/forums/ubuntu-linux/tips-tricks-customization-0)
* [http://www.rewardprograms.org/thefreegeek/features/17_musthave_free_apps_for_new_ubuntu_users.html](http://www.rewardprograms.org/thefreegeek/features/17_musthave_free_apps_for_new_ubuntu_users.html)
* [http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)
* [http://www.catswhocode.com/blog/featured/30-gnome-themes-to-enhance-your-ubuntu-experience-18](http://www.catswhocode.com/blog/featured/30-gnome-themes-to-enhance-your-ubuntu-experience-18)
* [http://www.howtogeek.com/tag/ubuntu/](http://www.howtogeek.com/tag/ubuntu/)
* [http://www.ubuntugeek.com/howto-install-gnome-do-in-ubuntu-hardy-and-gutsy.html](http://www.ubuntugeek.com/howto-install-gnome-do-in-ubuntu-hardy-and-gutsy.html)
* [http://www.getdeb.net/](http://www.getdeb.net/)
* [http://www.downloadsquad.com/2008/02/21/get-mac-style-menus-on-ubuntu-with-global-menu/](http://www.downloadsquad.com/2008/02/21/get-mac-style-menus-on-ubuntu-with-global-menu/)
* [http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/](http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/)
* [http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/](http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/)
* [http://linux-noob.com/review/smoothwall/express/3/install/index.html](http://linux-noob.com/review/smoothwall/express/3/install/index.html)
* [http://www.linux-tip.net/cms/content/view/316/26/1/0/](http://www.linux-tip.net/cms/content/view/316/26/1/0/)
* [http://www.informit.com/articles/article.aspx?p=1226928](http://www.informit.com/articles/article.aspx?p=1226928)
* [http://linuxcommand.org/](http://linuxcommand.org/)
* [http://www.vtc.com/](http://www.vtc.com/)
* [http://education-portal.com/articles/10_Sites_Offering_Free_Linux_Courses_Online.html](http://education-portal.com/articles/10_Sites_Offering_Free_Linux_Courses_Online.html)
* [http://beginlinux.org/](http://beginlinux.org/)
* [http://www.catswhocode.com/blog/featured/20-beautiful-dark-themes-for-gnome-and-ubuntu-418](http://www.catswhocode.com/blog/featured/20-beautiful-dark-themes-for-gnome-and-ubuntu-418)
* [http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
* [http://gnufreakz.wordpress.com/2008/08/26/how-to-customize-ubuntu/](http://gnufreakz.wordpress.com/2008/08/26/how-to-customize-ubuntu/)
* [http://allforlinux.blogspot.com/2008/08/best-themes-for-ubuntu.html](http://allforlinux.blogspot.com/2008/08/best-themes-for-ubuntu.html)
* [http://www.sizzledcore.com/2008/08/09/ubuntu-themes-awesome-themes-for-linux/](http://www.sizzledcore.com/2008/08/09/ubuntu-themes-awesome-themes-for-linux/)
* [http://dustinkirkland.wordpress.com/2008/09/05/announcing-the-ubuntu-manpage-repository-manpagesubuntucom/](http://dustinkirkland.wordpress.com/2008/09/05/announcing-the-ubuntu-manpage-repository-manpagesubuntucom/)
* [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
* [http://www.dsl.org/cookbook/cookbook_toc.html](http://www.dsl.org/cookbook/cookbook_toc.html)
* [http://ubuntu-rescue-remix.org/node/65](http://ubuntu-rescue-remix.org/node/65)
* [http://book.opensourceproject.org.cn/distrib/ubuntu/movingtoubuntu/](http://book.opensourceproject.org.cn/distrib/ubuntu/movingtoubuntu/)

I got too many of them, you don't need all that, let me know If you guys need tutorial for programming language..

---

### Post by Drowning_Child on 2008-12-26
i have it all installed & every thing i just want to learn all the basics i NEED to know

---

### Post by sayems on 2008-12-26
just play with it you will get to know the basic

---

### Post by RomeReactor on 2008-12-26
You can start with [this thread]("http://ubuntuforums.org/showthread.php?t=801404") at the top of the page. More help from the [official documentation]("https://help.ubuntu.com/8.10/index.html") and the [community documentation]("https://help.ubuntu.com/community"). And you can also press the "Help" button on your desktop to more information.

---

### Post by Drowning_Child on 2008-12-26
ok i want to install the game FoFiX(Frets on fire MFH Mod)
im wondering on how to work with all that
tried this: [http://www.fretsonfire.net/forums/viewtopic.php?p=315846](http://www.fretsonfire.net/forums/viewtopic.php?p=315846)
i got an error saying i could not get opengl.gl

---

### Post by RomeReactor on 2008-12-26
Can you give us more information about your computer (graphics card, processor, memory)? Also, please open a terminal (Applications->Accessories->Terminal), run this command:
```
glxinfo | grep rendering
```
and post the output.

---

### Post by Drowning_Child on 2008-12-26
tony@tony-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
PC: Pentium 4 HT Duo
Ati9500
512 ram 
2 hdds(slave set for ubuntu, main XP)
nothing relly special

---

### Post by RomeReactor on 2008-12-26
Can you post the exact error message you got? It's likely that you need to install certain packages before trying to install the game.

---

### Post by Drowning_Child on 2008-12-26
tony@tony-desktop:~/fofix-read-only$ python FretsOnFire.py
python: can't open file 'FretsOnFire.py': [Errno 2] No such file or directory
tony@tony-desktop:~/fofix-read-only$ cd / src
tony@tony-desktop:/$ cd /home/tony/fofix-read-only/src
tony@tony-desktop:~/fofix-read-only/src$ python FretsOnFire.py
Traceback (most recent call last):
  File "FretsOnFire.py", line 38, in <module>
    from GameEngine import GameEngine
  File "/home/tony/fofix-read-only/src/GameEngine.py", line 31, in <module>
    from OpenGL.GL import *
ImportError: No module named OpenGL.GL
tony@tony-desktop:~/fofix-read-only/src$ sudo apt-get OpenGL.GL
E: Invalid operation OpenGL.GL
tony@tony-desktop:~/fofix-read-only/src$ sudo apt-get OpenGL.GL
E: Invalid operation OpenGL.GL
tony@tony-desktop:~/fofix-read-only/src$

---

### Post by RomeReactor on 2008-12-26
According to the site you need to have these packages installed:

* python-pygame
* python-opengl
* python-numpy
* python-numeric
* python-imaging
* python-vorbis
* python-ogg
* python-xml

If you don't have them yet, run this to install them:
```
sudo aptitude install python-pygame python-opengl python-numpy python-numeric python-imaging python-pyvorbis python-ogg python-xml subversion
```

Then try the game again.

---

### Post by Drowning_Child on 2008-12-26
thank you very very much!
i do not know what i did wrong before that it didnt work.
now i would like help on installing a drive for a harmonix guitar for ps3(goes through a USB wireless)

---

### Post by RomeReactor on 2008-12-26
Did you get the game to run?

As for the guitar, [this page]("http://fretsonfire.wikidot.com/using-guitar-hero-controller") says you only need to configure it.

---

### Post by Drowning_Child on 2008-12-26
yes it worked i tried setting the keys but nothing it doesnt pick up the presses
edit: nvm tried it and it worked thank you very much

---

### Post by e4uforums on 2010-04-13
> **RomeReactor said:**
> According to the site you need to have these packages installed:

* python-pygame
* python-opengl
* python-numpy
* python-numeric
* python-imaging
* python-vorbis
* python-ogg
* python-xml

If you don't have them yet, run this to install them:
```
sudo aptitude install python-pygame python-opengl python-numpy python-numeric python-imaging python-pyvorbis python-ogg python-xml subversion
```Then try the game again.

Sorry to post to such an old thread, but I've been messing with this for about an hour now and this solved my problems.  Thank you!

---


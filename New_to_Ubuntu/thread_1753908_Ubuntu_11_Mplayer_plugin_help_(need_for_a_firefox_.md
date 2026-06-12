---
title: "Ubuntu 11: Mplayer plugin help (need for a firefox toolbar)"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Fieari on 2011-05-09
Experience level: Just slightly above beginner. I know how to access a terminal, I know what permissions are, I know what sudo means, and I once followed a tutorial on compiling a program instead of using an auto installer. Other than that, only windows experience.


On behalf of my father, I am attempting to get the [Fox News Radio toolbar]("http://www.downloadmytoolbar.com/fox-news-talk/download1c.htm") installed and working, particularly for the radio part.  I have the toolbar, but the streaming radio feature won't work. Checking their [help section]("http://foxnewstalk.ourtoolbar.com/help/"), it seems it requires WMP to work.

Doing a google search, it seems WMP can be emulated in Ubuntu via something called mplayer, which also needs mplayer-plugin to be accessed from firefox.

I used the software center to get mplayer, but I can't figure out how to get the plugin. There are guides online, but none work.  I'm not even 100% sure I'm following the right track to get this thing working.  I do still have windows installed on a separate partition, maybe there's some way of linking the WMP from that? If so, I've no idea how.

Any advice?

---

### Post by lovinglinux on 2011-05-10
Install gecko-mediaplayer.

```
sudo apt-get install gecko-mediaplayer
```

I also advise to follow the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Fieari on 2011-05-10
Thanks for the help!  Alas, while gecko-mediaplayer appears to have installed properly, the streaming radio player still won't appear in the toolbar. I tried uninstalling/reinstalling the toolbar, and that didn't work either.

I've since been following the Howto you linked to, but it fails at about the third step.  This part:

```
:~$ sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'icedtea-gcjwebplugin' can't be removed
Virtual packages like 'libflashsupport' can't be removed
E: Unable to locate package libflash-mozplugin
```I've followed the steps for what to do if you get this error to no avail. I've even done the manual adding of the medibuntu repository. No dice.  Skipping this and going on to later steps also doesn't work...

```
~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mozilla-helix-player
E: Unable to locate package mozilla-mplayer
``````
~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-plugin-vlc totem-mozilla xine-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mozilla-helix-player
``````
~$ sudo apt-get install mplayer mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mozilla-mplayer
```Any ideas?  Or does natty just not support this?  Here's my sources.list:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

deb http://packages.medibuntu.org/ natty free non-free
deb-src http://packages.medibuntu.org/ natty free non-free
```

---

### Post by lovinglinux on 2011-05-10
The errors are probably because the tutorial hasn't been updated and the packages names have changed.

I have installed the toolbar on both Firefox 3.6 and 4.0. It doesn't work. I don't think is the plugin (mplayer or gecko-mediaplayer) fault. The extension throws some jasvascript errors, so I believe is not fully compatible or needs to be fixed.

Personally, I wouldn't install any add-ons, specially toolbars, that are not approved by Mozilla. You can get approved add-ons from [Mozilla Add-ons]("https://addons.mozilla.org") site. Unfortunately, the Fox News toolbar is not available there, but perhaps you can find an alternative.

---


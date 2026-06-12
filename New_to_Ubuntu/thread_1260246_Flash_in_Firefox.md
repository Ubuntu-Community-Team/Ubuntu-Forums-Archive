---
title: "Flash in Firefox"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by callmecynic on 2009-09-07
I've got my first install of Ubuntu on a netbook and I'm trying to make it utilitarian enough to be the family utility box.  One of the requirements is to be able to view video, Youtube and Hulu are the common sites.

Unfortunately, I can't get flash to run in Firefox.  On Youtube, clicking on a video brings me to the page for that video, but w/ no vido window.  Clicking on the Watch Video in new window brings up a blank, black window.  Picking a Hulu video brings up a blank, black window.

As far as I can tell on this forum and others, the pieces-parts are all there, so I'm stumped.  The details of OS, Firefox version, Firefox plugin, dpkg, Synaptics detail, and a listing of the mozilla plugins directory follow.

Ubuntu 9.0.4, 2.6.28-15
Firefox 3.0.13
==================
from about:plugins in Firefox

application/x-vlc-plugin VLC Multimedia Plugin  Yes     
application/vlc VLC Multimedia Plugin   Yes
video/x-google-vlc-plugin VLC Multimedia Plugin Yes     
  application/x-ogg Ogg multimedia file ogg Yes
application/ogg Ogg multimedia file ogg Yes     
audio/ogg Ogg Audio oga Yes
audio/x-ogg Ogg Audio ogg Yes   
video/ogg Ogg Video ogv Yes
video/x-ogg Ogg Video ogg Yes   
  application/annodex Annodex exchange format anx Yes 
audio/annodex   Annodex Audio axa Yes   
video/annodex Annodex Video axv Yes     
video/mpeg MPEG video mpg, mpeg, mpe Yes
audio/wav WAV audio wav Yes     
  audio/x-wav WAV audio wav Yes   
audio/mpeg MP3 audio mp3 Yes
application/x-nsv-vp3-mp3 NullSoft video nsv Yes
video/flv Flash video flv Yes   
application/x-totem-plugin Totem Multimedia plugin Yes
application/x-shockwave-flash   Shockwave Flash swf Yes 
  application/futuresplash FutureSplash Player spl Yes
=====================================
callmecynic@callmecynic-wind:~$ dpkg --get-selections  | more
acl                        install
acpi-support                    install
  acpid                        install
adduser                        install
adobe-flashplugin                install
<snip>
=======================================
Synaptic
lashplugin-nonfree
Version 10.0.32.18ubuntu0.9.04.1
=======================================
callmecynic@callmecynic-wind:~$ ls  /usr/lib/mozilla/plugins/
  flashplugin-alternative.so  libtotem-gmp-plugin.so
libflashplayer.so           libtotem-mully-plugin.so
libjavaplugin.so            libtotem-narrowspace-plugin.so
libtotem-cone-plugin.so
========================================

---

### Post by mapes12 on 2009-09-07
I haven't read down the full plugin list cos it made my eyes go funny. In 99% of cases you need to do this to fix your problem:

1. In Synaptic install ubuntu-restricted-extras then 
2. Cut and paste these Terminal commands for the other none free codecs: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by FreewheelinFrank on 2009-09-07
[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

Check out Medibuntu too.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by baltadt on 2009-09-14
I had the same problem and here is how I fixed it....

1) copy this tutorial to tomboy notes

2) download the tar.gz file to your desktop (save file not open) at..

[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz))

3) extract it to your desktop

4) close firefox (very important)

5) open a terminal window (applications-accessories-terminal) and enter the following


sudo cp /home/USERNAME/Desktop/libflashplayer.so /usr/lib/firefox/plugins

enter password

(make sure you replace your username for USERNAME. make sure Desktop is typed with a capital D.

6) open firefox click Tools----add-ons----plugins. this should have installed the new plugin called shockwave flash 10.0 r32

Have fun on hulu.com, smallworlds.com and other sites

---

### Post by Rob Maddison on 2009-09-14
I've just solved my problem in the same vein.

I had too many flash installations conflicting so used the instructions in another solved flash thread[ here]("http://http://ubuntuforums.org/showthread.php?t=1254328&highlight=flash")

Good luck whatever you try :-)

It seems there's as many solutions as there are problems you just have to find the one that works for you.

---

### Post by baltadt on 2009-09-15
Rob may not know this but when I clicked on the link in his post WOT (web of trust) alert me that the site is not trusted.  Be careful, it might be nothing, but I usually trust what WOT rates the sites.

---


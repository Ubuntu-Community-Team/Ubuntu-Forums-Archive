---
title: "sound gone after update"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by stevek123 on 2009-11-03
ubuntu/hardy 8.04....    I just ran about 12-15 updates that were listed without reviewing them all. The first of the set were security/firefox and I just ran with it. I came back after several hours and saw it required a reboot and did so. Sound that worked perfectly is now gone. 

Volume control has redslash/circle and says "No volume control GStreamer plugins and/or devices found." I have no idea what I updated or how to find that list. - otherwise i'd just remove the offenders.   

System log is gobbldygook to me.    

System/preferences/hardwareinfo recognizes & shows my Yamaha YMF-724F sound card present. 

System/Pref/sound shows all set for alsa but gives this when tested   "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument"

Honestly I'm totally lost, VERY frustrated. Any help?

---

### Post by stevek123 on 2009-11-03
found similar problem in another thread - worked 2 commands as follows.

steve@ubuntudesktop:~$ lspci | grep Audio
01:0c.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
steve@ubuntudesktop:~$ sudo lsmod | grep snd 
[sudo] password for steve: 
steve@ubuntudesktop:~$ sudo lsmod | grep snd 
steve@ubuntudesktop:~$ 

I get nothing for snd.....
FWIW Sys/Pref/Snd - Devices is empty. Nothing in dropdown menu.

---

### Post by stevek123 on 2009-11-03
GRRRR - I remember this mess. I've done this before! the answer is found here   [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

this will be my LAST freakin kernel update til the next LTS release.:mad:

---

### Post by stevek123 on 2009-11-04
sorry but I wanted to make sure that others know - anyone who searches/links here to my weak thread- solutions to sound problems are solved using this guide! It rocks. Even for a noob. Just follow it step by step - copy & paste. sure its a pain but it WORKS =
Comprehensive Sound Problem Solution Guide:KS

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---


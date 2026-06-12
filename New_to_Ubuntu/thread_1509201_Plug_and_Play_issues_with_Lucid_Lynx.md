---
title: "Plug and Play issues with Lucid Lynx"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by playing_with_matches on 2010-06-14
Hello,

I have an MP3 player that does not show up if I hotplug it in (plug it in after Ubuntu boots).  It worked in Ubuntu 9.10 just fine, but the upgrade killed it.

The only way for me to access it is to have it plugged in before I boot up.  Also, even if I plug it in before I boot, once I open rhythm box, it automatically unmounts it.

Please help!  I don't have any of these problems with my ipod.

---

### Post by diablo75 on 2010-06-14
Does this MP3 player have any internal settings you can adjust for the mode its USB interface is in?  In my experience it's best to put the device in to "MSC" mode and not "MTP" mode.

Previous thread I started about a Sansa player:  [http://georgia.ubuntuforums.org/showthread.php?p=9298866](http://georgia.ubuntuforums.org/showthread.php?p=9298866)

---

### Post by playing_with_matches on 2010-06-14
unfortunately, no this is not an option. Also I need to make a correction: It shows up as an MP3 player in Ubuntu, NOT a thumb device.  When I type in lsusb , it shows the device.

---

### Post by Shazzam6999 on 2010-06-14
Edit: Err, apparently GDM makes this unnecessary in Ubuntu.

I'm not sure if this will fix the issue, but I had a similar issue with an mp3 player and running ```
ck-launch-session
``` in a terminal mounts it without any hassle. 

Err, apparently GDM makes this unnecessary in Ubuntu.

---


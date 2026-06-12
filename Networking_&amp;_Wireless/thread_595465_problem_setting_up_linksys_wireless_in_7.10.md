---
title: "problem setting up linksys wireless in 7.10"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Jake.P on 2007-10-28
First of all, I did get the wireless card to work using this driver for 7.04 so the driver should be OK. But I'm having problem in getting the wireless card to work in 7.10. Even the LED on the card isn't lit. This is what I've tried:

1) installed ndiswrapper of course. on command line, if I do "ndiswrapper -l" I got: 
wmp54gs : diver installed
             device (14E4:4318) present (alternate driver: bcm43xx)

2) "sudo gedit /etc/modprobe.d/blacklist" and added "blacklist bcm43xx" to the file

3) reboot. the LED on the wireless card is still off. so I tried "rmmod bcm43xx" and I got: "ERROR: Module bcm43xx does not exist in /proc/modules"

now i don't understand: if bcm43xx doesn't exist, why is it loaded??

Can any guru out there give me some tips in how to get this working? Thanks a lot!

---

### Post by Jake.P on 2007-10-29
anyone? Any idea on how to get the wireless card working?

---

### Post by Jake.P on 2007-10-29
up up. nobody? Someone please help

---

### Post by Jake.P on 2007-10-29
up again. still waiting for some suggestions. thanks!

---

### Post by invanitas on 2007-11-02
I'm having the same problem. No led light, ndiswrapper says things are fine.

---

### Post by kylirh on 2007-11-08
I'm also having the same problem. I've followed all of the steps that you guys have talked about, along with everything mentioned here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

...and here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

I'm getting that message that the "alternate driver: bcm43xx" is loaded and it seems to be stopping everything. I'm using 7.10 as well.

This wireless card has to work. ndiswrapper has it listed as working in their list of supported cards. Anyone know how to fix this?

Thanks.

Kylir Horton

---

### Post by Law506 on 2007-11-08
I got a linksys wireless card and when I first installed 7.10 it gave me some restricted drivers to use.

It said I couldn't use the broadcom one because I didn't have bcm43xx-fwcutter module installed.  I searched for it on synaptec package manager, after enabling other sites to be used for repositories and found it.  Installed it and then installed the restricted driver and it worked.

I tried using the ndiswrapper but couldn't get it to play.  The way I just described worked out  great.  

Good luck, hopes this helps.

-Law506

---

### Post by JustLikeJsh on 2007-11-24
try my thread, it worked for me and should work for you, let me know.

[http://ubuntuforums.org/showthread.php?t=618759&highlight=wmp54gs](http://ubuntuforums.org/showthread.php?t=618759&highlight=wmp54gs)

---


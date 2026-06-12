---
title: "Wireless card no working on my Dell D620 -  802.11 | Broadcom BCM4311"
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by pipa2 on 2016-03-11
Hi There,

My Wireless card(Broadcom BCM4311) isn't working on my laptop with Ubuntu 14.04 version. Is there anyway that I can make it  work properly in my laptop. If it is possible, how I can install this and commands to run?


Thanks for your help.

Pipa

---

### Post by howefield on 2016-03-11
Thread moved to the "*Networking & Wireless*" forum.

Have a read at the stickies [here]("http://ubuntuforums.org/showthread.php?t=2214110") and [here]("http://ubuntuforums.org/showthread.php?t=370108").

---

### Post by Hadaka on 2016-03-11
Your wireless card's PCID is..[14e4:4311]


From a working wired connection.open a terminal ctrl/alt/t then
Please Copy and paste the following commands one at a time
*Ignore any file not found

```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```


*If you are still experiencing difficulties please go here..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by pipa2 on 2016-03-13
Hi Hadaka,

Step 1 & 2 went fine. Issues is (sudo rm  /etc/modprobe.d/blacklist-bcm43.conf) , no such file or directory. Also  check the "modprobe.d" directory and couldn't fine the  (blacklist-bcm43.conf). Can you help me get to step 3,4 &5. 

Thanks, Pipa.

---

### Post by Hadaka on 2016-03-13
Hi pipa2 , its ok if you get those errors, thats why i said ignore
any file not found error, continue on and copy and paste the rest of the 
commands, its ok if you get an error or file not found. Not to worry that
is normal with those commands.You will probably get an error on #3.
4 and 5 should be fine.
keep me posted

---


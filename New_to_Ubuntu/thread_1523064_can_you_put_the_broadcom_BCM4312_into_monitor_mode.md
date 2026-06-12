---
title: "can you put the broadcom BCM4312 into monitor mode?"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-07-03
i've used an atheros chipset in monitor mode however i am now using the broadcom bcm4312 which came with my emachine laptop.  I've been trying to figure this out and I keep reading different stories.  My current kernel is: 
2.6.31-22-generic.  From what I have read this matters so I figured I'd put that in here to help solve this problem i'm having.  Thanks in advance.

---

### Post by okplayer02 on 2010-07-03
i guess it depends on the firmware for your chipset so i cant say for sure but i know if you are using ndiswrapper it will not work for sure but i did find a link in the forum 

[http://ubuntuforums.org/showthread.php?p=6120811](http://ubuntuforums.org/showthread.php?p=6120811)

now this one is a bit old so you have to take the results with a grain of salt. im assuming you are running Lucid. take a look though.

---

### Post by bradmayne04 on 2010-07-05
> **okplayer02 said:**
> i guess it depends on the firmware for your chipset so i cant say for sure but i know if you are using ndiswrapper it will not work for sure but i did find a link in the forum 

[http://ubuntuforums.org/showthread.php?p=6120811](http://ubuntuforums.org/showthread.php?p=6120811)

now this one is a bit old so you have to take the results with a grain of salt. im assuming you are running Lucid. take a look though.

Hey I am NOT using ndiswrapper.  I am using the broadcom Wireless STA driver.  Sorry forgot to mention that upfront!!!!!!

---

### Post by bkratz on 2010-07-05
> **bradmayne04 said:**
> Hey I am NOT using ndiswrapper.  I am using the broadcom Wireless STA driver.  Sorry forgot to mention that upfront!!!!!!

Afraid the sta driver will not work for  monitor mode, only the b43.

---

### Post by bradmayne04 on 2010-07-16
ok thanks

---


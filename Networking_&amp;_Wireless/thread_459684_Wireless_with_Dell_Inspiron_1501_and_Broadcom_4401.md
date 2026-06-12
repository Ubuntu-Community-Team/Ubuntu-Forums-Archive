---
title: "Wireless with Dell Inspiron 1501 and Broadcom 4401"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Tdraket on 2007-05-30
I just bought a Inspiron 1501 from dell.  I knew I would have some trouble with the wireless.  It seems I got the newest broadcom card(BCM4401) because no one else has a way to fix mine, just the 43XX versions.  I'd appreciate if anyone could help me with this.

---

### Post by spd106 on 2007-06-01
No, the 44xx series are for the wired Ethernet card controllers. 
Check the Device Manager or run lspci at a terminal to see the devices present.

It's far more likely that you will have a 43xx series, even the newer 11n series cards follow that moniker AFAIK.

---

### Post by tekdata on 2007-06-01
I bought the same a month ago. You have a 4311 with the cheaper wifi card, and some other type of 43xx if you got the upgrade. I'm having a horrid time getting mine to work right, though.

---

### Post by bmartin on 2007-06-01
There are two ways to get the Broadcom 4311 chipset to work:

1. If you have kernel 2.6.20.6 or later, you can use [the firmware method]("http://ubuntuforums.org/showthread.php?t=405990"). Most of the people who have tried this have had a lot of success. I've been keeping in touch with the guy who maintains those instructions. It's as easy as running a single script.

2. If you have an older kernel or the above method doesn't work, you can try [the ndiswrapper method]("http://ubuntuforums.org/showthread.php?t=457371"). I've written two scripts: one of them downloads and extracts the drivers, and the other one compiles/installs ndiswrapper and sets up your chipset to work with it.

If you have a problem with either of those methods, PM me or post to one of those threads. You should run the scripts from a terminal, but in the first case, if you have Ubuntu (not Kubuntu), you can run the installer by double-clicking on the script. The reason it won't work on Kubuntu is because it uses **gksudo**. I'm going to contact the author about that problem and fix that script.

---

### Post by razorboy on 2007-06-01
So im not a complete moron................

---

### Post by Tdraket on 2007-06-03
Thanks for the help guys.  I got it working using ndiswrapper!  :D

---

### Post by redDEADresolve on 2007-06-03
welcome to the world of owning a dell 1501

check out my blog, its all about the dell 1501

[www.ubuntu1501.blogspot.com](www.ubuntu1501.blogspot.com)

---


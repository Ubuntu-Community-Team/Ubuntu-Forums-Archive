---
title: "Wireless USB"
date: 2005-05-15
forum: Networking &amp; Wireless
---

### Post by iakudi on 2005-05-15
Hi all,

I have an IBM Thinkpad 600X and I want to install Ubuntu on it, however when I tried last time (Warty) it would not recognise my USB wireless connection.

Can anyone please help (step by step idiots guide please) me? Can I get USB wireless to work?

Also, if I do manage this and then buy a mini USB hub to use more than 1 USB device will my wireless still work?

many many thanks in advance

Ismail

---

### Post by jacobo on 2005-05-15
i have installed hoary and successfully set up a wireless usb device. the one we used (ma111) required that we used a windows .inf but it wasn't that tricky, ubuntu has utilities such as ndiswrapper (sudo apt-get install ndiswrapper-utils) to create a device module that works in linux. it should work, threads [here](http://ubuntuforums.org/showthread.php?t=15425) and [here](http://ubuntuforums.org/showthread.php?t=22995) have more details...

---


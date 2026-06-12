---
title: "Dell inspiron 1501  wireless internet"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by rajausman on 2007-05-15
Hi,

Does someone have any idea as how to enable the wireless internet connection on the above named laptop.

I am currently using **ubuntu 7.04**,  the laptop is equipped with a :

Network controller: Broadcom Corporation Dell Wireless 1390 Wlan Mini-pci card (rev 01).

Any suggestions are welcome.

---

### Post by bmartin on 2007-05-15
Try [these instructions]("http://ubuntuforums.org/showthread.php?t=297092").

---

### Post by rajausman on 2007-05-17
Thanks for your reply....I 
 have successfully followed all the steps in your guide, except that when i try

sudo ndiswrapper -l

i get the message, invalid driver, what would be the correct driver for this model of the laptop.

I could provide any additional information on this matter.
Any suggestions are welcome.

---

### Post by bmartin on 2007-05-17
I've looked into this matter a bit, and it appears that the chipset you have belongs to the Broadcom 43xx family. It's simply been rebranded. So [here are some instructions]("http://ubuntuforums.org/showthread.php?t=405990"); they're much simpler and they don't use NDISWRAPPER.

These instructions have worked for about 5/6 of the people using the method with Broadcom drivers. The basic steps are:

1. Remove NDISWRAPPER
2. Install the firmware
3. Run depmod and modprobe to insert the necessary kernel module

If you can live with a 11Mbps connection, I **highly** recommend this method, as I have one of these chipsets and this is the ***only*** way I could get this chipset to work.

---


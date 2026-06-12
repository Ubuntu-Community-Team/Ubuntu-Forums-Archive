---
title: "Driver looks OK, device disabled"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by twuerz on 2007-06-15
Hi, am new to linux and ubuntu - 7.04 i386 install was just yesterday!!

Unfortunately, having trouble with my wireless connectivity.  I have an Inspiron 6400 laptop with a Dell Wireless 1390 WLAN Mini-PCI Card.  When I run  sudo lshw  in terminal, the driver is recognized, but it says

*-network DISABLED

Any suggestions?

---

### Post by tturrisi on 2007-06-15
Driver looks OK, device disabled.

The reverse.  Device is OK, there's no driver loaded for it.  The device has a broadcom chipset.  Do a forum search for broadcom dell.

---

### Post by kevdog on 2007-06-15
Ok you have a built in wireless card for your dell. How did you try to install drivers for the card?

What is the output of:

lspci | grep Network

Example from my system:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Next I want you to take the leading number (06:00.0 in my case) and use this information to post the line from the following command

lspci -n

Example in my case:
06:00.0 0280: 14e4:4320 (rev 03)

---

### Post by twuerz on 2007-06-16
OK, so here is what I got from the following inputs:

lspci | grep Network

0b:00.0 Network Controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

lspci -n

0b:00.0 0280: 14e4:4311 (rev 01)

So, you'll have to forgive me for having no idea what that means.

I did previously download the driver Broadcom440x308b, which was recognized by Ubuntu as a program, but which did not seem to do anything when ran.  Furthermore, I tried to Add ndiswrapper from the Applications, but this would not download more than halfway either.  Again, I sheepishly admit my utter ignorance as to what might be going on in Ubuntu world that has made these things not work for me... :confused:

---


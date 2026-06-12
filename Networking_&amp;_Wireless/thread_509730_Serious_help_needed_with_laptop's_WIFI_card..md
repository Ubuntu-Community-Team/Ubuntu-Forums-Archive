---
title: "Serious help needed with laptop's WIFI card."
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by EvenStevens on 2007-07-25
Okay, so after hours of searching I figured that the wifi card in the laptop was "blacklisted".
It's a RealTek 8185L card. So I removed it from the blacklist, rebooted and the network manager activated wifi and found the network SSID.
However, when I press connect, it doesn't. 
Looking through hardware information, I found it was using the 8180 drivers rather than the 8185 drivers O_o
Possibly a cause of the problem?

I have the drivers for 8185 but have no idea how to replace them.

HALP!!

Using Ubuntu 7.04 Feisty, by the way.

---

### Post by gangolli on 2007-07-25
Which drivers do you have?  The following assumes you don't have a new fixed release of the r818x linux drivers (not sure if there is one).

If you removed one of these blacklist items from /etc/modprobe.d/blacklist,

> 
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187


I would **put it back **(leave it blacklisted), and try the rtl8185 windows driver with ndiswrapper instead.  I have used it successfully on one laptop with the Realtek 8185L chipset on a PCMCIA device.

---

### Post by EvenStevens on 2007-07-26
I'm using a bunch of drivers I had on the laptop CD.
When trying to install the r8185 drivers, ndiswrapper says that they're "Already installed".
Doesn't seem to make a world of difference :|

Where are these "fixed" drivers?

---

### Post by gangolli on 2007-07-26
Sorry if I was unclear.  What I am suggesting is that you keep the blacklist entries for the linux drivers since these blacklist entries were in the original Ubuntu distribution.  They trigger the bugs indicated in the comments. 

Instead of the linux drivers use the _Windows_ rtl8185 driver with ndiswrapper.  I can confirm that I have used the rtl8185 Windows driver with ndiswrapper and it works.

The Windows driver is usually distributed on CD with your device or can typically be downloaded from the device manufacturer's site.

Here are instructions on how to use ndiswrapper with Windows drivers.  Follow the instructions for your Ubuntu distribution.  In 7.04 it is very easy.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by gangolli on 2007-07-26
I guess I may not have read your post carefully enough, or didn't understand it.  Do you already have ndiswrapper and the rtl8185 windows driver installed? 

Can you run some of these diagnostic commands in a shell terminal window and post the output?

```

lsmod | grep ndis

lsmod | grep r8

sudo lshw -C network

ndiswrapper -l

iwconfig

ifconfig -a

```

---


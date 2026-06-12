---
title: "ndiswrapper with broadcom 4311"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by illusion on 2006-12-28
Hey,

Following the instructions here
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-77f1ef210976e4aed570c057e7ae72d2c6a09a91](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-77f1ef210976e4aed570c057e7ae72d2c6a09a91)

I have trying to get an hp pavilion 6110I with a broadcom 4311 card.  I have downloaded the appropriate driver inf file and sys file.  The driver installs and is detected.  

The following message is displayed to verify installation

ubuntu@laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 

But after the installation, and rebooting, the card does not read in the network gui, and does not show up with iwconfig

when loading the module, i get the following error

ubuntu@laptop:~$ sudo depmod -a
Password:
ubuntu@laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Not sure why it doesnt read, any help would be greatly appreciated,
Illusion

---

### Post by FrodoB on 2006-12-28
See:
 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by haiku99 on 2006-12-30
I got my 4311 working in Dapper and Edgy (on an HP nx6310 FWIW) w/ this simple howto...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
I copied drivers from my windows partition....

---

### Post by LavianoTS386 on 2007-12-30
I created a how-to for the Compaq F500 series, which has the 4311 in it too. Maybe it will help you.

[LINK]("http://compaqlinux.blogspot.com/2007/12/make-wireless-work-w-ndiswrapper.html")

---


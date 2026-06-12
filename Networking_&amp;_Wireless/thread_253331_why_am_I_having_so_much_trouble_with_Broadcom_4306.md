---
title: "why am I having so much trouble with Broadcom 4306 wifi??"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by bobbymcsteels on 2006-09-08
Ok as far as i know i have followed the how to [here]("http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+wifi") and still I am having trouble with setting up my wifi card.... Is there something I have missed or is not in the how to?

When I ```
lspci | grep Broadcom\ Corporation
``` it shows 

```
0000:01:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

But still I have tried everything I can think of but still doesnt work, Any suggestions?
Thanx

---

### Post by hw-tph on 2006-09-08
I have the same chip as you, even the same revision. I have no problems using the bcm43xx driver.

Dapper comes configured to use the free bcm43xx driver for Broadcom chips. I don't see why people insist on using ndiswrapper to use a nonfree Windows driver. OK, so there is one reason - the bcm43xx module does not support 54mbps transfers at the moment.

Remove ndiswrapper and blacklist the module if needed. Then simply use bcm43xx-fwcutter to extract the firmware from the Windows driver (or any other supported driver) and place it in the firmware directory for your kernel revision.

So, the output of **uname -r** is "2.6.17-ck1" on my laptop. I copy the firmware files to /lib/firmware/2.6.17-ck1/, load the bcm43xx module and that is it.

If you're having problems with cutting the firmware or obtaining it elsewhere, you can get it [here](http://hakan.prinsig.se/files/ubuntu/bcm43xx-firmware.tar.bz2). These are the firmware files I use. Just put them in /lib/firmware/$(uname -r) and reload the bcm43xx driver.


Håkan

*Edit*: SpeLing

---

### Post by bobbymcsteels on 2006-09-08
wow that was easy........ I thought that ndiswrapper was the only way to go with broadcom. Thanx for that, saved me going throught every single distro I have used in the past to try and see if it works:P

---

### Post by hw-tph on 2006-09-09
Yes, it really is easy. I have for a long time had a spare partition on my laptop with a more "techy" Linux distribution (Gentoo or Arch most of the time) to experiment with the bcm43xx driver. It has been way too much patching and rebuilding until Dapper. bcm43xx is also included in the vanilla kernel from 2.6.17-rc1 onwards, so now it is a breeze on all distributions.

One note though: By default, the bcm43xx driver will allocate a device name for the controller using the standard "eth?" way, so if you have one wired Ethernet controller installed, that controller will (most likely) be called eth0 and the bcm43xx-powered Broadcom chip will be known as eth1. This differs from when using ndiswrapper - ndiswrapper defaults to using wlan0. I have seen people screaming (typing?) their hearts out in IRC channels complaining that it doesn't work only because they didn't find a wlan0 device...when it was already running as eth1. :)


Håkan

---

### Post by bobbymcsteels on 2006-09-09
Like I said in one of my last post I thought that ndiswrapper was the "ONLY" way to install broadcom chips(dont know why, mite have read it somewhere), and with loads of how to install using ndiswrappers with loads of ppl sayin that the how to doesnt work, and I have tried to install it bout 10 times over the last couple of months and not been able to do it, then you go and show me a way to install my card that took litteraly 2 mins to do and worked 1st time, and I have got to say that its working better than in my windows partition, sayin that tho what doesnt work better in linux than windows:P

---

### Post by jandi on 2006-09-09
I've been struggling with a Broadcom 4306 card all day and can't still get it to work.  It was previously working using ndiswrapper under Breezy, but the upgrade to Dapper messed it up completely.  I don't have another way to access internet from that computer other than wireless, so I can't follow the how to here
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I tried your instructions here, unloading ndiswrapper and copying the firmware files through an usb drives, and then loading bcm43xx, but although the card appears as eth1, and I'm able to configure it with iwconfig, if I trie to shut down or up the interface with ifup/down I get
ifdown: interface eth1 not configured
ifup: ignoring unknown interface eth1=eth1
dhclient fails too

I also am unable to start the system-networking gui utility.  Users isn't working either.  I'm totally confused.

---


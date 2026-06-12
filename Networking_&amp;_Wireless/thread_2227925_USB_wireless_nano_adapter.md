---
title: "USB wireless nano adapter"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2014-06-04
Evening, one and all.

I'm an absolute newbie who has just moved over to Ubuntu during the last few days.

(New to Ubuntu, that is; for my sins, I've been faffing about with computers in general since the days of the Ark , but I digress...)

I'll say here and now that the changeover went VERY smoothly; installed from a USB thumb drive, and touch wood, so far I'm enjoying it.

Now then; to get to my question.

I have two computers; an elderly Compaq Presario PC, and an even older Dell Inspiron laptop. I generally run an Ethernet connection on the Presario; the Dell (for reasons I won't go into, won't work with the wireless adapter I have; a TP-Link WN725N nano USB dongle), so...RJ45 it is.

On the occasions when I'm using the Dell on the 'net, I use the dongle on the Presario to maintain a connection. I haven't yet needed to use the dongle, but having browsed the newbies forum, I've seen there's quite a number of people with this problem of wireless network connections.

What do I need to do, in order to make sure the dongle will work when I want it to?

I've had a look at the wireless cards wiki, but of course, this is a list of CARDS (not adapters). A TP-Link WN722N is mentioned, but mine's a 725N.....and it's a USB dongle, anyway.

I'm running Ubuntu 14.04 LTS, Trusty Tahr.

Any advice would be much appreciated. I'm not above GIVING advice when it's within my power to do so (I spent years doing just that on the Microsoft forums; sorry for the 'swearword'!!), but I fancy it'll be a little while before I can do so on here...

Mike Walsh.

---

### Post by kurt18947 on 2014-06-04
If this is correct, 

[https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1)

your device uses an RTL-8192CUs chipset.  I have a similar device, Edimax EW7811Un running on 14.04 Gnome.  It works when plugged in but not reliably in my experience.  When it stops, disabling then re-enabling wireless convinces it to work for a few minutes more.  To make it work well, I use this fix:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

This is the driver from RealTek tweaked to work with the 3.11 kernel.  As good fortune and good programming talent have it, it seems to work well with 14.04's 3.13.x kernel as well.

---

### Post by Mike_Walsh on 2014-06-05
Hallo, Kurt.

Sorry to be a little while getting back to you, and thanks for replying. I've had a look at the link, and yes, that is indeed the adapter in question. I appear to have version 2 (v2); does that make a difference?

That's interesting, 'cos the Presario's got a Realtek Ethernet card, too...:)

Anyway, do I take it that that particular driver will help the little beastie to function as it should? Having looked at the github page, do I understand that this is still in an intermediate, yet usable stage? Being new to Linux in general, I'm still getting my head round the concept of people happily acting as guinea pigs for other people's work... I don't know HOW those folk at *Mi.....ft* do things, but I'm sure they must very carefully vet people before they'll let them anywhere NEAR beta stage code'n'stuff..!!

Mike Walsh.

---

### Post by kurt18947 on 2014-06-06
> Sorry to be a little while getting back to you, and thanks for replying.  I've had a look at the link, and yes, that is indeed the adapter in  question. I appear to have version 2 (v2); does that make a difference?

It may.  If you're fortunate, the chipset has changed from 8188CUs to 8192CU.  I say fortunate because my 8192CU device seems to perform better than the 8188CUs device.  You should be able to tell which chipset is in use by opening a terminal and typing this command:

```

lsusb

```

You should see something like this:

:~$ lsusb
**Bus 002 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 17ef:1003 Lenovo Integrated Smart Card Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It seems to me like most 'nano' wifi devices use either RealTek's 8188CUs or Ralink/Mediatek's 5370 chip.  There may be newer generation chipsets but those two seem pretty common of late.

---

### Post by Mike_Walsh on 2014-06-06
Hi, Kurt.

Well, I've used the terminal, and what I get in response to 'lsusb' is the following:-

paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ lsusb
Bus 001 Device 007: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bc2:2312 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 

As you can no doubt see, I'm missing the necessary bit of info at the end. Could this be because it's not yet been configured? Like I said, I only use this occasionally, when the Dell laptop needs to use the Ethernet connection, but I guess it'll need setting up sooner or later...

Mike.

ps In case you're wondering, Paul's my second name...it's the one the family uses; I've always preferred my first name..!!

---

### Post by Mike_Walsh on 2014-06-06
Hallo, Kurt.

Well, I guess I'd better mark this one as 'solved', since I've simply gone into 'connections', and requested the wireless link to connect; put the security info in, and.....touch wood, it's up and running.

I'm still not getting the chipset info on the terminal, though; wonder why that is?

Anyway, thanks for your replies, and your help; both much appreciated. Cheers!

Mike.

---

### Post by gordintoronto on 2014-06-06
If you Google: USB 0bda:8179 
you can eventually get as much information as you want.

Glad to hear that it's working!

---


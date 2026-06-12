---
title: "Trendnet 424-UB ver 2, and Ubuntu 8.10"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by superfly1234567890 on 2008-11-07
Hey all, 
Hope everyone is doin' good. So I decided to format my Windows OS last week and placed 8.10 on my tower. So far so good. I have been a Ubuntu User since Dapper Drake and I'm loving it!

Anyways enough of that, it seems that there have been MANY different threads pertaining the use of the Trendnet 424UB Wirless USB Adapter (version 2), however after reading most of them and trying to put two and two together from configurations of older versions into 8.10 I seem to be getting some trouble. Pretty much I am not getting no progress at all when setting up this Wifi Adapter.

This has been a two going on three day research trying to find info on how to successfully install the drivers onto 8.10 however it seems to be somewhat of a challenge to find someone out there who is successful in setting this up. and I'm wondering if someone has experimented with the Trendnet 424UB wireless (version 2).

I did try to use ndiswrapper and install the drivers but when I did I tried to connect the USB adapter in and it crashed my system nine times out of ten. I ended up reinstalling Ubuntu just to get rid of alot of the irrelevant configurations which screwed up my system. I did get it going but at the same time it wouldn't connect to my network. 

I've tried many methods including trying to follow some of the tutorials from older Ubuntu Versions to see if it would work on 8.10. Right now I'm not giving up the fight and with that said I want to know if anyone was able to get their Wireless USB Adapter going? 

Here is the following information I can provide so that someone, or anyone out there who has been in the same situation as myself and now has their Wifi USB adapter running on 8.10 can help me.

**lsusb** *(please keep in mind I have the adapter connected at this point.)*
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**lspci | grep Ethernet**
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I really hope someone can give me a hand out there, and hopefully provide a simple tutorial so that not only myself can benefit from this but many others out there who are in my Shoes... Can someone please advise me on what should I do? 

Much appreciated,

- Superfly1234567890

---

### Post by ultimatePHIL on 2008-11-09
Hi,

although it wouldn't help you this much I want to report my problems with the trendnet 424 stick and ndiswrapper.

I succeded in getting this thing run in old ubunut versions (7).
But when I upgraded to 8.04 I had the same problems like you.

I tried diffrent things but when I plugged in the stick the system chrashed.
So I gave up and waited for a new ubuntu version. In the hope that it would work with this (remember it has been working before with older versions, crazy isn't it?), but now I'm afraid it wouldn't (after reading this).

Well, I just wan't to say I got the same problems. And you are not alone ;-)

Cheers

P.S. Please excuse me for failures in writing my native language is german..

---


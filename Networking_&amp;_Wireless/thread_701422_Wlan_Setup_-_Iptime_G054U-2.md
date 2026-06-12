---
title: "Wlan Setup - Iptime G054U-2"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by hhumala on 2008-02-19
Here goes..

I bought Iptime wireless router (G104) and USB receiver (G054U-2) and I want to use the USB receiver in my laptop. Manufacturer is Korean co and promises Linux support. 

I'm using Ubuntu 2.6.17-11-generic.

I found following posts but couldn't get it working:
[http://ubuntuforums.org/showthread.php?t=419709](http://ubuntuforums.org/showthread.php?t=419709)
[http://www.iptime.co.kr/zeroboard/iptime_bbs/view.php?id=general_review&page=10&sn1=&divpage=1&category=1&sn=off&ss=on&sc=on&select_arrange=headnum&desc=asc&no=1876](http://www.iptime.co.kr/zeroboard/iptime_bbs/view.php?id=general_review&page=10&sn1=&divpage=1&category=1&sn=off&ss=on&sc=on&select_arrange=headnum&desc=asc&no=1876)


.....
iwconfig prints following:
lo    no wireless extensions

master0   IEEE 802.11g Frequency: 2.412GHz
                RTS thr: off   Fragment thr=2346 B

wlan0      IEEE 802.11g  ESSID: " "
               Mode: Managed Frequency: 2.412 GHz Access Pont: Not-Associated
               RTS thr: off Fragment thr=2346 B
               Encryption key: off

....

My /etc/network/interfaces looks like this 

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid XXXX
pre-up iwpriv ra0 set WPAPSK="XXXX"

auto eth0
iface eth0 inet dhcp

.....

lshw -C network prints:

-usb
       description: Wireless interface
       product: 802.11 bg WLAN
       vendor: Ralink
       physical id: 1
       bus info: usb@1:1
       logical name: wmaster0
      version 0.01
      serial: 00:08:9f:fd:8c:e3
      capabilities: usb-2.00 logical wireless
     configuration: broadcast=yes driver=rt73usb driverversion=cvs firmware=rt73usb->%s: Error - vendor requ1-1:1.0 link=yes maxpower=300mA multicast=yes speed=12.0MB/s wireless=IEEE 802.11g

-network               
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:08:9f:fd:8c:e3
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g

....

I dont have anyother network connection on my laptop.

I have no idea where to go next... please help.

I'm no-expert with linux. I just want to get my wlan working..

h

---

### Post by hhumala on 2008-02-22
No help available?

I think there might be something wrong with the driver b-cause the one minor error message it gives. How can I make sure the driver works?

---

### Post by hhumala on 2008-02-26
Seriously... Not even one reply!?

I guess I'll switch back to windows... lol

---

### Post by hhumala on 2008-03-10
Just received it today..

[Any opinions about this]("http://www.windowsmarketplace.com/content.aspx?ctId=417&WT.mc_id_1107_184")

thanks

---


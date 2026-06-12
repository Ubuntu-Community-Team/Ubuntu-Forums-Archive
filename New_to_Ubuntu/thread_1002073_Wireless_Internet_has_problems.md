---
title: "Wireless Internet has problems"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by alon_lhv on 2008-12-04
Hello,

I am new in the Linux world. I have purchased this very old laptop: IBM Thinkpad T20 700MHz with 256MB RAM and 20 GB HD. It runs very sllow, however, this is not my biggest problem: the wireless Internet doesn't work well.

I have a NETGEAR WG111v2, connected to the USB. When I start the computer, it detects the wireless network and works good for couple of minutes, but after that it fails to connect to the Internet - it report "wireless network connection to'LahavNt' (0%)" when I put my cursor on the wireless icon. The USB is OK, because I see all the available networks. But it cannot reconnect to the Internet, until I restart the computer.

Also, sometimes even when the little icon reports 89% reception, it fails to communicate with the Internet.

It works good with my other new laptop with windows Vista, so I assume the problem is not there.

So, was it a wrong desission to buy this old computer? :(

---

### Post by garwaymatt on 2008-12-04
Do you have another adaptor to try, I have found that some USB ones can be tempremental under Ubuntu. What version of Ubuntu do you have installed?

---

### Post by Michael.Godawski on 2008-12-04
Can you please post the result of these terminal commands:
```

sudo lshw -C network
iwconfig
```

---

### Post by alon_lhv on 2008-12-04
My Ubuntu version is 8.04. And I do not have another WiFi adaptor. Do you think I shoud try it on a computer store?

---

### Post by alon_lhv on 2008-12-04
Here it is:

for the sudo lshw -C network:
-----------------------------
*-network
   description: Wireless interface
   physical id:1
   lagical name: wlan0
   serial: 00:0f:b5:b5:af:3b
   capabilities: ethernet physical wirless
   configuration: broadcast=yes ip=192.168.10.102 multicast=yes wireless=IEEE 802.llg

for the iwconfig, the results are:
----------------------------------
lo             no wireless extentions.
irda0          no wireless extentions.
wmaster0       no wireless extentions.
wlan0          IEEE 802.llg ESSID:"LahavNet"
               mode:Managed Frequency:2.412GHz Access Point: 00:14:d1:5:bf:ee
               Bit Rate=1 MB/s    Tx-Power=27 dBm
               Retry min limit:7 RTS thr:off  Fragmented thr=2346 B
               Link Qaulity=57/64 Signal Level=46/65
               Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
               Tx excessive retris:0 Invalid misc:0 Missed beacon:0

I hope it make seens to you. To me it doesn't...

---

### Post by Michael.Godawski on 2008-12-04
> for the iwconfig, the results are:
----------------------------------
lo             no wireless extentions.
irda0          no wireless extentions.
wmaster0       no wireless extentions.
wlan0          IEEE 802.llg ESSID:"LahavNet"
               mode:Managed Frequency:2.412GHz Access Point: 00:14:d1:5:bf:ee
               **Bit Rate=1 MB/s**    Tx-Power=27 dBm
               Retry min limit:7 RTS thr:eek:ff  Fragmented thr=2346 B
               Link Qaulity=57/64 Signal Level=46/65
               Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
               Tx excessive retris:0 Invalid misc:0 Missed beacon:0

very slow bit rate.
Try

```
sudo iwconfig wlan rate 11M
```

---

### Post by alon_lhv on 2008-12-04
Thanks for the quick replay...

It tells me:
Error for wireless request "Set Bit Rate" (8b20) :
  SET faild on device wlan ; No such device.

What now?

---

### Post by Michael.Godawski on 2008-12-04
> **alon_lhv said:**
> Thanks for the quick replay...

It tells me:
Error for wireless request "Set Bit Rate" (8b20) :
  SET faild on device wlan ; No such device.

What now?

sry it is getting late and my tired eyes...

```
sudo iwconfig wlan0 rate 11M
```

---

### Post by alon_lhv on 2008-12-04
Now it looks like Ubuntu liked it more.. But nothing realy happened.
I wrote this line, and no answer from the system. But when I tried [www.google.com](www.google.com), it kept telling me that it cannot find the server.

---

### Post by alon_lhv on 2008-12-12
Hi,

I solved this problem by installing Ubuntu 8.10. :)

---


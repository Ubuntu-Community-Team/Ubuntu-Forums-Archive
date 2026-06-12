---
title: "BCM4310 Rev 1 troubles (HP TX2500)"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by corwinspyre on 2008-07-03
Hi!  I'm having a bit of trouble getting wireless working in Hardy. I have an HP Pavilion TX2500z.

I've run through these guides using the driver for my BCM4310 rev01 without luck:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers)
[http://georgia.ubuntuforums.org/showthread.php?t=766560](http://georgia.ubuntuforums.org/showthread.php?t=766560)

First, here is some information
lspci
```
08:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```
lshw -C network
```
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:00:33:2f:ec
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

You'll notice it's loaded with ndiswrapper--I'll get to that.  First, before I did anything, it found it via the restricted drivers using driver wl, but it wouldn't put it in use.  Here's a screenshot of what I'm talking about: 
[IMG]http://i25.tinypic.com/33yjd5v.png[/IMG]

So, I decided to try to get ndiswrapper working.  I can get through everything, and it seems ok until ndiswrapper -l.  Instead of
```
Installed ndis drivers:
{name of driver}  driver present, hardware present
```
I get
```
bcmwl5 : driver installed
	device (14E4:4315) present (alternate driver: wl)
```
Notice the "alternate driver: wl".  Using sudo modprobe -r wl didn't help any.

I finished the install steps, and I believe it loads ndiswrapper correctly, so I think it's because it's still using the wl driver.  I believe it's working because this is the output of /var/log/messages after I finished installing it:
```
Jul  3 18:14:28 dell-d620 kernel: [    0.000000] lo: Disabled Privacy Extensions
Jul  3 18:14:31 dell-d620 kernel: [    0.000000] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] ndiswrapper: using IRQ 7
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] wlan0: ethernet device 00:21:00:33:2f:ec using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4315.5.conf
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] usbcore: registered new interface driver ndiswrapper
Jul  3 18:20:11 dell-d620 kernel: [    0.000000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

I've added these to /etc/modprobe.d/blacklist but it didn't make it work:
```
blacklist bcm43xx
blacklist wl
blacklist b43
blacklist b43legacy
blacklist b43 ssb
blacklist b43ssb
blacklist ssb

```

Installing ndiswrapper gave me a "Wireless Networks" section in the network-manager icon, but my network doesn't show up.

Help is very appreciated. I've run out of ideas.  Thank you very much.

---

### Post by isachan on 2008-07-05
I tried three different drivers to tackle with this issue, and none of them worked.

I tried the Vista driver from this link first :
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-60592-1&lc=en&cc=us&lang=en&os=2100&ts=true&dlc=en&product=3744020](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-60592-1&lc=en&cc=us&lang=en&os=2100&ts=true&dlc=en&product=3744020)

and it didn't work.

Second, I tried one of the Dell driver from one of your links with the name of "R174291-pruned", and it showed some positive signs, but no joy.
Basically, I got the same result as you got. With KWifiManager, I could see the card's speed was set to 54Mbps. I could set my ESSID, channel and WEP, but my wireless router or any router just don't show up. I used Wicd and some CLI commands to do this. 

One of your link in the Ubuntu forum stated that you don't have to worry about the alternative indication of wl driver, so I didn't. I made sure to check off the enabled in the Hardware Drivers Managers though. If you get "ADDRCONF(NETDEV_UP): wlan0: link is not ready" message when you do dmesg, that means the driver is not working. When I was trying to make my b43 driver with my TX1000 compiled from source code, I was getting the same message for a few weeks until the bug in the driver was finally fixed.

I think it's just the matter of finding a right driver for ndiswrapper, and we haven't nailed it yet. I'm thinking maybe faster to just swap mini-pci wlan card with my TX1000 (which has bcm4311 rev 2). I wish I can order a new one to install by myself.

Isao

---

### Post by corwinspyre on 2008-07-06
Hi! Thanks for the reply.  I've since found this thread [http://ubuntuforums.org/showthread.php?t=848622&page=3](http://ubuntuforums.org/showthread.php?t=848622&page=3) that explains at least part of our problem.  The b43 driver should work out of the box, but a recent update broke the wl driver.  So, hopefully a fix will come soon, and wireless will work for the tx2500.

Ndiswrapper should also work, so that part of our problem isn't fixed but will hopefully soon be irrelevant.

---

### Post by bacalao21 on 2008-07-17
corwinspyre, 
I have the same broadcom, and when I first booted, my 'wl' was listed as 'not in use' also. But I was able to connect to internet through cable and download/install updates. From there I tried different methods of activating the wireless. I gave up and restarted the comp. and the wireless worked but only for unsecured networks. I check to the hardware again and 'wl' was 'in use'. Did something similar happen to you?

---

### Post by thegnark on 2008-07-29
The fixed wl driver is in the proposed repo. If you enable that and update, your wireless should work flawlessly.

---

### Post by rizitis on 2008-08-15
for bcm 4310 follow this [http://ubuntuforums.org/showpost.php?p=5031396&postcount=1](http://ubuntuforums.org/showpost.php?p=5031396&postcount=1)

only driver is different but you  can try to downland this  from here [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

maybe work this one...
  good luck

---


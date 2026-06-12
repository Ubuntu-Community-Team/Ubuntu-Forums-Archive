---
title: "Dell Inspiron 6000 Broadcom 4318 (rev 02) Hardy - no wireless"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by venture68 on 2008-06-01
I've read endless posts on this forum. Tried tons of different things. Disabled security on my home network. I just can't get Ubuntu to connect wirelessly. Unfortunately, this is a deal breaker for me since this laptop is upstairs away from our router.

So, here's my last attempt to get this to work before going back to XP. I can't spend any more time getting this to work. I *WANT* to use it, but I can't if wifi won't work. So I'm now begging for help.  :lolflag:

I've installed a fresh copy (many many many times) of 8.04. It tells me about some proprietary drivers which I download. I reboot. My WiFi light is on. No connectivity to the network though.

Under Network manager wired and wireless are in roaming mode. When I pull down the tray icon I see that I am connected via wired mode. Under that it says Wireless Networks with nothing listed. I see Connect to Other Wireless Network and Create New Wireless Network.

Here's is some info that I see is usually asked for on the forums:

lshw -C network

> 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ee:58:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.153 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:4f:5b:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


lspci | grep Broadcom

> 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


lspci -n | grep '14e4:43'
> 03:03.0 0280: 14e4:4318 (rev 02)

lsb_release -d
> Description:	Ubuntu 8.04


Anyway, if you need to know anything else, I am new to Linux and Ubuntu (so far I love it except for this issue) so just tell me what to do to help diagnose the problem.

Thank you so much in advance.

---

### Post by dustigroove on 2008-06-01
Have you tried using ndiswrapper and the Windows driver?
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D_(Native_Driver)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D_%28Native_Driver%29")

Cheers,

---

### Post by dustigroove on 2008-06-01
Some more info on the native driver method... appears that the firmware needs to be copied over?

[http://www.debiantutorials.org/content/view/153/213/](http://www.debiantutorials.org/content/view/153/213/)

Cheers,

---

### Post by venture68 on 2008-06-01
I tried the steps and when I issue the 

cp /boot/config .config

command I get

cp: cannot stat `/boot/config': No such file or directory

*sigh*

---

### Post by venture68 on 2008-06-01
Can anyone tell me how to open up Nautilus in admin mode? I need to write to a directory in the usr area.

Thanks.

---

### Post by dustigroove on 2008-06-01
> **venture68 said:**
> Can anyone tell me how to open up Nautilus in admin mode? I need to write to a directory in the usr area.

Thanks.

```
gksudo nautilus /usr
```

From running a quick 'ls /boot' in a terminal it looks like the config file in /boot is named something like "config-2.6.22-14-generic".

Cheers,

---


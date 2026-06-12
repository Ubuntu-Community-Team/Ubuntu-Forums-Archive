---
title: "Very Slow Wifi connection with Ubuntu 14.10"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by gerryblewis on 2014-11-02
Hello Community!

My wifi connection on Ubuntu is realy slow. I checked google and saw that theres simluar problems with other versions, but i found nothing that helped for the 14.10 version.
Any sugestions what i can do about that?

I changed from Windows to Ubuntu and iam pretty new with this stuff.So be patient with my understanding of this system. 

Thanks!

---

### Post by Bucky Ball on 2014-11-02
*Thread moved to **Networking & Wireless**.*

Welcome. As long as you're happy with a learning curve, all good! 

Please open a terminal (do a search for 'terminal') and paste this in then hit return:

```
sudo lshw -C network
```

Post the output back here between [code] tags (see the last link in my signature).

---

### Post by gerryblewis on 2014-11-02
ok, here we go

```
   *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:53:e6:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:c000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3.3
       logical name: wlan0
       serial: 10:fe:ed:1c:fc:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.16.0-17-generic firmware=N/A ip=192.168.0.13 link=yes multicast=yes wireless=IEEE 802.11bgn

```

Thanks for the quick reply! Iam open to learn more about Linux and its tricky parts.

---

### Post by Bucky Ball on 2014-11-02
Have you installed a wireless driver yourself or did you plug a cable in, do an update and wireless just worked or did wireless just work 'out of the box'?

Could you now post the output of 'lsusb'. A USB dongle, not an internal card I presume.

---

### Post by gerryblewis on 2014-11-02
Iam using an USB Stick. Model is TP-LINK TL-WN823N . Its a cheap one, but it did its work on windows.
It was working directly after installing ubuntu. Slow....but working...

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05b8:3173 Agiler, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 003: ID 1e68:003f TrekStor GmbH & Co. KG 
Bus 006 Device 002: ID 2381:0100  
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by gerryblewis on 2014-11-02
It kicked me out a several times so i did some restart and now it works fine. Speed is ok and its stable (for now?)
Normaly i dont belive in "time will solve problems" but this makes me think.

---

### Post by Bucky Ball on 2014-11-02
Pleae mark your thread as solved by following the second link in my signature and please be mindful of language. We are a family-friendly forum that caters for all ages, nationalities and sensibilities.

I edited your last post. Cheers and good luck. ;)

---

### Post by gerryblewis on 2014-11-03
Ok, Sorry for that! I will mind it in the future. :-) 
But thanks for your time and help on this!
See you around...

---

### Post by Bucky Ball on 2014-11-03
> **gerryblewis said:**
> 
See you around...

You will. ;)

---

### Post by kurt18947 on 2014-11-03
> **gerryblewis said:**
> It kicked me out a several times so i did some restart and now it works fine. Speed is ok and its stable (for now?)
Normaly i dont belive in "time will solve problems" but this makes me think.

I'm having a similar experience with 14.10 and 2 RealTek adapters, RTL8192CU and RTL8192CUs.  It seems stable but not very fast.  I tried to download an .iso from a normally fast mirror and was seeing around 700KB./sec.  This mirror is normally capable of 3 MB./sec. which maxes out my broadband connection.  There is a patch about that enables the use of RealTek's linux driver on newer Ubuntu based installs.  It works with 14.04, I haven't tried it with 14.10 yet.  I want to see if the native driver continues to work albeit at near G speeds. If you have a 14.10 install that if it breaks there are no repercussions, the patch is here:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

The patch is supposed to blacklist the native driver.  I've needed to manually blacklist the native driver in order to prevent it loading.

Edit:  14.10 3 week old fresh install using native rtl8102cu driver & Edimax 7811Un device.  I was showing wifi connected but no internet.  Tried the usual fixes, no luck so rebooted the router.  Now I'm seeing 18 mb./sec download 12 mb./sec upload and it still seems stable.  Not great but better than what I've seen when using the native driver on previous *buntus.

---


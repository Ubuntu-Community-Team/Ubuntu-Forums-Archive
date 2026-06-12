---
title: "BCM4306 rev 02 not working on 8.10"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by XDevHald on 2008-11-02
Install Ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Allows you to run non-native drivers. Hope this helps :)

I don't recommend belkin ;)

---

### Post by Joe2Shoe on 2008-11-03
I followed the wiki on the bcm43xx installation for my specific card, but it's not working, and not even showing up at all.
Can someone please help?
I am about to bust!  I can't take it anymore.
Thank you so much.

This is what shows up in the Terminal when I run "lshw -C network"

gateway@gateway-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
gateway@gateway-laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
gateway@gateway-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:67:8d:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 1e:1c:64:c9:5d:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
gateway@gateway-laptop:~$

---

### Post by Ayuthia on 2008-11-03
> **Joe2Shoe said:**
> I followed the wiki on the bcm43xx installation for my specific card, but it's not working, and not even showing up at all.
Can someone please help?
I am about to bust!  I can't take it anymore.
Thank you so much.

This is what shows up in the Terminal when I run "lshw -C network"

gateway@gateway-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
gateway@gateway-laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
gateway@gateway-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:67:8d:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 1e:1c:64:c9:5d:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
gateway@gateway-laptop:~$

Can you post the results of:
```
ndiswrapper -v
ndiswrapper -l
```
You can also try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

---

### Post by jimv2000 on 2008-11-03
Does Ndiswrapper not work well with this particular card?

---

### Post by Joe2Shoe on 2008-11-03
tsali, I know what you mean.  
So, I uninstalled 8.10, then reinstalled 8.04 Hardy Heron.
Now, my D-Link DWL-G650 AirPlus ExtremeG PCMCIA card works using the ath_pci driver.
But, my Broadcom BCM4306 internal wireless adapter does NOT work, period!
The DWL-G650 only costs $13.38 on amazon...that includes shipping...what a cheap fix!
I guess I will stick with this setup on this laptop for awhile.
And, NO, NDISwrapper does NOT work with the Broadcom BCM4306 chip in 8.10 or 8.04.  I tried so many variations attempting to get it to work, that I forgot why I got up this morning.  I finally threw the towel in!
Best wishes to all, and a good night.
Joe2Shoe.
I am online right now using the D-Link DWL-G650 and 8.04 Hardy Heron.

---

### Post by Joe2Shoe on 2008-11-03
gatewaygateway@ubuntugateway:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 
gatewaygateway@ubuntugateway:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
gatewaygateway@ubuntugateway:~$ 


After my original post, I removed 8.10 and reinstalled 8.04.
The Broadcom BCM4306 is still not working, following the NDISwrapper installation for 8.04 to a T.
I am using a D-Link DWL-G650 AirPlus ExtremeG PCMCIA card with the ath_pci driver at this moment.  Even this card would not work in 8.10.

Thanks for your interest.
Joe2Shoe.

---

### Post by hksduhksdu on 2008-11-03
I have exactly the same card but I have no problem with it.  You can follow my thread here:

[http://ubuntuforums.org/showthread.php?t=969650](http://ubuntuforums.org/showthread.php?t=969650)

The most important part is to make sure you are connected to internet at first, let the Restricted Driver Manager searches for your Wireless card driver, when it shows in Restricted Driver Manager, it means it detects it correctly and you can activate it.  I didn't install NDISWrapper at all.

good luck.

---


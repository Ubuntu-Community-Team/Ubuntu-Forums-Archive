---
title: "Any hope of resolving SERIOUS network driver issues before 14.04 LTS?"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2014-02-18
Realtek is still a huge issue on Ubuntu, I believe due to outdated drivers that no one has bothered updating. I bought a Lenovo laptop that has an Intel wireless driver, thinking I'd be safe, but that's pretty horrible too. Atheros is the only one that works. Is there any hope of seeing these issues fixed for 14.04 LTS? They are serious problems that make my laptop nearly unusable on wifi. It would suck to be on a long term support OS that's broken in a severe way.

---

### Post by Bucky Ball on 2014-02-18
Realtek? Never had an issue. Running two of them now (and a TV dongle with a Realtek chip). Atheros? Generally fine. Intel? Most Intel wireless is covered right there in the kernel.  

What did you do to get these working that failed so miserably? Why don't you try and fix the problem with the card you have now by posting the output of this from a terminal:

```
sudo lshw -C network
```

Hard to know if 14.04 will be any different for you because no idea what your problem with these generally well supported cards is ... :-k

---

### Post by CaptSaltyJack on 2014-02-19
Hey, uh, Bucky Ball! :) I appreciate the response. I wish I had any hope of fixing my problem. Already posted before, but I suppose it couldn't hurt to get a different pair of eyes on it.

lshw -C network output:

```

  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:17:29:5e:4b:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-15-generic firmware=18.168.6.1 ip=192.168.11.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:46 memory:f1d00000-f1d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:fa:69:8e
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0c04000-f0c04fff memory:f0c00000-f0c03fff

```

---

### Post by Bucky Ball on 2014-02-19
This thread should get you somewhere:

[http://ubuntuforums.org/showthread.php?t=2089512](http://ubuntuforums.org/showthread.php?t=2089512)

Maybe some clues here also, but the full fix is in the first link. 

[https://www.kubuntuforums.net/archive/index.php/t-60746.html](https://www.kubuntuforums.net/archive/index.php/t-60746.html)

Remember to disable the wireless N capabilities. Post #7 here:

[http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable)

---

### Post by jimbo6 on 2014-03-21
Sounds suspiciously like yet another Realtek wifi card issue. From my experience and reading on the topic, it appears that realtek cards are just poorly supported on Ubuntu, although they perform just about flawlessly on PCs when dual booting.

According to this site:
**Realtek wireless chipset**
[COLOR=#000000][FONT=Arial]2.3. In case you have a Realtek wireless chipset that often loses connection and runs below its ordinary speed, that chipset probably runs on the buggy driver [/FONT][/COLOR][COLOR=#0000FF][FONT=Arial]rtl8192cu[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. You can[/FONT][/COLOR][install an improved driver like this]("https://sites.google.com/site/easylinuxtipsproject/reserve-7")"[COLOR=#000000][FONT=Arial].[/FONT][/COLOR]
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

I'm going through an issue which is yet to be resolved:
[http://ubuntuforums.org/showthread.php?t=2212089](http://ubuntuforums.org/showthread.php?t=2212089)

First take note of your specific Realtek chipset and then read these posts which have had some success:
[http://ubuntuforums.org/showthread.php?t=2044532](http://ubuntuforums.org/showthread.php?t=2044532)
[http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)
[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)
[http://ubuntuforums.org/showthread.php?t=2206392](http://ubuntuforums.org/showthread.php?t=2206392)

This rebuild of the driver looks most promising, but failed to work for me:
[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

However, posts 11 & 13 pretty much sum it up:
[http://ubuntuforums.org/showthread.php?t=2196909&page=2](http://ubuntuforums.org/showthread.php?t=2196909&page=2)
- [post #11]: Wait for a stable version of Ubuntu 14.04 LTS to come out (due to be release within a month, but advised to wait another four weeks to allow for the teething phase"). 
- [post #13]: Realtek wireless cards just aren't supported and are likely to encounter further problems in future. Ditch it and get another wireless card that is supported.

I know it's a rather disappointing result.

---

### Post by sdowney717 on 2014-03-21
I will testify that the Ralink 5370 usb wifi device works great for me. Plug and play.

My routers are all g band.
And I have had lots of wireless troubles with various hardware.

Mine looks like this one. And I did buy off Ebay this device.
[http://www.ebay.com/itm/150M-Ralink-RT5370-USB-2-0-Wireless-Network-Wifi-Card-New-New-802-11n-g-b-/111050907924](http://www.ebay.com/itm/150M-Ralink-RT5370-USB-2-0-Wireless-Network-Wifi-Card-New-New-802-11n-g-b-/111050907924)

---

### Post by varunendra on 2014-03-21
When posting experience with Realtek Wireless cards, it is VERY SIGNIFICANT to **also mention the kernel version** in use, since most of their proprietary drivers don't compile on the newer kernels, and a few of the old cards still don't seem to work well (e.g. rtl8723ae).

The 5370 is probably one of those whose driver from their official site won't compile on kernel >= 3.10, fortunately, the open source default driver in kernels >= 3.12 seems to be working reasonably well.

---

### Post by CaptSaltyJack on 2014-03-23
> **sdowney717 said:**
> I will testify that the Ralink 5370 usb wifi device works great for me. Plug and play.

My routers are all g band.
And I have had lots of wireless troubles with various hardware.

Mine looks like this one. And I did buy off Ebay this device.
[http://www.ebay.com/itm/150M-Ralink-RT5370-USB-2-0-Wireless-Network-Wifi-Card-New-New-802-11n-g-b-/111050907924](http://www.ebay.com/itm/150M-Ralink-RT5370-USB-2-0-Wireless-Network-Wifi-Card-New-New-802-11n-g-b-/111050907924)

Which version of Ubuntu are you using?

---


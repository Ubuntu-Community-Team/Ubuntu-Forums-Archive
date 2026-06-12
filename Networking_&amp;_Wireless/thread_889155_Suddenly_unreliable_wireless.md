---
title: "Suddenly unreliable wireless"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by sparrowkc on 2008-08-13
I don't remember when, but awhile back, Network Manager started endlessly asking for my wireless key when trying to connect to my network.  Switching to Manual configuration fixed it.  About a week ago, that stopped working too.  iwconfig seems to show that I am connected to the network, but have not been assigned an ip address.  Sometimes, if I am persistent, I can get it to connect briefly, only to die again shortly after.  It seems like my chances are better when the network in unencrypted, not so good with wep, and next to zero with wpa.  I don't think that this is an interference issue, the noise levels aren't that bad, I have tried different channels, and moving closer to the router doesn't help.  I only tested it once, but a windows laptop also had trouble connecting.

I have openwrt on my wrt54G router, switched from dd-wrt trying to fix things. I have a broadcom card in my laptop, I have tried Ndiswrapper and the broadcom driver.  They both worked in the past.


This is a terribly frustrating issue.

---

### Post by pytheas22 on 2008-08-13
The best way to figure out what's going on is to wait till the next time it crashes, them immediately open a terminal and run this command:
```

dmesg | tail
```

and post the output here.  That should contain messages from the kernel about why the connection is crashing.

It would also be useful to us if you posted:
```

lshw -C Network
```

Finally, you may want to see if you have better luck connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  A lot of people do.

---

### Post by sparrowkc on 2008-08-13
First off, thanks for responding!

I'm trying to gather information.  there is nothing new from dmesg after network manager fails to connect to a wpa network, I couldn't get it to connect and then fail.  I can successfully connect to the network if I turn off encryption.

lshw -C Network:
 ```
 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:25:1d:07:fd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:c2:45:78
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 ip=192.168.1.186 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

---

### Post by pytheas22 on 2008-08-14
Thanks for the information.  I see that you're using ndiswrapper on a Broadcom card.  First off, have you tried using the native driver?  I have the same chipset (Broadcom 4306) and it works well for me using bcm43xx.  That may solve the problem, although it would involve a bit of work to get bcm43xx going.

Otherwise, I do still suspect that Network Manager is at the heart of the issue, so using wicd instead may help.

Beyond that, please post "dmesg | tail" the next time it crashes, and hopefully that will explain concretely exactly what's going wrong and where.

---

### Post by sparrowkc on 2008-08-14
For now the problem seems to have solved itself, I'm connected using WPA, I will try wicd.  I have both ndiswrapper and b43 installed, ndiswrapper loads at startup but I can unload it and use b43 when I need monitor mode.

---

### Post by sparrowkc on 2008-08-14
Happening again...

I just got back on after a crash.

Lots of APIC Errors, there is 
[ 1484.895263] wlan0: deauthenticate(reason=3)

---

### Post by pytheas22 on 2008-08-14
hmmm, that error is pretty generic, unfortunately.  The next time it crashes, could you please post all of:
```

dmesg
```

It will be quite long but hopefully will provide more insight than the snippet above.

Your other option here is to use bcm43xx (the older version of b43).  It's in Hardy but by default it's blacklisted.  If you wanted to use it again, you'd have to blacklist b43, b43legacy, ssb and ndiswrapper, remove bcm43xx from the blacklist, then install the bcm43xx firmware with:
```

sudo apt-get install bcm43xx-fwcutter
```

(it will prompt you to download the firmware automatically).

---

### Post by sparrowkc on 2008-08-16
I've tried a windows laptop and an xbox, they both have similar problems at the same times, so I don't think the problem is with ubuntu.  I can connect to my neighbor's networks fine, so I don't think it's interference.  That means it must be the router.  I think I'll try the stock linksys firmware, and decide if it's a hardware problem or something that could be fixed.  I'll still post dmesg here if I catch it.

---

### Post by afilonov on 2008-08-16
> **sparrowkc said:**
> I've tried a windows laptop and an xbox, they both have similar problems at the same times, so I don't think the problem is with ubuntu.  I can connect to my neighbor's networks fine, so I don't think it's interference.  That means it must be the router.  I think I'll try the stock linksys firmware, and decide if it's a hardware problem or something that could be fixed.  I'll still post dmesg here if I catch it.

I'm having problems with Linksys access point (WAP54G) at work once in a while. The only remedy is to reset it by unplugging/plugging back power.

---


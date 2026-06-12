---
title: "Help with Wireless Internet"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by StormJosh on 2006-12-23
Can anyone help me set up my wireless internet. I'm a first time Ubuntu (and linux) user so the simpler the better :)

I'm using a Dell Latitude D810 with the following wireless card information that I get when using lspci in the terminal:

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controll (rev 02)

It also wouldn't configure properly when I was installing Ubuntu the first time.

I'm using Dapper Drake, not Edgy (due to the weird no root directory bug). I plan on upgrading to Edgy but I need to get my wireless working first.

Any support would be appreciated.

---

### Post by shane2peru on 2006-12-23
Well, I really can't help too much with the wireless, however if you are planning on upgrading to Edgy, I would recommend before investing time in getting your wireless running, you just go ahead and install Edgy.  Upgrading did have some issues, I don't know if they got the bugs worked out, but when I upgraded, it wasn't pretty.  I ended up just re-installing Edgy as a fresh install.  Or, just plan on sticking with Dapper, as it is Long Term Support.  Just my thoughts.

Shane

---

### Post by djRobbieF on 2006-12-23
If you're installing Edgy on a fresh hard drive, or wiping out the drive first, it works perfectly.  I think it was just the upgrade that caused problems for some users.

If you're going to do Edgy anyways, why not just give it a go first, and then see if you still have the trouble.  If yes, THEN post your questions.  But my concern is that you may be trying to fix something that's already been fixed (possible!) so why not try the newer version now, and then post your findings.

---

### Post by StormJosh on 2006-12-23
I tried installing Edgy fresh. But I'm booting it to an external hard drive that already has 130 GB of relatively important data on it that I have no other place for. I was able to partition aside 10 GB for the installion, 15 GB for home, and 2 GB for the swap.

It took me like 3 days to finally figure out how to install ubuntu on the external drive and let it boot, but now my problem is only with wireless internet.

I'll try the upgrade tonight, see if it allows me to use wireless, I'll post back.

Thanks for the replies!

---

### Post by dbott67 on 2006-12-23
I've got a Broadcom 4311 in my Dell laptop:
```
dbott@dapper:~$ lspci | grep Broadcom
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

```
```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

I've always had to use ndiswrapper (compiled from source) to get it working:

1. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

2. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

-Dave

---


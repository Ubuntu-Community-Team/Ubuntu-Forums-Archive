---
title: "Broadcom 4306 (Dell Wireless somethin or other) 208.11g issues"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by rjl5020 on 2007-03-26
Hey guys,

This is my first post here! But, before you hit BACK at the n00b, I've been using Linux and FreeBSD on and off for a few years, just for some reason figured I'd take a stab at desktop Linux, and lets just say, it's not near as much of the trek through the woods it used to be. Not only that, but I sure missed the command prompt.

I got EdgyEft dual booting on my Dell Inspiron 5100 laptop. Took me a day to figure out how to: 1. Find Broadcom firmware, and 2. Get the damn thing to connect to my router that's secured with WPA2, but I'm stuck on Number 3 and 4: I don't connect in 802.11g mode! I'm connected at 11Mbit, which isn't quite fast enough to stream video over to the xbox running XBMC. Furthermore, the connection randomly drops for a second or two, never long enough for it to kill connections, but enough for them to hang up for a second. I've read that's NetworkMonitor searching for networks, and 'iwlist eth1 scan' has the same effect.

In case it helps:

iwconfig eth1:

```
eth1      IEEE 802.11b/g  ESSID:"linksys2414"  Nickname:"linksys2414"
          Mode:Managed  Frequency=2.447 GHz  Access Point: 00:12:17:1C:6D:45   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:--   Security mode:open
          Link Quality=70/100  Signal level=-57 dBm  Noise level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:11084  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw:

```
 *-network:1
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@02:02.0
                logical name: eth1
                version: 02
                serial: 00:90:4b:b2:f4:41
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-11-generic ip=192.168.1.108 link=yes multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:faffc000-faffdfff irq:11

```

---

### Post by Floppyjoe on 2007-03-26
The Broadcom43xx driver you are using is one that can only do b speed(11Mbps).
If you used ndiswrapper you would get much faster speed out of it.

---

### Post by rjl5020 on 2007-03-26
Forgive my asking, but why does it detect it as 11g capable then? Emulating the Windows driver model just for my wireless card seems like a huge waste of resources to me, but that's just a guess.

---

### Post by Floppyjoe on 2007-03-27
> **rjl5020 said:**
> Forgive my asking, but why does it detect it as 11g capable then? Emulating the Windows driver model just for my wireless card seems like a huge waste of resources to me, but that's just a guess.

This is the Url of the driver developers list of supported devices:

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

These are experimental unstable reverse engineered drivers. from what I have read on the Forum they are only capable of the slower speed.

---

### Post by rjl5020 on 2007-03-27
Well, tried the ndiswrapper route, and it's works perfect now. Thanks!

---


---
title: "Dell Latitude LS 400 &amp; SMC Model SMC2635W"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by Wade85 on 2007-09-26
Hi All.

I have only been using Ubuntu (7.0.4) for a week if I and sort out wireless I think I will be a convert)

My wifi card is recognised - well I think the light comes on and now I have 2 new devices wlan1 and wmaster0.

If i open network manager I have tried both leaving it in 'roaming' and setting the card to manual and inputting the ssid and WEP ( not WPA just WEP) and no connection - but some times I get the light on the PCMCIA card to flash as it a small amount of data is being sent like searching for a network etc.

But in KWifiManager it says 'out of range' whether I am sitting 30cm (1 foot) away from my wifi router.

Any thoughts - thanks

ws

PS it works on LAN

---

### Post by noob12 on 2007-09-26
You may be getting some old driver versions that you'll need to update to get them to work acceptably with that card.

If you start by posting the output of these commands, people might have suggestions:
```

lspci -nn

sudo lshw -C network

```

---

### Post by Wade85 on 2007-09-26
Here are some I prepared earlier lol

> 

ISHW

  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth1
       version: 78
       serial: 00:b0:d0:51:5d:94
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=80 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: ioport:fc00-fc7f iomemory:fedfec00-fedfec7f irq:10
  *-network
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 1
       bus info: pci@02:00.0
       logical name: wmaster0
       version: 20
       serial: 00:04:e2:84:8b:0d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=adm8211 latency=64 maxlatency=128 mingnt=64 multicast=yes wireless=IEEE 802.11b
       resources: ioport:1000-10ff iomemory:14000000-140003ff irq:10

> IFTAB

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:e6:85:84:91 arp 1
wlan0 mac 00:18:4d:02:a2:12 arp 1

> interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


---

### Post by Wade85 on 2007-09-27
bump

---

### Post by noob12 on 2007-09-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You might be seeing the same bug as indicated.  

Does 

```

sudo iwlist scan

```

show any access points?  your access point?

There may be a more recent version of the driver that works properly.  You'd have to download source and build that.  I haven't ever done that for this driver.

---

### Post by Wade85 on 2007-10-19
> **noob12 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You might be seeing the same bug as indicated.  

Does 

```

sudo iwlist scan

```

show any access points?  your access point?

There may be a more recent version of the driver that works properly.  You'd have to download source and build that.  I haven't ever done that for this driver.


Yes my AP shows up but willnot connect even with WEP turned off....

any ideas?

ws

---

### Post by Wade85 on 2007-10-31
Have now upgraded to 7.10 via wired connection and now ubuntu cant find my card even with its drivers installed


:(

ws

---

### Post by dangermouse28 on 2007-11-08
I have exactly the same problem. Upgraded from Dapper to Gutsy - lost all wifi support in the process. The adm8211 module isn't loaded anymore and I don't know what I can do. I've even tried using ndiswrapper and windoze drivers. The adaptor powers up but it won't scan (no scan results) and won't connect. To add insult to injury, my USB wireless connector which has been a life-saver many times now behaves in exactly the same way. Something has changed in Gutsy which is crippling the operation of these interfaces :(

---


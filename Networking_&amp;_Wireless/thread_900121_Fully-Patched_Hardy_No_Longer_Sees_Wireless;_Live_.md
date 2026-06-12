---
title: "Fully-Patched Hardy No Longer Sees Wireless; Live CD Works Fine"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by talkingwires on 2008-08-25
Okay, I've been running Hardy since the beta, and recently started having increasingly bizarre problems with my wireless connection:[LIST=1]
[*]Starting about a week ago, Hardy started "forgetting" how to connect to a wireless network. I boot up, and everything's great, but after twenty-four hours or so of uptime, Hardy can see wireless networks, but no longer connect to them. I have to reboot.
[*]A few days (and a few patches from constant trickle from upstream) later and now Hardy can no longer connect immediately after rebooting. It can see the networks, but I have to wait ten to thirty minutes before it can connect.
[*]Today (and after the latest ubuntu-modules failed to install), Hardy no longer recognizes my wireless card. And it's not just network-manager; the card doesn't show up under manual configuration, either. I am typing this with Hardy's Live CD. It is having *none* of the problems my fully-patched installation of Hardy is having.
[/LIST]I'm running an Intel 2200 mini-PCI wireless card on a Dell C640. I do have proposed-updates enabled, and wonder if the new ubuntu-modules is related to the problems. I can't really select an older kernel to boot from, since Grub and uSplash display nothing on my laptop's screen; I have to wait for GDM to kick in before I see anything.

I'm not sure how to diagnose this problem. Any help would be greatly appreciated.

---

### Post by dmizer on 2008-08-25
Try comparing the output (on both the live cd and the install) of this command:
```
lshw -C network
```

---

### Post by talkingwires on 2008-08-25
> **dmizer said:**
> Try comparing the output (on both the live cd and the install) of this command:
```
lshw -C network
```Okay, I see what you're getting at. I'm posting the output from the Live CD for my convince. I don't feel like mounting my drive and saving output to a text file. :)

If the wireless card shows up on my installation, then I guess something has gone horribly wrong with Network-Manager. If not, where do I begin to look?```
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:9a:c6:39
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth2
       version: 05
       serial: 00:0e:35:a4:b3:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.14 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:2
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 78
       serial: 00:0b:db:23:29:fd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
ubuntu@ubuntu:~$ 


```

---


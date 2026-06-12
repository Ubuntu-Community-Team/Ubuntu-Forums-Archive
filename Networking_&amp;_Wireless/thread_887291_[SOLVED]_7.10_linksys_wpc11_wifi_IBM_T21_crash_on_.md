---
title: "[SOLVED] 7.10 linksys wpc11 wifi IBM T21 crash on boot"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by steve_d on 2008-08-12
Ok after fighting with Ubuntu 8.04 for WPA support on my Linksys WPC11 V4 wifi B mini-card I decided to 'downgrade' to 7.10. I've got my wireless connection working, except when I boot with the card inserted I get the following error:

[IMG]http://i4.photobucket.com/albums/y149/steve_d/s3600026.jpg[/IMG]

Just to be clear, I'm using WPA authentication, so I'm not sure why I'm getting a WEP line in there.

If i put the card out, the laptop will boot normally, and then I can insert it and connect using wicd without problems.

Anyone know what this last line means? Thanks!

---

### Post by chili555 on 2008-08-12
> prism2_wep_encryptIs this really a Prism card? After you boot, insert the card and run:```
lspcmcia
sudo lshw -C network
lsmod | grep prism
```Thanks.

---

### Post by steve_d on 2008-08-12
Excellent question, I don't think the card has anything to do with prism, but perhaps the on board controller does... anyways:

```

steve@thinkpad:~$ lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:02.0)
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:02.1)
steve@thinkpad:~$ sudo lshw -C network
[sudo] password for steve:
  *-network               
       description: Realtek
       physical id: 0
       version: Rtl8139
       slot: Socket 0
       resources: irq:10
  *-network
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:a6:a0:cf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0c:41:c1:d7:8f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8180 driverversion=1.45+Realtek,10/07/2004,5.173.10 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
steve@thinkpad:~$ lsmod | grep prism
steve@thinkpad:~$ 

```

---

### Post by steve_d on 2008-08-12
Searching around randomly I found this bug report [Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156050") and added the realtek module to the blacklist. I had tried adding prism and every iteration of prism I could find to no avail, but blacklisting the r8180 module seems to have worked.

There is a long hang at boot when detecting hardware but it does continue to load Ubuntu and will auto connect to my WPA network.

EDIT: A warning to 8.04 users, the r8180 module does exist in 8.04, but from some of what I've read it isn't enabled, so blacklisting it should have no effect. I can't verify this though.

---


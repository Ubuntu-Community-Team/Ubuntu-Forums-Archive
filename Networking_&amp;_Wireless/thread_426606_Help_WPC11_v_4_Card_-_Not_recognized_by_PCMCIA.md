---
title: "Help WPC11 v 4 Card - Not recognized by PCMCIA"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by tmcgee on 2007-04-28
I have a WPC11 v4 card that worked well on Edgy, but won't work after the upgrade to Feisty.

Here is what I get from:
sudo lshw

     *-network UNCLAIMED
          description: Ethernet controller
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 0
          bus info: pci@07:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=64 mingnt=32
          resources: iomemory:5c000000-5c0001ff irq:9

pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available

I have the RealTek 8180 Windows XP Driver, so I can use ndiswrapper if necessary, but I think I need to get the card recognized by the pccardctl first and foremost.

I've looked in the wiki and community docs and they all seem to assume that the pccardctl works already.

Any help would be greatly appreciated!

Thanks,

Trav

---

### Post by fwheeler_1 on 2007-04-28
Hi-  Try these 2 threads

[http://ubuntuforums.org/showthread.php?t=414594&highlight=fwheeler_1](http://ubuntuforums.org/showthread.php?t=414594&highlight=fwheeler_1)

[http://ubuntuforums.org/showthread.php?t=417018&highlight=fwheeler_1](http://ubuntuforums.org/showthread.php?t=417018&highlight=fwheeler_1)

There are 2 basic approachs:  1)  install Windows drivers for the card via ndiswrapper or it's gui equivalent, 2) unblacklist the native driver and see how that works.  These approaches are described in the threads.

Good luck, Fw

---

### Post by fwheeler_1 on 2007-04-29
Please see updated post in thread [http://ubuntuforums.org/showthread.php?p=2557243#post2557243](http://ubuntuforums.org/showthread.php?p=2557243#post2557243) for an update on how to make this work with Network Manager.  --Fw

---

### Post by tmcgee on 2007-05-03
I got it working!

un-blacklisting the 818x driver got it initialized and Network Mgr could see the wlan0 connection
Then adding the 'x' to the essid got me running! 

Thank you to all who helped and to the many links to get me there... Y'all are awesome!

Trav

---


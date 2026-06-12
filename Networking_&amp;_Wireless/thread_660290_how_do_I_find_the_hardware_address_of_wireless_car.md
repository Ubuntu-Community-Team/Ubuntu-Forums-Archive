---
title: "how do I find the hardware address of wireless card"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by sheepfunk on 2008-01-06
Long story short, my wireless interface disappeared from the network manager, and I haven't gotten a response from my post  yet.
[http://ubuntuforums.org/showthread.php?t=659801](http://ubuntuforums.org/showthread.php?t=659801)

Now I'm trying to add an interface via the networking module of the webmin utility
[http://www.debianadmin.com/webmin-installation-and-configuration-in-debian-and-ubuntu-linux.html](http://www.debianadmin.com/webmin-installation-and-configuration-in-debian-and-ubuntu-linux.html) 

however I'm noticing that there is no hardware address associated with my wireless card when I run

lshw -C network

 *-network               
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:13:a9:f1:19:04
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.101.106 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


so I'm wondering how to find the hardware address of my wireless card, because it's a piece of info I need to add the wlan interface with the webmin tool.

---

### Post by pdub on 2008-01-06
Does the adapter appear if you type ifconfig?

```
ifconfig
```

The hardware address should be there.

---

### Post by pdub on 2008-01-06
Sorry, I just read your previous post, ifconfig not showing the adapter.

---

### Post by sheepfunk on 2008-01-06
thanks for the response, yeah it used to show up as wlan0 but now ifconfig only shows:

eth0      Link encap:Ethernet  HWaddr 00:13:A9:F1:19:04  
          inet addr:192.168.101.106  Bcast:192.168.101.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fef1:1904/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168420645 (160.6 MB)  TX bytes:7466072 (7.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:593583 (579.6 KB)  TX bytes:593583 (579.6 KB)

---

### Post by sheepfunk on 2008-01-06
Do you have any idea what the most likely area my problem is related to (drivers, config files, etc.), just to get pointed in the right direction so I can do more of my own research?

---

### Post by FreakTech on 2008-01-06
I have no idea why it's not showing in your ifconfig list, but you could always look on the card itself.  Most have the MAC address on a sticker on them. While you are at it reseat the card.  Could have come loose. Hope this helps

---


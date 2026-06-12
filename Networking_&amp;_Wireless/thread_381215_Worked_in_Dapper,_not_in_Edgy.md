---
title: "Worked in Dapper, not in Edgy"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by Moonshine on 2007-03-10
Hey all,

I upgraded to Edgy Eft (from Dapper Drake) by doing a clean install over the top. Previously in Dapper Drake, my wireless card (or at least to the best of my memory) worked perfectly fine out of the box. The card is a Dlink DWL-G650.

Now however, the card is not even listed in the Network Settings 'Connections' area. 

So I'm wondering what I need to do to get it working in Edgy.

Thanks.

---

### Post by dbott67 on 2007-03-10
Can you post the output of the following commands:
```
dbott@edgy:~$** [COLOR=Blue]ifconfig -a[/COLOR]**
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:05
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3089 (3.0 KiB)  TX bytes:3089 (3.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:6F
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43250791 (41.2 MiB)  TX bytes:4176793 (3.9 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000

``````
dbott@edgy:~$ [COLOR=Blue]**sudo lshw -C network**[/COLOR]
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
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.37 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
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
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

``````
dbott@edgy:~$ [COLOR=Blue]**cat /etc/network/interfaces**[/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```-Dave

---

### Post by Moonshine on 2007-03-10
Thanks for the reply!

```

david@david:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:95:66:0E:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xc00 

eth1      Link encap:Ethernet  HWaddr 00:0C:6E:E9:30:E1  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fee9:30e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15051114 (14.3 MiB)  TX bytes:754177 (736.5 KiB)
          Interrupt:185 Base address:0x6800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

david@david:~$ sudo lshw -C network
Password:
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@02:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:feaf0000-feafffff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth0
       version: 10
       serial: 00:11:95:66:0e:70
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:b800-b8ff iomemory:feaefc00-feaefcff irq:209
  *-network:2
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@02:0f.0
       logical name: eth1
       version: 10
       serial: 00:0c:6e:e9:30:e1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b400-b4ff iomemory:feadf800-feadf8ff irq:185

```

```

dbott@edgy:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

```

david@david:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp

auto eth1

iface eth0 inet dhcp

auto eth0

```

Am I right in thinking that the wireless card hasn't been detected at all? I'm currently connected via a cable while I get this problem sorted (But I preferably don't want a bright blue cable streaking through the house with the misses wakes up 	:rolleyes:

Thanks for the help, very much appreciated

---

### Post by dbott67 on 2007-03-10
Well, [COLOR=Blue]lshw[/COLOR] shows the card as UNCLAIMED, but it is detecting it (not quite sure what that means).

I found this solution [here]("http://www.linuxquestions.org/questions/showthread.php?p=2541597#post2541597").  They seem to be using the same card as you.  I also found another user who solved it using ndiswrapper.
>  Hi.  Yes, same card and same problem with Edgy. Solved it so far by using madwifi-old:

1. install the sharutils and the build-essential packages
2. uninstall the restricted-modules package
3. Get old madwifi [http://snapshots.madwifi.org/madwifi-old-current.tar.gz](http://snapshots.madwifi.org/madwifi-old-current.tar.gz)
4. untar, make, sudo make install
5. Check to make sure old modules are not loaded and remove if they are.
6. sudo modprobe ath_pci
7. sudo dhclient ath0

Anita
[http://linuxbasics.org]("http://linuxbasics.org/")

BTW, I've never used madwifi, but I use ndiswrapper on my laptop, so I can help you with it, if needed.

You can check my post [here]("http://www.ubuntuforums.org/showthread.php?t=274915") for compiling ndiswrapper from source.  See the 1st post, start reading at the "**Broadcom 4311 Wireless**" section.  Keep in mind that you'll need to you the appropriate drivers for your card (and you can skip step #4 about blacklisting bcm43xx).

-Dave

---

### Post by dbott67 on 2007-03-10
Here's some more info on madwifi:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

-Dave

---

### Post by awperk on 2007-03-10
I'm having a similar problem with a prism 2.5 chipset wireless card. It worked on startup when i originally installed dapper but when i just updated to edgy, everything went haywire. The card's id was eth1 on dapper and now for some reason is wlan0 and says it's just an ethernet connection instead of wireless. I also can't seem to enable the card on edgy. My cards old profile is still listed under /etc/network/interfaces with the correct settings. Is there anyway to switch back to the old eth1 or change the wlan0 to identify my card correctly. thanks.

---

### Post by janhomb on 2007-03-12
I have got the same problem with my Prism 2.5 card on Edgy. It appeared when I updated the kernel from kernel 2.6.17-10 to kernel 2.6.17-11. The card still works when I boot in kernel 2.6.17-10.

---


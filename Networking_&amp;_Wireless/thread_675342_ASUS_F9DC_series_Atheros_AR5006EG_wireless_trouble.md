---
title: "ASUS F9DC series Atheros AR5006EG wireless troubles in Gutsy"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by Mygly on 2008-01-22
I don't know whether this should be here or in the hardware and laptops forum, but I thought I'd post here. I am running Gutsy and I cannot seem to get my wireless to be recognized in network settings, let alone work. For the command```
lspci -v | less
```, I got the following result for my built-in wireless. The restricted driver was enabled for it by default, but there is no sign of it in network settings. If anyone can help me out, I would be greatly appreciative. Thank you.

```
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1026
        Flags: fast devsel, IRQ 21
        Memory at febf0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
```

Also, this command```
sudo ifconfig -a
```
reuturns:
```
eth0      Link encap:Ethernet  HWaddr 00:1D:60:BF:C6:25  
          inet addr:192.168.1.143  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:febf:c625/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2340404 (2.2 MB)  TX bytes:315563 (308.1 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

no wlan, once again, thanks for any help you might be able to give me.

---

### Post by ugm6hr on 2008-02-03
Sorry, haven't read the whole thread, just trying to put AR5006/7 users in touch with potential solutions.

This may be of relevance:

[http://ubuntuforums.org/showpost.php?p=4259805&postcount=14](http://ubuntuforums.org/showpost.php?p=4259805&postcount=14)

---

### Post by Leighton on 2008-04-06
Just a quick note for other Asus F9DC users,  

I initially had this problem too.  After trying Ndiswrapper and madwifi installs without success i had all but given up, until...
[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)
Great howto, nicely written for newbies

Also changed my /etc/network/interfaces file to read this:


auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp


This solves the problem of seeing a wifi network but not being able to connect to it.
hope this helps someone else out too.

---


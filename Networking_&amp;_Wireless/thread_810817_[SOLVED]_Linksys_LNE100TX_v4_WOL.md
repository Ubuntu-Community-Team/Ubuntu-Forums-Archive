---
title: "[SOLVED] Linksys LNE100TX v4 WOL"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by vashwood on 2008-05-28
I have the linksys LNE100TX v4 NIC in my computer and I'm trying to get WOL to work w/ server 8.04.  When I had windows installed, WOL worked flawlessly.  I have enabled all the options in the bios and I have a cable connected to my motherboard.

So I thought I'd be able to do it in ubuntu.  But when I entered this
```
ethtool -s eth0 wol g
```
I get the following error message.
Cannot get current wake-on-lan settings: Operation not supported
not setting wol.

```
ethtool eth0
```
Gives me:
No data available

```
ethtool -i eth0
```
Gives me:
driver: tulip
version: 1.1.15
firmware-version: 
bus-info: 0000:02:09.0

And lastly
ifconfig gives me (I took off the MAC address)
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.143  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe4a:a43e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10515693 errors:3 dropped:0 overruns:3 frame:3
          TX packets:3657087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2849022861 (2.6 GB)  TX bytes:260086757 (248.0 MB)
          Interrupt:15 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75824 (74.0 KB)  TX bytes:75824 (74.0 KB)

```

Does anyone have any ideas?  This was working fine in windows.

---

### Post by vashwood on 2008-05-28
It works.  It still gives that error message but I went ahead and halted the system.  And from my other machine I sent a magic packet.  worked perfectly.

---


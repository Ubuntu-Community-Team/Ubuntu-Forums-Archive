---
title: "Internet doesn't work even though Network Manager says internet is connected"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by zach014 on 2008-08-27
Here's the results of ifconfig.
**Edit: the eth0:avahi entry is now gone...?**
```

eth0      Link encap:Ethernet  HWaddr 00:12:17:55:33:6a  
          inet6 addr: fe80::212:17ff:fe55:336a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:1 overruns:0 frame:0
          TX packets:0 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xd800 

eth0:avahi Link encap:Ethernet  HWaddr 00:12:17:55:33:6a  
          inet addr:169.254.4.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66236 (64.6 KB)  TX bytes:66236 (64.6 KB)

```
After some research, I thought it might have something to do with discovering DHCP. When I run "sudo dhclient":
```

There is already a pid file /var/run/dhclient.pid with pid 5768
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:17:55:33:6a
Sending on   LPF/eth0/00:12:17:55:33:6a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I found another (unsolved) thread from February by someone with (perhaps) the same problem: [http://ubuntuforums.org/showthread.php?t=706554](http://ubuntuforums.org/showthread.php?t=706554)
When I try pinging Google it says nothing for a while and then it says:
```
ping: unknown host google.com
```

Thanks in advance,
Zach

---

### Post by Crafty Kisses on 2008-08-27
Post the results of ```
lshw -C network
```

---

### Post by Iowan on 2008-08-27
NM thinks it's connected because it has an address - albeit an avahi address.    Internet doesn't work because avahi address is not in subnet.  There are a few threads about this problem (I'll have to look for some).  Are you set for DHCP or roaming?

---

### Post by zach014 on 2008-08-28
I hope this helps!
```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 11
       serial: 00:12:17:55:33:6a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes

```

---

### Post by zach014 on 2008-08-29
bump

---

### Post by Crafty Kisses on 2008-08-29
Try to ping a website, do you get a reply?

---

### Post by zach014 on 2008-08-29
It doesn't say anything for a while, and then it says:
```
ping: unknown host google.com
```

---

### Post by zach014 on 2008-08-30
bump

---

### Post by zach014 on 2008-09-01
bump

---

### Post by Iowan on 2008-09-01
> **Iowan said:**
>  Are you set for DHCP or roaming?The question remains...

---

### Post by zach014 on 2008-09-01
Sorry about that. I don't know what it means.  When I go into Network Settings, I've got roaming mode enabled, if that helps.

---

### Post by zach014 on 2008-09-30
For some reason, about a week after the last post, the internet started working again. I have no explanation whatsoever. Perhaps a hardware failure

---

### Post by zach014 on 2008-10-13
I had two network cards in. A wireless card and an ethernet card. I recently removed the wireless card, and the ethernet card stopped working, when i put the wireless card back in, neither the wireless card or the ethernet card were working, and the original problem resurfaced. I have no idea what i did before to fix it, and maybe this information will provide some sort of clue.

---

### Post by jimv on 2008-10-13
Looking at your original post, your machine is not getting an IP address from your router/modem.  So that's why your internet isn't working.  Are you hooked into a router or a straight into your modem?

---

### Post by zach014 on 2008-10-13
i'm hooked onto the router.

---

### Post by jimv on 2008-10-13
Ok, do you have any  other machines hooked into the router?  Do they work?  Have you tried resetting the router?  (Unplug it for 30 seconds, plug it back in.)

---

### Post by zach014 on 2008-10-14
yeah, the other machines work, and i tried resetting the router to no avail.

---

### Post by zach014 on 2008-10-14
i think it's a hardware problem, because all of a sudden it's working again

---

### Post by jimv on 2008-10-14
Could be.  You could get a cheap NIC off Newegg, or see if anyone in your town has one for cheap on Craigslist.

---


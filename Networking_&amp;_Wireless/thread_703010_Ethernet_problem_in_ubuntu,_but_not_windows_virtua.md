---
title: "Ethernet problem in ubuntu, but not windows virtual machine"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by GorgonSed on 2008-02-20
Hi,

I just installed Ubuntu 7.10 a couple of days ago to see what it was like.  I normally use XP.

Anyway, the first time I booted it up the internet worked, which I thought was cool.  But now it doesn't work at all.  I think my problem is from my Windows XP virtual machine, which is what I'm on right now actually.  The virtual machine internet works fine, but the ubuntu internet isn't working at all.  WHEN it was working, I was running on the eth0 connection.

Ok, so I think you guys want this.  Please help.

```
john@amdjohnnyubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:D1:BF:69  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fed1:bf69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3259297 (3.1 MB)  TX bytes:742699 (725.2 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:13:D4:D2:39:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22144 (21.6 KB)  TX bytes:6788 (6.6 KB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72121 (70.4 KB)  TX bytes:72121 (70.4 KB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by The Cog on 2008-02-21
I don't understand your setup there. Are you running Ubuntu inside a VM on XP? 
If so, what makes you say that the VM internet works but Ubuntus doesn't?
Do you have a DHCP server?

---

### Post by nixscripter on 2008-02-21
Would you post the output of:

```
route
```

I'm wondering about the two interfaces with 192.168.1.* addresses.

---


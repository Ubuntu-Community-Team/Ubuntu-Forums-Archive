---
title: "slow boot because of network"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by jkarlsen on 2007-02-07
When i boot my laptop, it hangs for a while on the bootscreen.

have tried to remove the "-quiet" and "-splash" in grub to see the problem.

the task "setting up network" takes a long time.

a friend om mine said it maybe was because my wireless tries to connect to a network that is not in range... 

any suggestions?

---

### Post by dmizer on 2007-02-07
please post the contents of:
/etc/network/interfaces

as well as the output of:
ifconfig

SHOULD be an easy fix.

---

### Post by jkarlsen on 2007-02-08
> **dmizer said:**
> please post the contents of:
/etc/network/interfaces


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

> **dmizer said:**
> 
as well as the output of:
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:36:3C:87:DC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:02:0B:95:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16882 errors:0 dropped:1170 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x4000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6580 (6.4 KiB)  TX bytes:6580 (6.4 KiB)

---

### Post by dmizer on 2007-02-08
okay ... well, in the above you don't appear to be connected to the internet at all.  are you able to get connected to the internet?  or do you even WANT to be connected to the internet?

for the time being, replace everything in your /etc/network/interfaces file with the following:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
```

that will at least cut your boot time in half.  then we can think about getting you connected to the internet if you need that.

---


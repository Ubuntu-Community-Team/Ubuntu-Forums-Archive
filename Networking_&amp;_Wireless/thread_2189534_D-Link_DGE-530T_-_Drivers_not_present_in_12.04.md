---
title: "D-Link DGE-530T - Drivers not present in 12.04?"
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by iraiam on 2013-11-22
I'm trying to install a D-Link DGE-530T Gigabit NIC in my Ubuntu 12.04 system,  Apparently I read some bad information that said the drivers for this card were already in 12.04. 

I have also ran into conflicting information as to what module covers this device. modprobe outputs below.

> ira@MEDIACENTER:~$ modprobe sk98lin
FATAL: Module sk98lin not found.
ira@MEDIACENTER:~$

> ira@MEDIACENTER:~$ modprobe sk
FATAL: Module sk not found.
ira@MEDIACENTER:~$ 

> ira@MEDIACENTER:~$ modprobe skge
FATAL: Error inserting skge (/lib/modules/3.2.0-56-generic/kernel/drivers/net/ethernet/marvell/skge.ko): Operation not permitted
ira@MEDIACENTER:~$ 

I think it is actually sk based on this [http://manpages.ubuntu.com/manpages/raring/man4/sk.4freebsd.html](http://manpages.ubuntu.com/manpages/raring/man4/sk.4freebsd.html)

The new NIC is apparently not being detected at all

Listed is the 10/100 interface on the motherboard and nothing else.

> ira@MEDIACENTER:~$ ifconfig -a | grep eth
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:bd:a1:1c

I'm not sure what to do next mostly because I don't know which driver package I need to compile (if any)

anyone can point me in the right direction, I would appreciate it.

---

### Post by iraiam on 2013-11-22
Just for grins I installed the DGE-530T in my T7600 to make sure it does in fact work, it does. (Win 7 Pro)

I tried to make the Linux drivers that came on the CD,  there are problems with it, the drivers are stated as being for kernel 2.4x 2.6x, I got many warnings and a few errors, the make process failed horribly.

I'll have to go though and check each error and see if I can resolve due to missing libraries or some such, but it's becoming more trouble than it's worth,  I haven't done a compile is a few years due to my work increasingly being done in another OS.

---

### Post by Yellow Pasque on 2013-11-23
Try installing the 3.8 lts-raring-kernel

---

### Post by Bucky Ball on 2013-11-23
*Thread moved to **Networking & Wireless**.*

---

### Post by iraiam on 2013-11-23
> **Temüjin said:**
> Try installing the 3.8 lts-raring-kernel

Good call, that got it working. Thanks much.

I'll nose around and figure out which package(s) the thing actually uses.

---

### Post by Bucky Ball on 2013-11-23
Simple:

```
sudo lshw -C network
```

You will see the drivers, firmware, etc. down the bottom of the output for the network controller. 

Please mark this thread as 'solved' to help others. Thanks. Post a new thread for any further issue.

---

### Post by iraiam on 2013-11-23
At one time I thought that the r8169 driver was what I needed, but changed my mind after further reading. Oh well it's working with the r8169 driver so it must be the right one.

  
> 
  *-network
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev.C1) [Realtek RTL8169]
       vendor: D-Link System Inc
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 10
       serial: d8:fe:e3:38:d7:a4
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 driverversion=2.3LK-NAPI** duplex=full ip=192.168.0.28 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff


Both interfaces are listed now 
> 
ira@MEDIACENTER:~$ ifconfig -a | grep eth
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:bd:a1:1c  
eth1      Link encap:Ethernet  HWaddr d8:fe:e3:38:d7:a4 

---

### Post by iraiam on 2013-11-23
Additionally, I got it working in 3.2 kernel.

> 
			 				ira@MEDIACENTER:~$sudo modprobe r8169
ira@MEDIACENTER:~$

After a reboot the NIC functions fine.

---

### Post by Bucky Ball on 2013-11-23
Great news. ;)

---


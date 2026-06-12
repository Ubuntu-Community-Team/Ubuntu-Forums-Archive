---
title: "Random/Sporadic WIRED Internet Access on New HP 8.04 Dual Boot"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Rockmaninoff on 2008-08-14
Hey all-

Posting this from a newly installed 8.04 LTS 1.  I'm dual booting this with Vista (Home Premium) on a computer my brother just purchased.  Specs (if they matter):

Q6600
3GB RAM
430GB Vista partition, 40GB Ubuntu partition (he just wants to mess around)
nVidia 8400 GS

It's a refurbished HP computer.  After setting up Vista, I used the Live DVD of 8.04 to install.  Went off without a hitch and booted right into the Desktop.  However, upon connecting my wired ethernet connection, data transfer seems to be random.  The first two times I booted into Ubuntu, no data was transferred.  The next two times things worked fine.  It's been randomly working and not working since.  This is all during times where my laptop can connect and the Vista side can connect.

Any help?

ifconfig (currently the Internet is working):

```
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:75:b2:8d  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565 errors:0 dropped:893947414 overruns:0 frame:0
          TX packets:507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:675736 (659.8 KB)  TX bytes:75747 (73.9 KB)
          Interrupt:218 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11200 (10.9 KB)  TX bytes:11200 (10.9 KB)

```

---

### Post by Rockmaninoff on 2008-08-17
Bump with some new information:

I have this output for lshw -C network when Internet is working:

```
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:1e:8c:75:b2:8d
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.102 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

And when Internet ISN'T working:

ifconfig:

```
eth0     Link encap:Ethernet  HWaddr 00:1e:8c:75:b2:8d
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:4294967284 overruns:0 frame:0
         TX packets:0 errors:0 dropped:138 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:218 Base address:0xe000 

eth0:avahi     Link encap:Ethernet HWaddr 00:1e:8c:75:b2:8d
         inet addr:169.254.8.31 Bcast:169.254.255.255 Mask:255.255.0.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         Interrupt:218
         Base address:0xe000

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:281 errors:0 dropped:0 overruns:0 frame:0
         TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:17642 (17.2 KB)  TX bytes:17642 (17.2 KB)
```

lshw -C network

```
*-generic
description: Ethernet interface
product: Illegal Vendor ID
vendor: Illegal Vendor ID
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: ff
serial: 00:1e:8c:75:b2:8d
size: 1GB/s
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s
```


Any help?

Edit: It seems like avahi is doing something?  I don't even know what avahi is!  I'm going to Google some information on it.  Also, what could it mean by "Illegal vendor" in the non-working lshw -C network code?

---

### Post by Ayuthia on 2008-08-17
From what I have seen, the r8169 module does not seem to work too well with the 8168 cards.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

It says that Windows will disable the Wake on LAN and the r8169 module does not know how to turn it back on.  It sounds like the work-around is to shut down your computer and unplug it for about 10 seconds (so that it will reset the card) then you can start up Ubuntu and it will be ok.

If it does not, let us know.  I think that some people have also gone and compiled the r8168 module, but I have not confirmed this yet.  If the above link is the problem I would think that the r8168 would have the same issue.

---

### Post by Rockmaninoff on 2008-08-17
> **Ayuthia said:**
> From what I have seen, the r8169 module does not seem to work too well with the 8168 cards.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

It says that Windows will disable the Wake on LAN and the r8169 module does not know how to turn it back on.  It sounds like the work-around is to shut down your computer and unplug it for about 10 seconds (so that it will reset the card) then you can start up Ubuntu and it will be ok.

If it does not, let us know.  I think that some people have also gone and compiled the r8168 module, but I have not confirmed this yet.  If the above link is the problem I would think that the r8168 would have the same issue.

Unfortunately doing this (twice to check) didn't work for me.  Now, the problem may be that I removed avahi-autoipd and avahi-daemon through Synaptic?  Would that affect things?  If so, how should I reinstall it without Internet access?

---

### Post by Rockmaninoff on 2008-08-17
Posting this from the Linux side, Internet is working after I went through Vista's network configuration (via Device Manager).  The "Wake-on Lan after Shutdown" was already enabled, but following instructions here:

[http://ubuntuforums.org/showthread.php?p=2901884](http://ubuntuforums.org/showthread.php?p=2901884)

I also disallowed the computer to make power changes to the device.

After restarting and booting into Ubuntu (without taking off power to the mains or unplugging the cable) things weren't working.  I shut down, then unplugged, waited ~15 seconds, and restarted with my network cable removed.  Once Ubuntu had loaded, I plugged my network cable back in and things were up and running.  I'm going to reinstall avahi through Synaptic now.

Again, not positive if this is a permanent solution, but things seem to be working for now.  I will do a few reboots to make sure.

---


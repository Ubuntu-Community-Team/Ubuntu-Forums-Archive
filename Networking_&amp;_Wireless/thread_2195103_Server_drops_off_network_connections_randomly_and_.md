---
title: "Server drops off network connections randomly and becomes unresponsive"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by sanju_verma_99 on 2013-12-22
Hi all, I have a 11 years old PC that has been functional through the years. Recently I converted it to a Ubuntu Server (12.04 LTS, 32 bit). My plan was to use it as a media server, keep all digital media (pics, home vids, movies) on that server, share the drives via Samba over the network so it is accessible to others PCs/devices around the home. I also installed a mysql server on this PC, for development use.

Here is the problem. This server works fine with "light" network traffic. So if I am accessing mysql from another PC, it will be ok. If I ssh into the box from another PC, that is fine. But if I do any continous network activity, the Server will become unresponsive/go offline after a random interval of time (anywhere from 15 minutes to couple of hours max). The continous network activity could be anything like a large file transfer, or watching a movie from a drive shared on this server etc. When it does go into that mode, the Server becomes comletely inaccessible on the network - no response to ping, ssh etc. If I go to the machine and hook it up to a monitor, even then it does not respond to any command. The only way back at that point is a reboot.

This is what I have tried so far:
1. At first I thought that maybe the built in LAN in the motherboard has gone bad. So I bought and installed a PCI based LAN card - no change.
2. I disabled the onboard LAN in the BIOS - no change.
3. I was seeing the "eth0: no IPv6 routers present" in the syslogs, so I disabled IPv6 from sysctl.conf - no change.

I do not see anything obvious in the syslog, but I am definately not an expert either - any help will be greatly appreciated. To be honest, I am not even sure that the issue is related to networking, just that it displays itself when the Server is asked to do any continous network activity. It is a matter of pride for me to kee this old machine alive as long as I can...almost an emotional attachment now :-).

Some bits of information you folks might need are below. If you need anything else, please just ask.

```
sanjeev@WORKHORSE:/var/log$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:52:bf:66:4a  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:978711 (978.7 KB)  TX bytes:2566731 (2.5 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 B)  TX bytes:700 (700.0 B)

```
```

sanjeev@WORKHORSE:/var/log$ sudo lshw -C network
[sudo] password for sanjeev: 
  *-network               
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 10
       serial: 00:e0:52:bf:66:4a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.140 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:9000(size=256) memory:d8181000-d81810ff memory:80080000-8009ffff
```

---

### Post by houstonbofh on 2013-12-23
Start with making sure you have a stable platform.  Run memtest overnight.  This will test the memory, but it will also test the stability of the power supply and CPU.

Once you know it is for sure not hardware, we can start looking at other things...

---

### Post by sanju_verma_99 on 2013-12-23
Thanks for the reply houstonbofh! Starting that now, will report tomorrow morning :-).

---

### Post by sanju_verma_99 on 2013-12-24
Ran memtest for 17+ hours (still running). No errors reported. Please see attached snapshot for details.

---

### Post by sanju_verma_99 on 2013-12-30
Bumping this up...any pointers will be appreciated, thanks!

---

### Post by houstonbofh on 2014-01-01
Build a USB boot or boot from a LiveCd and test it again.  This will say if it is hardware or your install.  I would also try both 10.04 and 12.04 to see if it is a kernel specific problem.

---

### Post by nickabbey on 2014-01-01
This is your problem:

product: RTL8169 PCI Gigabit Ethernet Controller


A forum search will show that this is a fairly common issue.  As to why it happened with a pci nic as well, not sure - unless it was ALSO a realtek 8169.

I'm in the process of dealing with this nightmare currently. 
You can try installing the updated driver straight from realtek's web site.
I was able to make it work in my 10.04 system which ran stable for a LONG time - but I had this same problem back then too.
Only difference is that I was able to get it sorted back then, but so far, on 12.04 (x64), no such luck.I actually got it up and running by 
installing the driver from realtek, but it's only running at 100mbs, and it's a gb card connected to a gb router, and other machines on the network 
(connected to same router) are working fine at gb speed.

look for directions on downloading and compiling the r8168 driver, if i can find a decent link in my browser history ill post it for you, but I've been at this issue all
day with no resolution and it's late here

PS - that's not a typo, you have an r8169 device, but the driver is borked (has been for quite some time apparently).  the trick is to compile and install the r8168 driver (and you may have to blacklist the 8169 driver)

---

### Post by nickabbey on 2014-01-01
This is a pretty good thread, it got me up and running with the new driver, though I'm still struggling with the gigabit issue myself:

[http://ubuntuforums.org/showthread.php?t=1992200](http://ubuntuforums.org/showthread.php?t=1992200)

---

### Post by nickabbey on 2014-01-01
And this one, too:

[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

---


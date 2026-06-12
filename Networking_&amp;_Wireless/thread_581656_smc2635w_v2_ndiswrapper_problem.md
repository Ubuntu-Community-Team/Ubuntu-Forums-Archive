---
title: "smc2635w v2 ndiswrapper problem"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by spamzilla on 2007-10-19
After upgrading to Gutsy from Feisty, I removed the old Feisty kernel which broke my wireless. I have just installed the smc2635w v2 driver:

> ndiswrapper -l

net2635r : driver installed
device (1814:0101) present (alternate driver: rt2400)

My wireless still doesn't work. How can I fix my ra0 wireless driver or make the driver which is using ndiswrapper work?

---

### Post by Vadi on 2007-10-19
I had a simiar problem (but different card, different driver).

Try **sudo ifconfig wlan0 up**, I think that's what worked for me.

---

### Post by spamzilla on 2007-10-19
That didn't work as the LED light was already green. 

I tried reloading the driver by typing "modprobe ndiswrapper" but still no luck. Wicd doesn't pick up any wireless networks (im currently on xp using my wireless connection) so I know it works.

Anyone else got any ideas?

---

### Post by Vadi on 2007-10-19
There's a new wireless thing in the kernel that Gutsy is using, so that's why it's being odd.

Try doing **sudo lshw -C network**,and post what it says here.

---

### Post by spamzilla on 2007-10-19
Here's the output of that command:

> sudo lshw -C network 

  *-network DISABLED      
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 00:04:76:45:9d:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=yes maxlatency=5 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: ra0
       version: 00
       serial: 00:04:e2:d3:a1:fd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2400 latency=64 module=rt2400 multicast=yes wireless=RT2400PCI

---

### Post by Vadi on 2007-10-19
Strange, I expected a different result.

What does **iwconfig** say?

---

### Post by spamzilla on 2007-10-19
> iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2400PCI  ESSID: off/any  
          Mode:Managed  Channel=1  Bit Rate: 11 Mb/s   
          RTS thr: off   Fragment thr: off

If it helps, in network tools under interface ra0, the is no IPv4 protocol, just IPv6.

---

### Post by Vadi on 2007-10-19
Oh, sorry, I have no idea then.

File a bug on launchpad.net then, and search on the wiki (help.ubuntu.com/community), I *think* I remember this IPv6 problem described somewhere in there.

---

### Post by spamzilla on 2007-10-20
Thanks any way :)

Bump!

---

### Post by Vadi on 2007-10-20
See if this thread is helpful ([click]("http://ubuntuforums.org/showthread.php?t=563547")).

---

### Post by spamzilla on 2007-10-21
Yay it works!! I think blacklisting my driver is what made things work.

Thanks a lot :D

---

### Post by Vadi on 2007-10-21
Awesome.

---


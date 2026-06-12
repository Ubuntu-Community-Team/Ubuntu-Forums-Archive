---
title: "VT6102 fails to work on reboot"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by cpricejones on 2007-12-02
Hey guys,

I am a newb having issues with the VT6102 Rhine II (rev 78) onboard LAN. It works fine if I start up my system in XP and reboot into XP. It works fine if I boot into XP then Ubuntu/Gutsy. But if I boot into Gutsy and try to reboot into either gutsy or XP, it no longer works. what i have to do to get it to work again is to completely turn off the computer, then remove the power plug (to kill the LAN lights), plug back in, reboot.

I had this problem when I used Fedora too.

here is my configuration from lshw -C network

  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial:
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=xxx.xxx.xxx.xxx latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

when the card is working, if i ifconfig -s it will show eth0 and lo working fine. when i reboot, then eth0 is missing.

so i'm thinking somewhere in the system shut down process, my card is not being reset properly, but i have no idea how to do anything about this. it is not essential, as i have a fix for it (turn off / uplug), but it's annoying as all hell. :)

cheers

---

### Post by cpricejones on 2007-12-02
bump :(

---

### Post by cpricejones on 2007-12-13
nada?

---


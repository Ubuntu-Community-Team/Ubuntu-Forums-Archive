---
title: "What is going on, Ubuntu?? Some recent update is hosing my network connection??"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by berlinbrown on 2007-09-29
Hello

Some recent upgrade is hosing my network connection over time after a hour of inactivity.  The problem is simple.  If I am not using the internet or something similar I lose my network connection (internet and the ability to ssh to my other boxes).   My system has 3 machines (and 1 xbox360) connected to a router.  All of the other machines also have recent versions of ubuntu (6.06?) and they stay connected but this version of Ubuntu seems to lose it over time. These are all wired connections.

Also, it seems strange because, it is like the network hangs as opposed to a complete loss of a connection to the router.  For example, if I disconnect the router I get a message "Connection disconnected", but with this problem, I dont get a disconnection error, the internet for example will just not connect.  Eg, if I open firefox, it will attempt to connect to a site and wait for forever.  The only real solution is for me to reboot.

Another weird solution, if I leave connections open like an irc window open; I dont get that hanging problem (internet is active) but the minute I forget to launch irc and then go away from my computer I get that hanging issue.

Also, I have had this system for several months and it seems like this problem has existed for about 1 month or so.

Anyone have any ideas.

System:
Ubuntu fiesty
Linux houston 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

---

### Post by berlinbrown on 2007-09-29
Here are some commands I just run.

 sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:17:31:6f:5a:4e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:a800-a8ff iomemory:f8fff400-f8fff4ff irq:20


cat /etc/network/interfaces
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


eth0      Link encap:Ethernet  HWaddr 00:17:31:6F:5A:4E  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe6f:5a4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3057648 (2.9 MiB)  TX bytes:384322 (375.3 KiB)
          Interrupt:20 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---


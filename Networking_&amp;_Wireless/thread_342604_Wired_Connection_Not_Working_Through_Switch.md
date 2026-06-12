---
title: "Wired Connection Not Working Through Switch"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by silverado on 2007-01-20
Help!  

My Ubuntu desktop will not connect through my switch to the router.  Actually it will not even connect to the switch (no lights).  The lights flicker while I boot, but when Ubuntu takes control all connectivity is lost.  If I connect it directly to the router it works just fine (I am posting with that config now).

Another piece of info is that I have a Windows 2000 Pro desktop with the same PCI adapter connecting through the smart switch to the router and on to the network just fine.  I swapped cables, that is not the problem.  

I have pretty much narrowed the problem down to something with Ubuntu interfacing with the network through the unmanaged smart (autosensing) switch.  When I bring up the router config page I also see that the Mac address of the Ubuntu desktop is 00:00....00:00, which may be confusing the switch but not the router.  Any ideas?  

Hardware list:

Netgear GA311 PCI Adapter
Netgear GS605 Gigabit Ethernet Unmanaged Switch
Netgear WNR854T Wireless Draft-N Router with Gigabit

Thanks!

---

### Post by silverado on 2007-01-20
I just went to the terminal to use ifconfig and found that my hardware does indeed have a MAC address.

---

### Post by mips on 2007-01-20
Check duplex and speed.

---

### Post by silverado on 2007-01-20
Could you expand on checking the duplex and speed?  I am new to Ubuntu and am unsure if I should check this on the router, switch (not really possible), or computer.  I did an ifconfig and got the following (this is while connected directly to router not via the switch):

eth0      Link encap:Ethernet  HWaddr 00:16:6D:CE:FD:55 
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fecb:4d44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:493958 (482.3 KiB)  TX bytes:49976 (48.8 KiB)
          Interrupt:11 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212 (212.0 b)  TX bytes:212 (212.0 b)
)

I used ethtool to check this connection and found the following when connected directly to the router:

thor@ValHalla:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

I found the following when connected to the switch:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no

How do I change the settings while connected to the switch and keep them that way?

Thanks for pointing me in this direction

---

### Post by silverado on 2007-01-21
MIPS I found this in one of your other postings, but it is not working for me.  WHenever I use ethtool to try and change the settings, they are not applied.  ](*,)   

The first thing I do is try ethtool eth0 and it still shows the speed at 10 and half duplex.  This is driving me crazy.  I read somewhere that there may be a way to change the firmware, or recompile the kernel with a better driver.  Any ideas on ndisdriver?  Or is there an easier way?  Thanks.
--------------------------------------------------------------------------------

You can try mii-tool or ethtool.

mii-tool:
Options are- 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
sudo mii-tool -F 100baseTx-FD eth0 would set the card to 100Mb/s Full-Duplex

ethtool:
Options are-
-s DEVNAME \
[ speed 10|100|1000 ] \
[ duplex half|full ] \
[ port tp|aui|bnc|mii|fibre ] \
[ autoneg on|off ] \
[ phyad %d ] \
[ xcvr internal|external ] \
[ wol p|u|m|b|a|g|s|d... ] \
[ sopass %x:%x:%x:%x:%x:%x ] \
[ msglvl %d ]

sudo ethtool -s eth0 speed 1000
sudo ethtool -s eth0 duplex full

---

### Post by mips on 2007-01-21
What does **lspci -v | grep Eth** give you ?

Check the LAN chipset from the above output against these forums via a search to see if there are any known issues. Some chipsets don't play nicely.

Maybe disable IPv6.

---

### Post by mips on 2007-01-21
I looked at your ethtool output again and when you connect to the switch you have no LINK status.

Are you using the same cable to the switch that you used to the router ? Remember that the router would require a X-Over cable and the switch a Straight cable.

Some newer 1Gb cards will do auto MDI-X / MDI swicthing internally to make a cable crossover or vice versa.

---

### Post by silverado on 2007-01-21
MIPS - thanks for all your help.  I am using a smart switch which automatically senses the type of traffic and can work without using the crossover.

I fixed the problem this evening by removing the netgear GS605 switch with a linksys EG008W switch.  The Netgear GA311 (RTK 8691) immediately recognized the switch and connected through the switch to the router no problem.  :D 

Who would have known that the Netgear switch would not connect with the Netgear card, and all I needed was to buy a better switch :lolflag:

---


---
title: "Network problems, can't see eth1"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by len1x on 2008-07-03
Some guy on my LAN installed Ubuntu and I couldn't resolve his hostname but could ping his ip.. anyways being stupid enough I uninstall DHCP3 ;/
got the packages from my other machine and installed them..

Now I can connect to my internet but I can't communicate with the network.. I can't even see eth1 ( which is my lan card ) in ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:00:f2:75  
          inet6 addr: fe80::219:d1ff:fe00:f275/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:469547 (458.5 KB)  TX bytes:73163 (71.4 KB)
          Base address:0x40c0 Memory:92200000-92220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85600 (83.5 KB)  TX bytes:85600 (83.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.108.64.202  P-t-P:194.165.130.224  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:456491 (445.7 KB)  TX bytes:60209 (58.7 KB)

```

i'm also missing that network icon on my panel.. big mess , im really sad i was stupid enough to do that ;/

can anybody help? :(

---

### Post by len1x on 2008-07-03
anyone?

---

### Post by pytheas22 on 2008-07-03
What is the output of:
```

lshw -C Network
```

Is dhcp3 the only thing you installed?  And you didn't do anything else to your computer besides install that package?  Did you change any configuration files?

---

### Post by len1x on 2008-07-03
```
 *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:00:f2:75
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-0 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Network controller
       product: B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
       vendor: Techsan Electronics Co Ltd
       physical id: 1
       bus info: pci@0000:07:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b2c2_flexcop_pci latency=32 module=b2c2_flexcop_pci
  *-network:1
       description: Ethernet interface
       product: SURECOM EP-320X-S 100/10M Ethernet PCI Adapter
       vendor: MYSON Technology Inc
       physical id: 2
       bus info: pci@0000:07:02.0
       logical name: eth1
       version: 00
       serial: 00:02:44:66:73:77
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=fealnx driverversion=2.52 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=fealnx multicast=yes port=MII speed=10MB/s

```

This is the output of the above command.. The only thing I did we deleting dhcp3 and reinstalling it..

By the way I did ifconfig eth1 up and now I can see eth1 when i do ifconfig.. but still no luck with communicating with network

---

### Post by pytheas22 on 2008-07-03
I'm thinking that maybe Network Manager (the thing in the panel that manages connections) was autoremoved when you uninstalled dhcp.  Try:
```

sudo apt-get install network-manager-gnome
sudo ifconfig eth1 up
sudo NetworkManager
```

then see if you can connect normally.  If not, try:

```
sudo dhclient eth1
```

Does that get you a connection?

---

### Post by len1x on 2008-07-03
Thanks man, there is progress, I got back the networkmanager.. can connect to my adsl connection when i click on the icon and connect to dslprovider

but I still can't ping another ubuntu machine on my lan
/home/lenix# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

and it hangs on that line.. any ideas?

If it stays like this I might re-install ubuntu as a last resort.. I'm still kinda new to it, 2 days running it, and no i'm not giving up on it :P it's better than winblows

---

### Post by TreeFinger on 2008-07-03
are you sure that is the IP of the other ubuntu box?

---

### Post by len1x on 2008-07-03
Yes it is.. I'm seriously lost here ;/
here is the output of /etc/network/interfaces .. if it has to do with anything ? im not sure
```
lenix@JUST-TRY:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

```

edit: I also can't ping my machine from the other ubuntu machine, but I'm sure the problem is in my machine..

lenix@JUST-TRY:~$ ping just-try
PING JUST-TRY (127.0.1.1) 56(84) bytes of data.
64 bytes from JUST-TRY (127.0.1.1): icmp_seq=1 ttl=64 time=0.030 ms
64 bytes from JUST-TRY (127.0.1.1): icmp_seq=2 ttl=64 time=0.024 ms

shouldn't i be getting a network ip ?

---

### Post by pytheas22 on 2008-07-03
Yes, you should have an IP if Network Manager appeared to connect.  What does:
```

ifconfig eth1
```

say?

---

### Post by len1x on 2008-07-03
```
eth1      Link encap:Ethernet  HWaddr 00:02:44:66:73:77  
          inet6 addr: fe80::202:44ff:fe66:7377/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2394 (2.3 KB)  TX bytes:4959 (4.8 KB)
          Interrupt:18 Base address:0x1000 

```

---

### Post by pytheas22 on 2008-07-03
So eth1 doesn't really have an IP address...any Network Manager definitely says it's connected?  It could be connecting through another interface (eth0 or ppp0).

What does this do:
```

sudo ifconfig eth0 down
sudo ifconfig ppp0 down
sudo dhclient eth1
```

(If it breaks the Internet, you can use:
```

sudo ifconfig eth0 up
sudo ifconfig ppp0 up
```

to be able to connect again.)

---

### Post by len1x on 2008-07-03
Seems like ppp0 disappears when I do sudo ifconfig eth0 down

here is the whole process you asked me to do
```
lenix@JUST-TRY:~$ sudo ifconfig eth0 down
lenix@JUST-TRY:~$ sudo ifconfig ppp0 down
ppp0: ERROR while getting interface flags: No such device
lenix@JUST-TRY:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 8222
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:02:44:66:73:77
Sending on   LPF/eth1/00:02:44:66:73:77
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
lenix@JUST-TRY:~$ sudo ifconfig eth0 up
lenix@JUST-TRY:~$ sudo ifconfig ppp0 up
ppp0: ERROR while getting interface flags: No such device
lenix@JUST-TRY:~$ 

```

---

### Post by pytheas22 on 2008-07-03
hmmm, I'm not sure what's going on.  That's weird that you can't bring ppp0 back up.

It might be easier to just reinstall Ubuntu.  If you only installed Ubuntu yesterday, then presumably you don't have much invested in that installation, and it only takes half an hour to do a fresh install.  So that might make more sense.

That said, I'm perfectly willing to keep trying to fix the existing installation if that's what you want to do, so just let me know and I'll think about what to try next.

---

### Post by len1x on 2008-07-04
Will do a reinstallation soon

---


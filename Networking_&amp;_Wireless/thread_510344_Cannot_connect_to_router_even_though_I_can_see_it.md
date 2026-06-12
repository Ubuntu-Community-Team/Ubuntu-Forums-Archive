---
title: "Cannot connect to router even though I can see it"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by droseman on 2007-07-26
Hi All,

I have an issue with connecting to my router using wireless.  I have Netgear DG834G router and a Netgear client card in the PCI.  I can see the networks in network manager (actually its wicd, based on a rec from here), but when I try to connect with all the security turned off I still cannot.

Here is a grab of ifconfig -a

```


[Thu Jul 26;19:40:43] droseman:~ $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8D:63:12:2D  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe63:122d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1663568 (1.5 MiB)  TX bytes:327660 (319.9 KiB)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380 (380.0 b)  TX bytes:380 (380.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:84:C7:04  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe84:c704/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9421 (9.2 KiB)  TX bytes:4369 (4.2 KiB)
          Interrupt:20 Memory:e6010000-e6020000 

```

Any ideas ?

Dave

---

### Post by imdano on 2007-07-26
Are you assigning static ips?  Because that output makes it seem like you're connected.  Also what's the output of ```
sudo lshw -C network
```

---

### Post by droseman on 2007-07-28
Hi 

I have my router set to use dhcp, there are no static ips set up.  Also, i can connect using Windows box with no trouble

Output of lshw shown below 
```

 *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:50:8d:63:12:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=192.168.0.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: iomemory:e7000000-e7000fff ioport:c400-c407 irq:16
  *-network DISABLED
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@01:08.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:84:c7:04
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e6000000-e600ffff iomemory:e6010000-e601ffff irq:20
[Sat Jul 28;13:52:55] droseman:~ $ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:50:8d:63:12:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=192.168.0.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: iomemory:e7000000-e7000fff ioport:c400-c407 irq:16
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@01:08.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:84:c7:04
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e6000000-e600ffff iomemory:e6010000-e601ffff irq:20

```

---

### Post by imdano on 2007-07-28
Could you post the output of ```
ndiswrapper -v
ndiswrapper -l
```What are you using as your wpasupplicant driver in wicd?  And any idea why in your first post wlan0 (your wireless interface) was able to get an ip address?  That suggests you did successfully connect.

---

### Post by droseman on 2007-07-28
From wicd, the WPA supplicant driver is listed as "wext"

No idea why I was able to get an ip originally, I just checked and I don't seem to have  one now, also, after my original post, I disabled the eth0 interface leaving just wlan0 and i was unable to connect still.

Below shown output of ndiswrapper -v and ndiswrapper -l

```

[Sat Jul 28;18:27:24] droseman:~ $ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
[Sat Jul 28;18:28:31] droseman:~ $ ndiswrapper -l
bcmwl5 : invalid driver!
wg311v3 : driver installed
        device (11AB:1FAA:1385:6B00) present
        device (11AB:1FAA) present

```

---


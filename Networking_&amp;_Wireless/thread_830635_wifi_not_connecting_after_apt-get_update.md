---
title: "wifi not connecting after apt-get update"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by kernelsanders on 2008-06-16
as the title says I did an apt-get update and now I am unable to connect to my router via my atheros card. also, the network manager is missing from the upper panel and it wont' start after typing Alt+f2 nm-applet. I wanted to get this app running since it's used in a posting of a similar problem: 
[http://ubuntuforums.org/showthread.php?t=810723&highlight=apt-get+update+wifi+-connecting](http://ubuntuforums.org/showthread.php?t=810723&highlight=apt-get+update+wifi+-connecting)

There are also errors related to network manager when I shutdown but they go by so fast all I can make out is something about network manager and a bus...?  Would these be logged anyplace for me to find?
 
Not sure what to do next so I'm listing what I've done so far in hopes that some ubuntu guru can point me in the right direction:

Attempted  
> sudo dkpg -r network-manager-gnome network-manager
> sudo apt-get install network-manager-gnome
> sudo apt-get install network-manager 
but this did not get the program to run.

Tried turning off the wifi interface, and then back on:
> sudo ifdown wifi0 --force
> sudo ifup wifi0 
[output...]
There is already a pid file /var/run/dhclient.wifi0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Just in case it helps here is some of the output from ifconfig -a and lshw -C network.

thoth@alexandria:~$ ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:40:f4:f3:94:84  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:23:be:7d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe23:be7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:16710378 (15.9 MB)  TX bytes:1588780 (1.5 MB)
          Memory:50380000-503a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119000 (116.2 KB)  TX bytes:119000 (116.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-40-F4-F3-94-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45254 errors:0 dropped:0 overruns:0 frame:264
          TX packets:1029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5535928 (5.2 MB)  TX bytes:47334 (46.2 KB)
          Interrupt:20 

thoth@alexandria:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:23:be:7d
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.2.0 duplex=full firmware=1.3-0 ip=192.168.1.100 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:40:f4:f3:94:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
thoth@alexandria:~$

---


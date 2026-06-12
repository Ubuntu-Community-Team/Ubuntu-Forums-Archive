---
title: "[SOLVED] No wireless AR2413 Atheros"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by fewjr on 2008-09-22
I am having trouble getting wireless up with hardy heron lshw -C network gives me: 

 *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:89:b4:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:d0:5b:98:d4
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.104 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

The AR2413 is my dlink WDA-1320 pci card.I have tried to follow kevdog's manual connect guide and this is what I get:

goblin@goblin-lanbox:~$ sudo ifconfig ath0 down
goblin@goblin-lanbox:~$ sudo dhclient -r ath0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:b4:1f
Sending on   LPF/ath0/00:15:e9:89:b4:1f
Sending on   Socket/fallback
goblin@goblin-lanbox:~$ sudo ifconfig ath0 up
goblin@goblin-lanbox:~$ sudo iwconfig ath0 essid "tubescreamer"
goblin@goblin-lanbox:~$ sudo iwconfig ath0 xxxxxxxxxxxxxxxxxxxxxxxxxx
iwconfig: unknown command "xxxxxxxxxxxxxxxxxxxxxxxxxx"
goblin@goblin-lanbox:~$ sudo iwconfig ath0 key shared
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "shared".
goblin@goblin-lanbox:~$ sudo iwconfig ath0 restricted
iwconfig: unknown command "restricted"
goblin@goblin-lanbox:~$ sudo iwconfig ath0 mode Managed
goblin@goblin-lanbox:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:b4:1f
Sending on   LPF/ath0/00:15:e9:89:b4:1f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
goblin@goblin-lanbox:~$ 

I'm not sure why its not taking my 128bit HEX key. I have replaced the 26 digits with x for this post. The actual key was used to recieve this output. It is a combination of numbers and letters. What am I doing wrong there? My router is setup as Shared, but it says its an unknown command as well as Restricted. The guide doesn't talk alot about that. Just that that line of commands may be needed.  Any ideas folks?

---

### Post by fewjr on 2008-09-24
Update.....I disabled HAL layer in System>Admin>hardware drivers as per a howto I read. I unistalled old Madwifi modules and downloaded and compliled the latest Madwifi. Everything went fine there. Then I ran the following commands in the terminal:


goblin@goblin-lanbox:~$ sudo ifconfig ath0 down
[sudo] password for goblin: 
goblin@goblin-lanbox:~$ sudo dhclient -r ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:b4:1f
Sending on   LPF/ath0/00:15:e9:89:b4:1f
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
goblin@goblin-lanbox:~$ sudo ifconfig ath0 up
goblin@goblin-lanbox:~$ sudo iwpriv ath0 authmode 2
goblin@goblin-lanbox:~$ sudo iwconfig ath0 essid "tubescreamer"
[sudo] password for goblin: 
goblin@goblin-lanbox:~$ sudo iwconfig ath0 key xxxxxxxxxxxxxxxxxxxxxxxxxx
goblin@goblin-lanbox:~$ sudo iwconfig ath0 mode Managed
goblin@goblin-lanbox:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:b4:1f
Sending on   LPF/ath0/00:15:e9:89:b4:1f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
goblin@goblin-lanbox:~$ sudo ifconfig eth0 up
goblin@goblin-lanbox:~$ 

The first time I did it after I put in new Madwifi it connected via DHCP to my router and acquired an IP. It even pinged Google okay. It however was conflicting with eth0 I guess because I was still using Firefox and it couldn't get on that way. I unplugged ethernet cable and rebooted and ran all the commands to bring up ath0 again. I couldn't get an IP this time or any other time since. The output above is what I get now even after I run sudo ifconfig eth0 down. I know my NIC is working because I saw it connect. What is going on here with my wireless:confused: Please help!

Here is the output of ifconfig again:

goblin@goblin-lanbox:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:89:b4:1f  
          inet6 addr: fe80::215:e9ff:fe89:b41f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:15:e9:89:b4:1f  
          inet addr:169.254.6.238  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5b:98:d4  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe5b:98d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2802197 (2.6 MB)  TX bytes:202544 (197.7 KB)
          Interrupt:222 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103200 (100.7 KB)  TX bytes:103200 (100.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-89-B4-1F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141557 errors:0 dropped:0 overruns:0 frame:289278
          TX packets:1688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:13914915 (13.2 MB)  TX bytes:80258 (78.3 KB)
          Interrupt:20 

IWCONFIG:



goblin@goblin-lanbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"tubescreamer"  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:139925  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and lshw:




goblin@goblin-lanbox:~$ sudo lshw -C network
[sudo] password for goblin: 
  *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:89:b4:1f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:d0:5b:98:d4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.104 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s

---

### Post by fewjr on 2008-09-30
I marked this thread as solved. I changed my wireless settings in my router from WEP to WPA personal. It would not connect with WEP no matter what I did. So anyone using Hardy with this Atheros chipset, give WPA a try. Its more secure anyway.

---


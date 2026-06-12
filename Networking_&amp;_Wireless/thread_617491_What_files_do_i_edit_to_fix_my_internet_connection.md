---
title: "What files do i edit to fix my internet connection?"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by edmonds on 2007-11-19
hi

i can connect if i boot in Recovery Mode, but not if i boot normally. 

So i was hoping that if i knew what files to look at /copy in recovery mode i could paste them to files in normal mode  and that might fix it.

So what files do i need to look for?

thanks

tom

---

### Post by Seisen on 2007-11-19
What kind of problems are you having with your internet connection and the files in recovery mode are the same one's.

---

### Post by edmonds on 2007-11-19
it doesn't connect to the internet. i have no idea why. or how to find out.

i have this:


 sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:b2:e5:43
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair

  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:48:42:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"stud10"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

ifconfig
ath0      Link encap:Ethernet  HWaddr 00:05:4E:48:42:3D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:05:4E:48:42:3D  
          inet addr:169.254.3.179  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0D:60:B2:E5:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13434 (13.1 KB)  TX bytes:13434 (13.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-48-42-3D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:976
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:18037 (17.6 KB)  TX bytes:17878 (17.4 KB)
          Interrupt:11 

 dhclient wifi0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted


 ifup wifi0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

 dhclient wifi0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 ifup wifi0
Ignoring unknown interface wifi0=wifi0.


thanks for replying - any ideas?
tom

---

### Post by edmonds on 2007-11-20
ok
perhaps the problem is that the laptop is muddled about what it should connect with:

Connection Properties shows only  - lo or atho:avahi
and a very slight connection, about 2kb


in Network Tools i can see:
   lo, 
   Ethernet Interface (eth0)
   Unknown Interface (wifi0) Configure=the interface does  not exist
   Unknown Interface (ath0) 
   Unknown Interface (ath0:avahi) Configure=the interface does  not exist. but seems to have packets

i think i need it to connect with ath0. So i need to get ath0 to appear in the Connection Properties box (and remove ath0:avahi (whatever that is))

so how can i do that?
tom

---

### Post by Kuzi on 2007-12-26
I got the same problem: "could not find interface: "ath0:avahi"
the named file: /proc/net/dev is empty! 
what must be the content?

---

### Post by kevdog on 2007-12-26
Your interface name is ath0 (you must be using the madwifi driver).  Why dont you first try connecting from the command line first to see if you can get everything up and running?? Again your interface name is ath0.  The commands are in my signature.

---


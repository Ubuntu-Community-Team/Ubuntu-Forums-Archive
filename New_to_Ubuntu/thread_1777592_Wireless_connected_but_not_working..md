---
title: "Wireless connected but not working."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by balaraja on 2011-06-07
Hi All,

I saw several old threads with title "Ubuntu:Wireless connected but not working". But I could not solve the problem.

Hence I am asking it here. I am able to connect to my Wireless but I am unable to browse. The outputs you expect

balaraja@balaraja-laptop:~$ **ifconfig eth1**
eth1      Link encap:Ethernet  HWaddr 00:22:69:76:32:e5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe76:32e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:13234
          TX packets:338 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42239 (42.2 KB)  TX bytes:41042 (41.0 KB)
          Interrupt:17 Base address:0xc000 

balaraja@balaraja-laptop:~$ **sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"ORANGE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C4:3D:C7:62:CD:4D   
          Bit Rate=48 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=4/5  Signal level=-61 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet2    no wireless extensions.

vmnet3    no wireless extensions.

vmnet4    no wireless extensions.

vmnet8    no wireless extensions.

balaraja@balaraja-laptop:~$ **sudo dhclient eth1**
There is already a pid file /var/run/dhclient.pid with pid 2136
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:22:69:76:32:e5
Sending on   LPF/eth1/00:22:69:76:32:e5
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
SIOCADDRT: No such process
bound to 192.168.1.2 -- renewal in 34311 seconds.

balaraja@balaraja-laptop:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.20.0       *               255.255.255.0   U     0      0        0 vmnet3
192.168.209.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
10.0.30.0       *               255.255.255.0   U     0      0        0 vmnet4
10.0.10.0       *               255.255.255.0   U     0      0        0 vmnet2

balaraja@balaraja-laptop:~$ **cat /etc/resolv.conf** 
nameserver 192.168.1.1

Please let me know, what should I do to connect to the internet.

Thanks,
Bala.

---

### Post by webofunni on 2011-06-07
are you able to ping 192.168.1.1 ? 

try adding a gw

```

sudo route add default gw 192.168.1.1 eth1

```

---


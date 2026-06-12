---
title: "Lost ubuntu connection?  windows works (with manual config)"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Mgiacchetti on 2008-06-05
Ubuntu Hardy 64, Linksys WAP54g v3.1 w/DD-WRT firmware, connected to WRT54g v? with current linksys firmware.

OK i am using a WAP54G downstairs with DD-WRT.  It is set as client bridge for my networking purposes, the WRT54G upstairs has linksys firmware.  anyway

Everything was working fine up until this morning..

my WAP is 192.168.1.2 with gateway as 192.168.1.1 (wrt)  all the settings match up fine, im "connected" but Ubuntu Hardy no longer sees either router, or the internet.

I rebooted into windows, and had the "limited or no connectivity" problem, so i manually set all my crap to whatever, and couldnt get to the net until i manually entered my DNS servers...

It seems that the WRT is no longer leasing me an ip addy, because I have to manually set my local ip to 192.168.1.115 to get it to work in windows.

Now this is the funny part.


Ubuntu cannot see the internet at all.. however..  in virtual box (which is in ubuntu) my win 2000 install sees the internet just fine (with the manual configuration)

Can anyone explain this??

---

### Post by superprash2003 on 2008-06-05
are you able to ping 192.168.1.1 or 192.168.1.2 from the ubuntu machine?

---

### Post by Mgiacchetti on 2008-06-05
destination unreachable

here's my ifconfig

```

br0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:49  
          inet6 addr: xxxx:xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:822140 (802.8 KB)  TX bytes:42971 (41.9 KB)

br0:avahi Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:49  
          inet addr:169.254.34.36  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:49  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: xxxx:xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14178175 (13.5 MB)  TX bytes:1275661 (1.2 MB)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:184305 (179.9 KB)  TX bytes:184305 (179.9 KB)

vbox0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:b8  
          inet6 addr: xxxx:xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14588 errors:0 dropped:177 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1047787 (1023.2 KB)  TX bytes:13897980 (13.2 MB)

```

---

### Post by Mgiacchetti on 2008-06-05
and heres when i try to ifup after ifdown for br0

```

sudo ifup br0
There is already a pid file /var/run/dhclient.br0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/br0/xx:xx:xx:xx:xx:49
Sending on   LPF/br0/xx:xx:xx:xx:xx:49
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Mgiacchetti on 2008-06-05
ok i figured it out, my bridge for virtualbox was preventing me to set static ip


but I still wish to figure out this dhcp thing

---

### Post by Mgiacchetti on 2008-06-05
also, the two wireless laptops upstairs are working now (after a power cycle of the WRT54g linksys firmware)

i tried power cycling my wap but to no avail, tried a factory reset, nothing.

gonna try one more factory reset, then set it up again, then the magic button on the back if that dont work..

---

### Post by Mgiacchetti on 2008-06-05
^bump^

still having problems with the WRT54G handing my WAP54G (client bridge) a dhcp address for my machine... i don't really like having to set static...

---

### Post by Mgiacchetti on 2008-06-05
what does this mean?  this was when i started having problems...

```

Jun  5 09:37:11 AMD-64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun  5 09:37:15 AMD-64 dhclient: DHCPREQUEST of <null address> on br0 to 255.255.255.255 port 67
Jun  5 09:37:18 AMD-64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jun  5 09:37:31 AMD-64 avahi-daemon[5143]: Withdrawing address record for 192.168.1.105 on br0.
Jun  5 09:37:31 AMD-64 avahi-daemon[5143]: Leaving mDNS multicast group on interface br0.IPv4 with address 192.168.1.105.
Jun  5 09:37:31 AMD-64 avahi-daemon[5143]: Interface br0.IPv4 no longer relevant for mDNS.
Jun  5 09:37:32 AMD-64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jun  5 09:37:32 AMD-64 dhclient: DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 8
Jun  5 09:37:40 AMD-64 dhclient: DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 10
Jun  5 09:37:42 AMD-64 dhclient: No DHCPOFFERS received.
```

and this is route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 br0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

---

### Post by Mgiacchetti on 2008-06-05
and it seems when i bring br0 and eth0 down and bring eth0 up, i get the same prob

br0 is set static, eth0 is dchp

im confused...

---

### Post by crane on 2008-06-10
I am having the same issues at work. I cna't figure out why DHCPDISCOVER is using subnet 255.255.255.255 our network is 255.255.255.0.

---

### Post by Mgiacchetti on 2008-06-14
k i figured out that my problem is with dd-wrt, and its a known issue with v24.

Just wondering when they will fix this issue.

---

### Post by Mgiacchetti on 2008-06-16
update, downgraded to DD-WRT v23 sp2 and the problem went away...

---


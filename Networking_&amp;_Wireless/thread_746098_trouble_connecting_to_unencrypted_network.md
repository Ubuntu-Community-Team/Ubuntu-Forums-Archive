---
title: "trouble connecting to unencrypted network"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by equity on 2008-04-05
I adready tried to connect to a WPA AP in vain a few days ago using the guide from kevdog:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Now it even does not work to connect to an unencrypted network with MAC-filter disabled. The point I wonder about is that it seems that kevdog only mentioned to create a text file when WPA is used, but in this text file is the WLAN driver cited that is not when connecting to a non encrypted network. So I think the problem is I need to cite my wlan driver on some way.

Thanks in advance for your help, here is my command line output, written bolt:


[B]user@G1-AP021C:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:ef:d8:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.
1.34 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:d2:69:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1
 firmware=14.2 1:0 () ip=192.168.1.67 latency=0 module=ipw3945 wireless=unassoci
ated
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo ifconfig eth1 down
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 29374
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
user@G1-AP021C:~$ sudo ifconfig eth1 up
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo iwconfig eth1 essid "my_essid_in_quotes"
user@G1-AP021C:~$ sudo iwconfig eth1 mode managed
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@G1-AP021C:~$ [/B]

---

### Post by kevdog on 2008-04-05
Try taking eth0 down.

Also when you do the lshw -C network statement -- you see your ethernet card and then the wireless card listed.  You do not want to see the words DISABLED under the wireless card, or nothing will work.  See your previous post above -- it states DISABLED.


You cant run wired and wireless for your purposes at the same time (its possible with other configurations however -- ie bridging).

---

### Post by equity on 2008-04-05
If you mean "*-network DISABLED" I think it is related to my wired ethernet connection because it is cited above my wlan device.
I think my ethernet adapter was disabled, but I tried it again and it still does not work... damn

[B]user@G1-AP021C:~$ sudo ifconfig eth0 down
[sudo] password for user:
user@G1-AP021C:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:D2:D2:69:00  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:485 errors:0 dropped:304 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24776 (24.1 KB)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 Memory:fe1ff000-fe1fffff 

eth1:avah Link encap:Ethernet  HWaddr 00:19:D2:D2:69:00  
          inet addr:169.254.5.216  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175420 (171.3 KB)  TX bytes:175420 (171.3 KB)

user@G1-AP021C:~$ sudo ifconfig eth1 down
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 29494
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
user@G1-AP021C:~$ sudo ifconfig eth1 192.168.1.37 netmask 255.255.255.0 up
user@G1-AP021C:~$ sudo route add default gw 192.168.1.1
user@G1-AP021C:~$ sudo iwconfig eth1 essid "my_essid_in_quotes"
user@G1-AP021C:~$ sudo iwconfig eth1 mode managed
user@G1-AP021C:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17

user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:D2:D2:69:00  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:485 errors:0 dropped:306 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24776 (24.1 KB)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175764 (171.6 KB)  TX bytes:175764 (171.6 KB)

user@G1-AP021C:~$ sudo ifconfig eth1 down
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
user@G1-AP021C:~$ sudo ifconfig eth1 up
user@G1-AP021C:~$ sudo iwconfig eth1 essid "my_essid_in_quotes"
user@G1-AP021C:~$ sudo iwconfig eth1 mode managed
user@G1-AP021C:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15

user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo ifconfig eth1 down
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
user@G1-AP021C:~$ sudo ifconfig eth1 up
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo iwconfig eth1 essid "my_essid_in_quotes"
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo iwconfig eth1 mode managed
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@G1-AP021C:~$ [/B]

---

### Post by kevdog on 2008-04-05
Post your lshw -C network again -- you have to solve the network DISABLED first before messing with the configuration -- don't put the cart before the horse.  The way Im looking at your old statment is that NETWORK DISABLED is referring to your wlan card and not your wired card.

---

### Post by equity on 2008-04-05
Oh... now I see you are right, it is really down... strange...

The point is I enabled my network and I can see networks when using airodump-ng for example...
I cannot figure out what is my problem...

Now the lshw command gives the same output as I have written in my first post of this topic

Any idea what is going on???

---


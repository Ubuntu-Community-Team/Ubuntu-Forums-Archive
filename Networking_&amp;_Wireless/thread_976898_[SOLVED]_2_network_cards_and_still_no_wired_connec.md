---
title: "[SOLVED] 2 network cards and still no wired connection but works with laptop!"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by PGScooter on 2008-11-09
Hi guys,

Networking is definitely not my strong point. I have tried two networking cards with my desktop (Dimension 2350) and still can't seem to get a WIRED connection. The first one is integrated on the motherboard and the second one I pulled from an old desktop. Should I try a newer card? I was under the impression that almost all ethernet cards work pretty well with ubuntu.

The problem first reared its head during the installation (when I only had the integrated port and had not yet tried the PCI card) when I received this error:
"Network autoconfiguration failed
Your network is probably not using the DHCP protocal. Alternatively, the DHCP server may be slow or some network hardware is not working properly"

I went on with the installation anyway. Then, my network showed up as DISABLED undo the sudo lshw -C Network command. I put an entry in my /etc/network/interfaces file and that removed the DISABLED. However, I could not connect.

I then put in a PCI Ethernet card. Again, it showed up as DISABLED, so I put another entry in my /etc/network/interfaces file and it showed up fine. But I could still not connect.

How can I tell if the problem is with my ethernet ports or not? I do not mind buying another card if I know that is a problem.

I am trying to connect to an SBV5220 Comcast cable modem. I can connect through ethernet with my laptop on Xubuntu. That is why I don't understand what the problem is.

Is it bad to have an eth0 and an eth1? Should I disable one when experimenting with the other?

How can I use my laptop, which connects just fine, to get the information that I need to connect with the desktop. Do I need to put in the Gateway and all that junk? I didn't have to with my laptop, everything was automatic.

Note, this laptop is connected and has no problem, I want to use this information to connect with my desktop
```

laptop sudo ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:de:30:2c  
          inet addr:24.6.17.124  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::2a0:d1ff:fede:302c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5540033 (5.2 MB)  TX bytes:670519 (654.8 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4200 (4.1 KB)  TX bytes:4200 (4.1 KB)

```
laptop
```

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

```


----------------------------
here is the output from my desktop
```

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```


```

sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 78
       serial: 00:01:03:d5:28:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:11:ac:ec
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

```

```

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:11:ac:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:01:03:d5:28:f3  
          inet6 addr: fe80::201:3ff:fed5:28f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10051 errors:0 dropped:0 overruns:297 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:682874 (666.8 KB)  TX bytes:6412 (6.2 KB)
          Interrupt:17 Base address:0x8000 

eth1:avahi Link encap:Ethernet  HWaddr 00:01:03:d5:28:f3  
          inet addr:169.254.7.230  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18900 (18.4 KB)  TX bytes:18900 (18.4 KB)

```

```

sudo /etc/init.d/n
networking     nvidia-kernel  
 * Reconfiguring network interfaces...                                    There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:db:11:ac:ec
Sending on   LPF/eth0/00:0b:db:11:ac:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:01:03:d5:28:f3
Sending on   LPF/eth1/00:01:03:d5:28:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```


I would really appreciate some help on this. Thank you!

---

### Post by PGScooter on 2008-11-10
bump

---

### Post by PGScooter on 2008-11-10
bump

---

### Post by lswb on 2008-11-10
Some comcast cable modems look for a specific MAC address (ethernet hardware address) and will not assign an ip address to others. Is the laptop the original system you used when you frist got comcast internet? 

It is easy to spoof the mac address though. Try this on your desktop while connected to the cable modem.I have copied the ethernet hardware address from your laptop that you posted. If it is different, substitute the real one. Also use the correct interface name if it is different from eth0.

On the desktop system, run this command in a terminal

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:a0:d1:de:30:2c
sudo ifconfig eth0 up
sudo dhclient eth0

If you connect, you can add the ethernet hw address to your /etc/network/interfaces file like this:

auto eth0
hwaddress ether 00:a0:d1:de:30:2c
iface eth0 inet dhcp 

You probably should check the man pages for /etc/network/interfaces to be sure, but I believe that is the correct syntax.

If you use Network Manager be aware that it does not play well with /etc/network/interfaces. However, on a desktop system that is always connected to the same network, you don't really need Network Manager.

---

### Post by PGScooter on 2008-11-11
Hi lswp, thank you for the reply!

well, it didn't work- still no DHCPOFFERS received.

But at least your code worked as you though it did because after all of that I did another ```
sudo ifconfig
``` and the HWaddress showed the new one.

Any other ideas? What is eth0:avahi and eth1:avahi under ifconfig? Is their presence a problem?

thanks

---

### Post by lswb on 2008-11-11
The avahi is a service that will self-assign ip addresses to a system in the absence of any other network configuration like dhcp, and also allows devices like network printers to be automatically configured if they also support it. It shouldn't cause any problems.

Other ideas? well, make sure you don't have any firewall rules running that might interfere with the connection. If you have ever configured a firewall on the desktop, temporarily disable it until the connection is up and running.

I would first try setting up the desktop exactly like the laptop, including the /etc/network/interfaces file. Then run the sudo ifconfig command to set the ethernet hardware address to the same as the laptop, and use whatever method the laptop uses to connect to the cable modem. If that doesn't work you can try progressing to other methods.

If you want to set up the desktop to connect with the /etc/network/interfaces file, it is probably best to disable Network Manager. THe commands to do so are

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

and to restart run the same command line but replace "stop" with "start"

You might searching google as well as this forum for something like "linux comcast cable internet" or something similar. Good luck.

---

### Post by PGScooter on 2008-11-12
thanks lswb,

It's a clean install of ubuntu, so only the default firewall if there is one. I already installed Network Manager, but installed Wicd, cause that's what I use to connect on my laptop.

I'll do some google research. If I find the solution I will be sure to post back here.

Thanks for your help!

---

### Post by PGScooter on 2009-01-07
I realised that I forgot to post back here. It ended up that the network cards were fine and that it was indeed the router as lswb suggested. After turning the router off (disconnecting all telephone, power, and cable to it), and then turning it on, it worked fine with the new computer. However, whenever I want to switch I have to do that. I wonder why it didn't work by spoofing the mac. In any case, thanks for the help.

---


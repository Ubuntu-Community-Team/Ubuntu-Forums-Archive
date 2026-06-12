---
title: "Configuring network interface fails at boot (seems dhcp related)"
date: 2005-08-29
forum: Networking &amp; Wireless
---

### Post by tristure on 2005-08-29
Hi,

I'm using hoary, and everything worked very well until yesterday...

Here's the system I use :
I have an onboard Lan card which I don't use, because I never managed to make it work. Anyway it's seen by the system and called eth0.

I have a Realtek PCI lan card, which is what I use, at eth1.

I have a wireless RT2500 card, which I don't use right now.

Yesterday, I tried to configure my wireless card, following the rt2500 howto on the ubuntu wiki.

I really don't know why, but this changed "something somewhere" (warning : noob inside ;-) ), and when rebooting, my eth1 network is not configured correctly.

After boot, if I type "dhclient eth1", the network works, though, but it's very odd : it used to work automatically, without any intervention from me!

Here's the output I get from various commands :

> tristan@dhcp-296-4694:~$ ifconfig eth1
eth1      Lien encap:Ethernet  HWaddr 00:40:F4:1D:C7:C8
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:16 Adresse de base:0xc400 

sudo route gives me blank output before i run dhclient, and after that it returns :

> tristan@dhcp-296-4694:~$ sudo route
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
81.66.134.0     *               255.255.254.0   U     0      0        0 eth1
default         gw.net81-66-134 0.0.0.0         UG    0      0        0 eth1 

> tristan@dhcp-296-4694:~$ cat /etc/resolv.conf
nameserver 212.198.2.51
nameserver 212.198.0.91 

And dhclient returns the following output :
> tristan@dhcp-296-4694:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:40:f4:1d:c7:c8
Sending on   LPF/eth1/00:40:f4:1d:c7:c8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 85.171.90.4
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 85.171.90.4
bound to 81.66.134.46 -- renewal in 7840 seconds. 

Any ideas about what went wrong and how to solve this?

Thanks a lot for your help!!

---

### Post by s_p_a_r_k_y on 2005-08-30
try editing /etc/network/interfaces and seting eth1 to dhcp and auto, here's mine

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
     script grep
     map eth0

# The primary network interface

iface eth1 inet dhcp
wireless-essid SOMEESSID
wireless-key XXXXXXXXXXXXPOO
auto eth1

---

### Post by tristure on 2005-08-30
I tried this and it still doesn't work. Here's my /etc/network/interfaces :

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
iface ra0 inet dhcp
iface eth0 inet
auto eth1


Any other idea?

---

### Post by s_p_a_r_k_y on 2005-08-31
your having trouble with the wireless card, no? Mine has the essid and key in the /etc/network/interfaces file so that upon boot it can plug those values in. Maybe i'm not understanding the problem correctly

---

### Post by tristure on 2005-08-31
Well, actually, I removed every reference to ra0 and eth0 in the file, and now it works...

I can't understand why it does now and didn't before. but well, my network problem is solved.

Now I still have to configure my wifi card... So I guess i have some more work to do...

thanks for your help!

---


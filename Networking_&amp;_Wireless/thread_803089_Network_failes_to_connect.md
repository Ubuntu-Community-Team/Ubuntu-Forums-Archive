---
title: "Network failes to connect"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by remush on 2008-05-22
I have installed xubuntu onto an older computer and it will not connect to my router, which works in dhcp mode. My laptop works fine of the same network cable.

The interface is called eth0 but when I do ifconfig I do not get an ip address.

Any suggestions would be helpful.

---

### Post by Paris Heng on 2008-05-22
> **remush said:**
> I have installed xubuntu onto an older computer and **[COLOR="Red"]it will not connect to my router[/COLOR]**, which works in dhcp mode. My laptop works fine of the same network cable.

The interface is called eth0 but when I do ifconfig I do not get an ip address.

Any suggestions would be helpful.

dear, which problems of PC you facing, new or old, old PC you stated "will not connect", I can not comprehend your problems. Please give more details again.

---

### Post by Peter09 on 2008-05-22
Check in network manager that you have a DHCP connection configured.

PC

---

### Post by ddemetrios5 on 2008-05-22
Hi

I have a similar problem i installed ubuntu 7.10 it worked ok network ok then i installed vlc restarted and now i cannot get a network and no internet

---

### Post by Peter09 on 2008-05-22
Post the results of ifconf and also the contents of /etc/network/interfaces

PC

---

### Post by remush on 2008-05-22
Steps taken to change network settings under Xubuntu 8.04

---------------------------0---------
ifconfig output before making changes
-----0-------------------------------
eth0      Link encap:Ethernet  HWaddr 00:60:67:78:d6:e0  
          inet6 addr: fe80::260:67ff:fe78:d6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8342 (8.1 KB)  TX bytes:6052 (5.9 KB)
          Interrupt:11 Base address:0x7800 

eth0:avahi Link encap:Ethernet  HWaddr 00:60:67:78:d6:e0  
          inet addr:169.254.10.79  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x7800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1192 (1.1 KB)  TX bytes:1192 (1.1 KB)


------------------------0--------------------------------
Making Changes and how I did it and what I saw
---------------0--------------------0--------------------

Applications > System > Network
Unlock

Under Connections Tab it says
Wired connection
Roaming mode enabled
and
Point to point connection
This network interface is not configured.

Under General Tab it says
Host name : ubuntu1
Domain name : 

Under DNS Tab it says
DNS Servers :
and
Search Domains :

Under Hosts Tab it says
127.0.0.1	localhost
127.0.0.1	ubuntu1
::1	ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
ff02::3	ip6-allhosts

So back to the Connections Tab I click on Wired connection and then the Properties button
I untick Enable roaming mode and then change the Configuration to Automatic Configuration(DHCP)
And Click the ok button

This window appears
Network Settings
Changing interface configuration

And then goes away after about 30 seconds

------------------------------------------------
ifconfig output after making these changes
------------------------------------------------

eth0      Link encap:Ethernet  HWaddr 00:60:67:78:d6:e0  
          inet6 addr: fe80::260:67ff:fe78:d6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16154 (15.7 KB)  TX bytes:8886 (8.6 KB)
          Interrupt:11 Base address:0x7800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4992 (4.8 KB)  TX bytes:4992 (4.8 KB)

--------------------------------------------------------------------
contents of the /etc/network/interfaces file
---------------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

---------------------------------------------------------------------

I hope the information I have provided was useful

---

### Post by remush on 2008-05-23
Here are the network card details

RTL8139B

---


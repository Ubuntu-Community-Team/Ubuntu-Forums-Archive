---
title: "Problems Setting Up Basic IPv6 Communication"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by matt3e18 on 2008-09-10
Hi All,

I've been using Ubuntu for a couple of years now, but have just recently been trying to get some basic IPv6 connectivity working on a private network with just a couple of PC's.  

My initial setup is two Ubuntu 8.04 PC's connected to a hub.  I ultimately want to do some basic socket programming for UDP communication between these two PC's.  I'm having a little bit of trouble configuring the systems, though.

Since I am just setting up communication between 2 PC's on a local (private) network, and won't be using internet connectivity, I was thinking to use statically configured global IPv6 addresses.  (but, I am not sure if this is the correct decision).  The IP addressing scheme I would like to use is:

PC1 IP Addr: dead:beef:dead:beef:18:8bff:fe72:fd41
PC2 IP Addr: dead:beef:dead:beef:12:3fff:fe01:2327

As a first step, I've configured PC1 and am trying to capture some IPv6 Ping requests (using ping6) headed towards PC2.  My configuration in /etc/network/interfaces is:

----
# Loopback interface
auto lo
iface lo inet loopback

auto eth0

# IPv6 for etho
iface eth0 inet6 static
address dead:beef:dead:beef:18:8bff:fe72:fd41
netmask 128

# IPv6 for eth0
iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
----

It looks like this configuration is taking effect; the output of ifconfig is:

---
eth0      Link encap:Ethernet  HWaddr 00:18:8b:72:fd:41  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: dead:beef:dead:beef:18:8bff:fe72:fd41/128 Scope:Global
          inet6 addr: fe80::218:8bff:fe72:fd41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10817 (10.5 KB)  TX bytes:8839 (8.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95337 (93.1 KB)  TX bytes:95337 (93.1 KB)
---

But, there must be something incorrect with this configuration, because ping6 gives me this:

---
matt@matt-desktop:~$ ping6 dead:beef:dead:beef:12:3fff:fe01:2327
connect: Network is unreachable
---

I've looked through a couple of FAQ's and tutorials on Linux with IPv6 (the 'Linux IPv6 HowTo' was particularly helpful), but I fear I've hit a dead end of reading through existing documentation.

Has anyone set up a similar small network successfully?  Or, is it possible that someone can have a look at my configuration and recommend a change to try?

Thanks!!!

Matt

---

### Post by matt3e18 on 2008-09-11
Oops!! this error was caused by the "netmask 128" being set.

I suppose having a 128 bit netmask with no default gateway set is not the best configuration if you actually want to send IPv6 traffic somewhere :)

---


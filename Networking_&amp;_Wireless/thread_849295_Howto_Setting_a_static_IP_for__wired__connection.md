---
title: "Howto?: Setting a static IP for _wired_ connection"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by minuxx on 2008-07-04
Hi!

I am sorry to bother you with this rather silly questions but I cant help than to ask.

I would like to set a static IP on my eth0 which is a wired connection. I already was supplied with a dynamic IP by my local dhcp server.
It looks like this.

bob@hostname:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:a7:3c:2b
          inet addr:172.30.241.245  Bcast:172.30.241.255  Mask:255.255.254.0
          inet6 addr: fe80::21d:7dff:fea7:3c2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:462886 (452.0 KB)  TX bytes:91548 (89.4 KB)
          Interrupt:251 Base address:0x8000

bob@hostname:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.240.0    0.0.0.0         255.255.254.0   U     0      0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         172.30.240.1    0.0.0.0         UG    100    0        0 eth0

I would like to set the already given IP as static and use the above route. Whats the command to manually set this up?

Thank you!

---

### Post by dardack on 2008-07-04
I find the easiest way is to go into your router and use DHCP Reservation, it assigns the same IP address to specific Mac Addresses.  If your router doesn't do that you have to edit /etc/network/interfaces
(From the Security sticky in this forum):
The content should look similar to this:
Quote:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
3. Now replace the last 2 lines with the following using your own network settings (the sequence in which the lines appear is crucial):
Quote:
auto eth0
iface eth0 inet static
address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0

That should do it, be warned that when I did this on my file server it broke Samba (my post can be found), i fixed this with DHCP Reservation with my router.

---

### Post by minuxx on 2008-07-04
Lets assume my rig is working in an enviroment I dont habe any effect on.
Lets assume as well that I am told to use a specific IP.
That IP and route is shown in my first post.
So how can I manually assign that ?

---

### Post by minuxx on 2008-07-04
*bumb*

---

### Post by kevdog on 2008-07-04
Thanks for doing some reading or just trying things.  Really lazy. 

auto eth0
iface eth0 inet static
address 172.30.241.245
netmask 255.255.254.0
gateway 172.30.240.1

---

### Post by minuxx on 2008-07-04
Thank you!

---


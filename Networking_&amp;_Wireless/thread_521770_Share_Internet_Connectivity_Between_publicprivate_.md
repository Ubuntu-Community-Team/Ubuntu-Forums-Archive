---
title: "Share Internet Connectivity Between public/private Interfaces"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by giganet on 2007-08-09
I have an Internet Connectivity issue going on with a new server I am working on...
Ubuntu 6.06
Shorewall 3.0.4

5 ethernet ports *eth0, eth1, eth2, eth3, eth4* -
 (**eth0 public**) 
(**eth2 private**)
(_eth1, eth3, eth4 UN-CONFIGURED_)

[COLOR="Blue"]eth0 IP 72.169.xxx.xxx Default Gateway Device[/COLOR]
[COLOR="Red"]eth2  IP 10.0.0.225 Default Gateway = 72.169.xxx.xxx[/COLOR]

**The Ethernet connected PC uses the following connection settings**- (connected PC is MS XP)
[COLOR="DarkGreen"]IP 10.0.0.103[/COLOR]
[COLOR="Green"]Subnet Mask: 255.0.0.0[/COLOR]
[COLOR="SeaGreen"]Default Gateway: 72.169.152.211[/COLOR]

Presently I have the server accessible from the public side into **HTTP, HTTPS, SFTP, SSH** services provided by the server.
From the server terminal you can ping the outside world VIA *eth0*, however, from any ethernet (**STRAIGHTTHROUGH**) connected
computer from *eth2* of the server I can ping both public(*eth0*) and private(*eth2*) interfaces on the server but am unable to ping the world.
Likewise while on any ethernet connected computer on *eth2* I am able to gain access to **HTTP, HTTPS, SFTP, SSH** services
provided by the server.

If anyone has some suggestions I would greatly appreciate them...:KS

'**mailman@bender:~$ ifconfig**'
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:2E:F8:E7
          inet addr:72.169.xxx.xxx  Bcast:72.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20a:e6ff:fe2e:f8e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2352454 (2.2 MiB)  TX bytes:1952125 (1.8 MiB)
          Interrupt:11 Base address:0xd400

eth1      Link encap:Ethernet  HWaddr 00:00:24:C4:5E:A4
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000

eth2      Link encap:Ethernet  HWaddr 00:00:24:C4:5E:A5
          inet addr:10.0.0.225  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::200:24ff:fec4:5ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4375109 (4.1 MiB)  TX bytes:1467533 (1.3 MiB)
          Interrupt:11 Base address:0x6000

eth3      Link encap:Ethernet  HWaddr 00:00:24:C4:5E:A6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000

eth4      Link encap:Ethernet  HWaddr 00:00:24:C4:5E:A7
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33248 (32.4 KiB)  TX bytes:33248 (32.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


'**mailman@bender:~$ iwconfig**'
lo        no wireless extensions.

eth1      no wireless extensions.

eth2      no wireless extensions.

eth3      no wireless extensions.

eth4      no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


'**mailman@bender:~$ cat /etc/network/interfaces**'
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 72.169.xxx.xxx
netmask 255.0.0.0
gateway 72.169.xxx.xxx

auto eth0

iface eth2 inet static
address 10.0.0.225
netmask 255.0.0.0
gateway 10.0.0.225

auto eth2


'**mailman@bender:~$ cat /etc/resolv.conf**'
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 208.67.222.222
nameserver 63.226.12.96
nameserver 209.48.2.11


'**mailman@bender:~$ ip route**'
72.0.0.0/8 dev eth0  proto kernel  scope link  src 72.169.xxx.xxx
10.0.0.0/8 dev eth2  proto kernel  scope link  src 10.0.0.225
default via 72.169.xxx.xxx dev eth0
default via 10.0.0.225 dev eth2  scope link


'**mailman@bender:~$ ip link**'
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:00:24:c4:5e:a4 brd ff:ff:ff:ff:ff:ff
3: eth2: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:00:24:c4:5e:a5 brd ff:ff:ff:ff:ff:ff
4: eth3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:00:24:c4:5e:a6 brd ff:ff:ff:ff:ff:ff
5: eth4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:00:24:c4:5e:a7 brd ff:ff:ff:ff:ff:ff
6: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0a:e6:2e:f8:e7 brd ff:ff:ff:ff:ff:ff
7: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0


'**mailman@bender:~$ ip addr**'
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:00:24:c4:5e:a4 brd ff:ff:ff:ff:ff:ff
3: eth2: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:00:24:c4:5e:a5 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.225/8 brd 10.255.255.255 scope global eth2
    inet6 fe80::200:24ff:fec4:5ea5/64 scope link
       valid_lft forever preferred_lft forever
4: eth3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:00:24:c4:5e:a6 brd ff:ff:ff:ff:ff:ff
5: eth4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:00:24:c4:5e:a7 brd ff:ff:ff:ff:ff:ff
6: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0a:e6:2e:f8:e7 brd ff:ff:ff:ff:ff:ff
    inet 72.169.xxx.xxx/8 brd 72.255.255.255 scope global eth0
    inet6 fe80::20a:e6ff:fe2e:f8e7/64 scope link
       valid_lft forever preferred_lft forever
7: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0


**Thanking you in advance for your help and time...** (;-}'

Regard

---

### Post by giganet on 2007-08-10
Bump-----

This is insane!
When I had only a single interface config all worked fine, but now with two interfaces I can't manage to SNAT or anything for that fact to manage to provide an internet connection to eth2 from eth0...


Come on someone--- throw the dog a bone here folks! [-o<

Thank you

---

### Post by Rick Z on 2008-02-01
Can you provide me the /etc/shorewall/policy & /etc/shorewall/rules?  I believe you have to enable the pinging in /etc/shorewall/rules.

---


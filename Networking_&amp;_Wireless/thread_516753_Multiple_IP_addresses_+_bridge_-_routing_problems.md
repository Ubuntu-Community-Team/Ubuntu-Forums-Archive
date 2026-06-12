---
title: "Multiple IP addresses + bridge - routing problems"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by myak on 2007-08-03
Hello,

First of all, let me introduce myself as it is my first post on Ubuntu Forums. I am Ubuntu user for.. well, 2 days now. My previous experiences include Gentoo (been a total fanboy for a long time) and openSUSE not to mention my earlier adventures with Linux which began with RedHat 5 or something and failed miserably at that time. Right now I am using Kubuntu Gutsy.

Now up to the interesting part. Let me note that I am almost a complete noob in networking. My current network setup is as follows: eth0 is configured with public IP address and there's an alias, eth0:0, configured to use a private address. These two interfaces (well, one and an alias) use different netmasks and gateways. My /etc/network/interfaces looks like that:

***Note:** Public IP details in the whole post have been changed obviously ;)*
```
**# /etc/network/interfaces.nobridge**

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
    address 252.153.21.232
    netmask 255.255.255.224
    gateway 252.153.21.225

auto eth0:0
iface eth0:0 inet static
    address 192.168.1.91
    netmask 255.255.254.0
    gateway 192.168.0.1
```
*Note: Both gateways provide access to the Internet. Somehow, Ubuntu is clever enough to use the public one, which is what I want.*

My ISP provides me with one more public IP address, namely 252.153.21.233. I would like to use it in my Windows 2003 Server Enterprise Edition (I feel like I need to explain - I need it to run Sharepoint for my thesis ;)  running in VirtualBox so both the host and guest computer are visible to the public. So what I need is a bridge. Here's the /etc/network/interfaces used for that:
```
**# /etc/network/interfaces.bridge**

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
    address 252.153.21.232
    netmask 255.255.255.224
    gateway 252.153.21.225

auto eth0:0
iface eth0:0 inet static
    address 192.168.1.91
    netmask 255.255.254.0
    gateway 192.168.0.1

auto tap0
iface tap0 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down
    tunctl_user myak
    uml_proxy_arp 252.153.21.233
    uml_proxy_ether eth0

auto br0
iface br0 inet static
    address 252.153.21.232
    netmask 255.255.255.224
    gateway 252.153.21.225
    bridge_ports eth0 tap0
    bridge_maxwait 0
```

Ok. Now, almost everything works fine after setting tap0 as host interface in VirtualBox. Host computer is visible as 252.153.21.232 and guest computer as 252.153.21.233. But, private network is unreachable. Previously, with the interfaces.nobridge, I could successfully ping 192.168.0.3 and connect to it using smbclient. With interfaces.bridge, I get *Destination Host Unreachable* and, obviously, can't connect to SMB shares.

Route table for **interfaces.bridge**:
```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
marcin2.blablab *               255.255.255.255 UH    0      0        0 tap0
252.153.21.224  *               255.255.255.224 U     0      0        0 br0
252.153.21.224  *               255.255.255.224 U     0      0        0 eth0
192.168.0.0     *               255.255.254.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         gate3.blablabl. 0.0.0.0         UG    0      0        0 br0
default         gate3.blablabl. 0.0.0.0         UG    0      0        0 eth0
```

Route table for **interfaces.nobridge**:
```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
252.153.21.224  *               255.255.255.224 U     0      0        0 eth0
192.168.0.0     *               255.255.254.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
default         gate3.blablabl. 0.0.0.0         UG    0      0        0 eth0
```

Well, apart from br0 routes, the only difference is that there is no default gateway specified as 192.168.0.1 when using interfaces.bridge. I don't know why it wasn't automagically added to routing table even though eth0:0 configuration looks the same in both files, but let's run:
```
route add default gw 192.168.0.1
```
I would expect everything to work as it worked before. Nope. Same problem - Destination Host Unreachable when pinging 192.168.0.3.

Sorry for the long post but the issue is not that trivial, at least it doesn't seem like so to me and I can't figure it out. So if there's someone experienced with networking, routing, whatever, please share any suggestions. Also, if you don't understand something (sorry for my English), feel free to ask for explanation and/or any additional information I can provide (logs, configuration, whatever). I've been trying to solve it by myself for many hours and failed :(

---

### Post by MatthewAPeters on 2007-08-05
I am having similar issues - at least I think I am.  My VirtualBox-windows session can access the network nicely if I set the Virtualbox network interface to use NAT.  My  attempts to bridge in Feisty have failed - even caused windows not to boot in Virtualbox.  I thought the VirtualBox documentation was pretty useful for setting up the bridge, until the bridge failed.  Is there any chance that Avahi has something to do with this?

Edit

Ah, the joys of Google!

[http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)   This worked for me on Feisty.

---

### Post by myak on 2007-08-05
Well, my bridged connection works. Both guest and host can access the net, using unique public addresses. My problem is that I cannot access my private network (on alias eth0:0).

---

### Post by combatwombat_nz on 2007-08-10
try:
# /etc/network/interfaces.bridge

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
    address 252.153.21.232
    netmask 255.255.255.224
    gateway 252.153.21.225

auto eth0:0
iface eth0:0 inet static
    address 192.168.1.91
    netmask 255.255.254.0
    gateway 192.168.0.1

auto tap0
iface tap0 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down
    tunctl_user myak
    uml_proxy_arp 252.153.21.233
    uml_proxy_ether eth0:0

auto br0
iface br0 inet static
    address 252.153.21.232
    netmask 255.255.255.224
    gateway 252.153.21.225
    bridge_ports eth0:0 tap0
    bridge_maxwait 0


As it appears that you were trying to hook br0/tap0 to eth0, not eth0:0.

---

### Post by Hero of Time on 2008-01-21
I have the same 'problem'. However, I did what combatwombat said. I have my bridge with IP 1, and set my lan with IP 2, but somehow, when I use ifconfig to show my ip config, I don't see an ip address on the interface. This is what I have for the interfaces file:
```
auto brdg
iface brdg inet static
bridge_ports lan vbox0 vbox1
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto lan
iface lan inet static
address 192.168.0.1
netmask 255.255.255.0
```
So, as it is now, I can't connect trought the 0.1 address. If I manually bring down lan, and then up again, it does get the correct address, but I can't connect trough it to anywere.

... Long time later...

I somehow got something working. I added the following:
```
auto lan
iface lan inet manual

auto lan:0
iface lan:0 inet manual
address 192.168.0.1
netmask 255.255.255.0
```
I left the bridge interface as it was, I only added and alias for the lan interface. This somehow works. Samba is with some hickups, but functional. Somewhat.

---

### Post by karyonix on 2008-01-23
Don't assign IPs directly to network interfaces which is parts of a network bridge.  You can assign more IPs to aliases of the bridge itself. 

My /etc/network/interfaces looks like this.
```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0
iface tap0 inet manual
  tunctl_user myusername

auto br0
iface br0 inet dhcp
  bridge_ports eth0 tap0
  bridge_maxwait 0

auto br0:1
iface br0:1 inet static
  address 10.0.0.99
  netmask 255.0.0.0
  gateway 10.0.0.9
```
eth0 will automatically start with br0.  There is no need for 'auto eth0'.  But the script for starting network bridge does not create TUN/TAP interface automatically, so I have to put 'tap0' in an 'auto' statement before 'br0'.

This might work for myak's problem.
```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0
iface tap0 inet manual
    tunctl_user myak

auto br0
iface br0 inet static
    bridge_ports eth0 tap0
    bridge_maxwait 0
    address 252.153.21.232
    netmask 255.255.255.224
    gateway 252.153.21.225

auto br0:1
iface br0:1 inet static
    address 192.168.1.91
    netmask 255.255.254.0
    gateway 192.168.0.1
```

This might work for Hero of Time's network.
```
iface lan inet manual

auto brdg
iface brdg inet static
bridge_ports lan vbox0 vbox1
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto brdg:1
iface brdg:1 inet static
address 192.168.0.1
netmask 255.255.255.0
```

---


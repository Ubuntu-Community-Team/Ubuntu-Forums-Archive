---
title: "masquarade (connection sharing) help NEEDE BAD"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by InfernalPenguin on 2007-02-23
ok heres the deal. i have a, lets call it BOX 1 (Kubuntu Dapper) with two NICs that is connected to the net ip 192.168.21.51(dhcp)  second NIC ip 192.168.1.1(manually). now that second NIC is connected to lets call it BOX 2 (damn small linux) via crossover cable. what i need to do is share connection between those two boxes
heres my /etc/network/interfaces from box 1

[COLOR="Red"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface connected to the lan

auto eth1

iface eth1 inet static

     address 192.168.1.1
      
      netmask 255.255.255.0
	    
      network 192.168.1.0
      		  
      broadcast 192.168.1.255
			
      up sysctl -w net.ipv4.ip_forward=1
			      
      up iptables --table nat --insert POSTROUTING --jump MASQUERADE
      gateway 192.168.1.254[/COLOR]

if i made a mistake here please do corect me.
my question is how do i setup that second box with Damn Small Linux on it so that it has acces to internet.or maybe i already made a mistake here. i have no idea. all i know is that i tried all kinds of things, all types of configurations on Box 2 and nothing. please help. explain this to me like im 5 years old. what should my /../interfaces file on Box 2 look like. HELP!

---

### Post by koenn on 2007-02-23
>  up sysctl -w net.ipv4.ip_forward=1

up iptables --table nat --insert POSTROUTING --jump MASQUERADE
if you 've put this in /etc/network/interfaces ... wel, it doesn't belong there. 

Read this first:
[http://ubuntuforums.org/showpost.php?p=2135536&postcount=2](http://ubuntuforums.org/showpost.php?p=2135536&postcount=2)

---


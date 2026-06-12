---
title: "Newbie Wifi Woes"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by updownleftright on 2007-01-22
Hi guys, i'm a total Linux noob, and i'm going round in circles with my 2 day old ubuntu 6.10 installation trying to get connected to the net. I've followed dozens of tutorials/guides/threads on the subject, and still can't get anywhere.

In Network Manager I have a Wireless connection showing up, but whenever I try and ping anything I get "Network Unreachable" (except 127.0.0.1, that works).

If I do a scan, I can see the network I want to connect to, but for some reason when I type in the ESSID and WEP key into the network manager it won't connect. It always spends a few seconds configuring the network when I change details (i've tried ascii and hex wep keys), so I assume that was it connecting, but obviously not.

Is there any easy way of telling at what point things are failing in linux? I am assuming that my drivers are loaded, the card is on and configured, and the network detected, so the failure must be somewhere around the connection/autherisation point, am I right?

I have 128 bit WEP on the router, and DHCP enabled, both of which I need to keep for other users of the access point. Oh, and the card is a Linksys / ADMTEK ADM8211 (rev11), if that helps.

Any ideas what's up? I'm tearing my hair out now! I love the feel of ubuntu so far, but this is making me want to go back to the relative comfort of XP :)

---

### Post by tribaal on 2007-01-22
Did you comment out your interface configuration in /etc/network/interface ?
The only two lines that shouldn't be commented are the two first ones (the ones about loopback).

That sounds just like the problem I had, which was related to thoses uncommented lines.

Hope this helps any... :)

- trib'

---

### Post by updownleftright on 2007-01-22
I havn't messed with any config files yet, i've only used the point and click interfaces and a few tentative steps into terminal.

I'll have a look at that file shortly!

---

### Post by tacm on 2007-01-22
> **tribaal said:**
> Did you comment out your interface configuration in /etc/network/interface ?
The only two lines that shouldn't be commented are the two first ones (the ones about loopback).

That sounds just like the problem I had, which was related to thoses uncommented lines.

Hope this helps any... :)

- trib'Im having this same problem can you elaborate on the steps to acoplish this please

---

### Post by updownleftright on 2007-01-22
I've finally got connected. It turns out the problem was with my WEP encryption. I turned it off on the router, and now i'm connected fine. Hopefully I can turn it back on again at some point, but at least i'm back online!

---

### Post by Cyberbayne on 2007-01-22
Grats! Could you post your iwconfig, please?

---

### Post by Christopher H. on 2007-04-01
I second the request for posting the relevant /etc/network/interfaces listing

System with a SMC2635W "red" i.e. adm8211 wireless card
Using the 6.01 live distro and the graphical network configuration tool
it automatically finds a couple of wireless ESSIDs and I can select mine 
and give it the WEP and evergything works well as far as I can tell.

However in my installation of "Ubuntu 6.10 - the Edgy Eft"
no such luck. - Doubt that the problem is a card driver if the previous 
incarnation (Dapper) gets things going just fine.
To me it looks like /etc/network/interfaces is a bit garbled.
I gave the graphical interface tool two locations (at home and the office
i.e. one with wireless and dhcp and the other with a fixed address etc. 
and a wired ethernet connection.

For the wireless connection the light on the card flashes busily but 
doesn´t give me any ESSID to choose from and even if I give it the ESSID
and WEP it just says that it is activating the network interface but
doesn´t produce the goods.

Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006

Booted from live distro: contents of /etc/network/interface
_________________________________

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid aaaaaaaa
wireless-key nnnnnnnnnn

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
_________________________________

 Ubuntu 6.10 - the Edgy Eft  - released in October 2006.
				
 Booted via diskette grub menu (dual boot without touching MBR of hard disk):
 contents of /etc/network/interface
_________________________________

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid aaaaaaaa
wireless-key nnnnnnnn

auto eth1

iface eth0 inet static
address 192.168.107.105
netmask 255.255.255.0
gateway 192.168.107.253

_____________________________

Having done a little RTFM but being new to Linux although I have done RTFM on OS´s 
such as OS8 (Digital Equipment PDP8 with 4k solid state memory - when core memory 
was common), PrimeOS, VMS, DOS: 
I think that the file /etc/network/interfaces should read as follows:
_____________________________

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet dhcp
wireless-essid aaaaaaaa
wireless-key nnnnnnnnnn

auto eth1

iface eth1 inet static
address 192.168.107.105
netmask 255.255.255.0
gateway 192.168.107.253
_____________________________
Can anyone shoot this down? and tell me the clanger that I´m about to drop!

---


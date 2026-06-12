---
title: "IP address change"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by lkstamenov on 2007-11-12
I have Gutsu Gibbon installed. Desktop Edition. The problem is everytime I restart the system the IP assoiciated with Apache, PostFix and FTP servers is changing. First one was 192.168.0.3 and then it become .2, and so on. Now is 192.168.0.13 

I have LAMP, Postfix servers installed and I need a permanent IP address.

How can I fix that ?

---

### Post by ddrichardson on 2007-11-12
What's /etc/network/interfaces look like?

---

### Post by lkstamenov on 2007-11-12
> **ddrichardson said:**
> What's /etc/network/interfaces look like?
 I got this:

auto lo
iface lo inet loopback

Nothing more

---

### Post by ddrichardson on 2007-11-12
You can specify static addresses in there too, there's a guide [here]("http://www.sematopia.com/?p=50").

---

### Post by lkstamenov on 2007-11-13
I tried. Nothing changed. Even after restart. Any other ideas ?

---

### Post by lkstamenov on 2007-11-13
I found it. It is

System->Administration->Network->Connection

from there I put static IP address. Unfortunately the roaming option is ON by default so in every session I must switch it OFF and put static IP. Now /etc/network/interface look like:

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
iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.1

iface eth25 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth25

iface eth26 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth26

iface eth27 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth27


Thanks for the help

---


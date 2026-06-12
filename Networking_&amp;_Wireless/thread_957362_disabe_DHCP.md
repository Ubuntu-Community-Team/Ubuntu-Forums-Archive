---
title: "disabe DHCP"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by kosc on 2008-10-24
Hi

I have ubuntu server 8.04.1 LTS and 2 NICs, since I'm newbie can someone clear this out for me :)

eth0 is connected to LAN
eth1 is connected to another PC.

/etc/networks/intefaces:
[COLOR="DarkRed"]auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1

#eth1
auto eth1
iface eth1 inet static
 address 192.168.5.1
 netmask 255.255.255.0
 network 192.168.5.0
 broadcast 192.168.5.255
[/COLOR]

after sudo /etc/init.d/network restart
everything is OK, but 30min after eth0 change address from DHCP to 192.168.1.182 ???

/var/log/syslog:[COLOR="DarkRed"]
Oct 24 12:15:27 router dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Oct 24 12:15:27 router dhclient: DHCPOFFER of 192.168.1.182 from 192.168.1.1
Oct 24 12:15:27 router dhclient: DHCPREQUEST of 192.168.1.182 on eth0 to 255.255.255.255 port 67
Oct 24 12:15:27 router dhclient: DHCPACK of 192.168.1.182 from 192.168.1.1
Oct 24 12:15:27 router dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Oct 24 12:15:27 router dhclient: bound to 192.168.1.182 -- renewal in 1776 seconds.[/COLOR]

Why DHClient fetches address?
line in /etc/network/interfaces [COLOR="DarkRed"]iface eth0 inet static[/COLOR] 
tells that address is static (or not?)

I "fix" this modifying /etc/dhcp3/dhclient.conf
from
[COLOR="DarkRed"]request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;[/COLOR]
to
[COLOR="DarkRed"]# request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;[/COLOR]

---

### Post by Iowan on 2008-10-24
In a word (OK, 2 words), it shouldn't. I don't know why dhclient decides to run uninvited, but your "fix" seems quicker/easier than what I'd have suggested: finding the appropriate rcX.d file and changing, for instance, "S49" to "s49" to keep dhclient from starting.

[Here]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") is another article I just stumbled across that describes removing dhclient completely.

---

### Post by kosc on 2008-10-26
thanx

In short this is bug in dhclient/network scripts :)

I removed dhcp-client from ubuntu and now it works just fine :)

[COLOR="DarkRed"]sudo apt-get remove dhcp-client[/COLOR]

---


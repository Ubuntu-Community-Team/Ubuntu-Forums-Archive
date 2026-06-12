---
title: "I can't override the DNS-server from my ISP"
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by linusnilsson on 2015-09-27
Hi!

I have a LAN, which is served by an Ubuntu Server with dhcp-server (dhcpd), dns-server (bind9) etc...
I have set up the dns-server to serve my LAN with an internal domain, which works great. I have the dhcp-server to distribute the local dns-server to all the clients/hosts on the LAN and all those hosts are able to resolve the internal domain names. All clients get 192.168.0.1 as their dns-server. The dns-server is setup to resolve the internal domain and to cache all other by using external dns-servers.

Here's my problem... The dns-server has 2 network interfaces, one for the internet-connection (WAN), and one for the LAN. The problem is that the dns-server itself, by default, uses the external dns-servers that it gets from my ISP. Because of that, my dns-server can't resolve my internal domain names, since it doesn't ask itself first but rather uses my ISP's dns-server, which of course has no clue about my internal domain, as that's how I've configured it.

I have tried adding
```
prepend domain-name-servers 192.168.0.1;
``` and 
```
supersede domain-name-servers 192.168.0.1;
``` in the dhclient.conf for the WAN-interface.
I've also tried manually adding
```
auto eth0
iface eth0 inet dhcp
dns-nameservers 192.168.0.1
```
in /etc/network/interfaces but whatever I do, I still find the ISP's dns-servers in the top of /etc/resolv.conf. I could get my dns-server added below the ISP's dns-servers but I want it to be in the top so that my dns-server asks itself first, and then, if it fails, it can ask my ISP's dns-server.

Does anyone have any suggestions? :)

---

### Post by Doug S on 2015-09-27
Hi, and welcome to Ubuntu forums,

I have a setup similar to what you describe.

A couple of years ago, I used to use "prepend" in my /etc/dhcp/dhclient.conf file. My note to myself, in that file, from when I changed, says "# No, use /etc/default/bind9 to set the DNS".
I now force the dns via the options statement in my /etc/dhcp/dhcpd.conf file:```
...
# option definitions common to all supported networks...

default-lease-time 86400;
max-lease-time 93000;
option domain-name "smythies.com";
# option domain-name-servers 192.168.111.1, 75.154.133.68, 75.154.133.100;
option domain-name-servers 192.168.111.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.111.255;
option routers 192.168.111.1;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;
...

```Notice that I no longer bother using my ISP provided dns servers, if my server is down, then they cann't be accessed anyway and I have my dns using the root servers when they need to go upstream. (i.e. I have the forwarders area of /etc/bind/named.conf.options commented out.)

---

### Post by linusnilsson on 2015-09-28
I use that statement too and that's how I get my LAN-clients to use 192.168.0.1 (my DNS-server) as their primary dns-server.
The problem is that my dns-server (192.168.0.1) itself uses my ISP's dns-servers to resolve hostnames.

Let me try to describe a little better...
The LAN-clients use my dns-server (192.168.0.1) to resolve hostnames. They can resolve my local-domain hostnames since they ask my dns-server first.
My dns-server uses my ISP's dns-server to resolve hostnames. It can't resolve my local-domain hostnames since it asks my ISP's dns-server.
I use nslookup or dig, without specifying a dns-server, to resolve for instance [www.localdomain.test]("http://www.localdomain.test"). Doing this on any of the LAN-clients will be successful since they use 192.168.0.1 as their dns-server. Doing the same on the dns-server will fail since it doesn't ask itself first but instead asks my ISP's dns-server, since that's what it get from the dhcp-response from my ISP when it gets its IP-address.

---

### Post by linusnilsson on 2015-09-28
I think I actually have a solution. I just found a similar question on  askubuntu [http://askubuntu.com/questions/211757/how-do-i-set-a-static-dns-nameserver-address-on-ubuntu-server](http://askubuntu.com/questions/211757/how-do-i-set-a-static-dns-nameserver-address-on-ubuntu-server) and there was a guy who suggested that you could change the  interface-order of resolvconf and thereby make resolvconf add another  interface's dns-settings first. While experimenting with this I found  the easiest solution to be this:

Since I found out that the loopback interface's  settings are prioritized before ethernet interfaces, I just had to add  the dns-nameservers 192.168.0.1 to the loopback-interface in /etc/network/interfaces instead of adding it to eth0:

```

# The loopback network interface
auto lo
iface lo inet loopback
dns-nameservers 192.168.0.1

# The primary network interface (WAN-interface)
auto eth0
iface eth0 inet dhcp
#dns-nameservers 192.168.0.1

```

This way I get 192.168.0.1 loaded into resolv.conf before the ones it later gets from the ethernet-interfaces, problem solved! :)
So hard answer to find, but such an easy solution...

---

### Post by Doug S on 2015-09-28
Glad you got it figured out. Just for completeness, I do it a different way, that doesn't involve the /etc/network/interfaces file. I changed the /etc/default/bind9 file from this:```
# run resolvconf?
RESOLVCONF=[COLOR="#FF0000"]no[/COLOR]

# startup options for the server
OPTIONS="-u bind"
``` to this:```
# run resolvconf?
RESOLVCONF=[COLOR="#FF0000"]yes[/COLOR]

# startup options for the server
OPTIONS="-u bind"

```When I use the dns server itself to do a lookup, I get:```
doug@doug-64:~/config/etc/default$ [COLOR="#FF0000"]nslookup s10[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   s10.smythies.com
Address: 192.168.111.102

doug@doug-64:~/config/etc/default$
```

---

### Post by Doug S on 2016-02-02
Readers please note: The method I described in this thread worked fine on my 12.04 Ubuntu server. However, and for unknown reasons, it doesn't work on the 16.04 (development branch) Ubuntu server I am building. So I have gone back to the default /etc/default.bind9 file and done the /etc/network/interfaces file method mentioned by linusnilsson. My interfaces file:
```
# interfaces file for smythies.com 2016.01.30
#       attempt to set local DNS herein, as the method
#       used with the old 12.04 server no longer works.
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
pre-up /home/doug/init/doug_firewall
dns-nameservers 127.0.0.1

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp

# Local network interface (uses built in ethernet port)
auto enp2s0
iface enp2s0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```And an example local lookup:
```
doug@DOUG-64:~/config/etc/network$ [COLOR="#FF0000"]nslookup s10[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   s10.smythies.com
Address: 192.168.111.102

```

---


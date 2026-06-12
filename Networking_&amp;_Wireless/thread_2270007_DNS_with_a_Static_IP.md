---
title: "DNS with a Static IP"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by bruce-hyatt on 2015-03-19
I have an Ubuntu 14.04 server with a static IP number. It can find other computers, both on my LAN and on the WAN but only by IP number. It obviously needs to be able to find a DNS.

The [14.04 Server Guide - Networking page]("https://help.ubuntu.com/lts/serverguide/network-configuration.html") says to put a DNS-nameservers assignment in the /etc/network/interfaces file but the [Interfaces Manpage]("http://manpages.ubuntu.com/manpages/trusty/man5/interfaces.5.html") makes no mention of a DNS-nameservers variable. I don't have the server available to me right now but I'm pretty sure I added that variable to the interfaces file as described in the Server-Guide Networking-Configuration page last night but without success. I tried searching the forums for "/etc/network/interfaces" but it fails.

If anyone can point me in the right direction, I would greatly appreciate it.

- Bruce Hyatt

---

### Post by papibe on 2015-03-19
Hi bruce-hyatt.

The syntax is 'dns-nameservers' follow by the addresses. For example:
```
iface eth0 inet static
    address 192.168.1.139
    ...
    dns-nameservers 192.168.1.1 208.67.222.222
```
The details are on the 'resolverconf' man page:
```
man resolvconf
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by bruce-hyatt on 2015-03-19
I have that code in /etc/network/nameservers but it isn't working. I looked at the manpage for resolvconf and followed some of the links. It looks like a description of how daemons and scripts place network configurations into the /etc/resolv.conf file but I couldn't track down anything about setting IP numbers for DNS there.

I appreciate your help but I think I must be overlooking some other setting I made somewhere else.

---

### Post by papibe on 2015-03-19
That goes on your /etc/network/interfaces

EDIT: Also make sure your /etc/resolv.conf is a link not a file:
```
ls -l /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 May 19  2014 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```
Regards.

---

### Post by bruce-hyatt on 2015-03-19
I'm sorry, I meant /etc/network/interfaces and /etc/resolv.conf *is* a link.

---

### Post by bruce-hyatt on 2015-03-19
I restarted the server and it works now. It has to be either the way I was restarting the network services:

sudo /etc/init.d/networking restart

or, maybe, putting both DNSes and the gateway in /etc/network/interfaces.

Thanks very much for your help.

---

### Post by papibe on 2015-03-19
;)

---


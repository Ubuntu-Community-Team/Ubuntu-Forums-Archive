---
title: "Can't Ping My Network Name"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by IvDogg on 2008-05-10
Hi All,

So here's my problem.

I have a small peer to peer network, 3 Win XP, 2 (Hardy) Ubuntu on a linksys SOHO router with DHCP enabled.

ONE of my ubuntu hosts can ping all other hosts on the network by IP or hostname.

ALL of the computers on the network can ping that ONE ubuntu host by IP but not by hostname.

That ONE ubuntu host can ping itself by pinging localhost, 127.0.0.1, 127.0.1.1, but not by it's own hostname.

I have already modified /etc/nsswitch.conf and installed winbind to work with NetBIOS names on my workgroup, and the other ubuntu host works just fine.

I don't want to manually edit hosts files on all the other hosts, I don't want to setup my own DNS server, so please don't post those solutions unless anyone else is interested in that(?).

I'd like some suggestions on how to get that one host working like all the others, thanks.

---

### Post by Iowan on 2008-05-11
Try editing the **/etc/dhcp3/dhclient.conf** file. Find the line similar to:```
send host-name "<hostname>";

```
Change <hostname>  to the machine's real hostname and restart networking (or dhclient, anyway).

---


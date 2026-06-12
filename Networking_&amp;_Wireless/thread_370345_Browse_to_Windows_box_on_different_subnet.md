---
title: "Browse to Windows box on different subnet?"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by neander on 2007-02-25
I have an ubuntu 6.10 desktop box installed as a testbed webserver. It has a static ip of 192.168.1.10, and connects to router 1 with ip of 192.168.1.1. Router 1 connects to the internet via cable modem. The LAN pcs are connected to router 2 on 192.168.1.100. Router 2 has a lan address of 192.168.2.1, and serves dhcp in range 192.168.2.100-200.

My ubuntu install is new and relatively unmodifed. I've given the ubuntu box the same 'domain' name as the LAN pcs, tho this may have been unneccessary. I cannot ping ubuntu box from lan or the other way around, probably to be expected since they're on different subnets (I'm not very good with networks).

How can I either browse or share between the two subnets? I've tried Places/Connect to Server, then Windows Share; browse network exposes nothing (tho a windows network is shown, nothing behind it). I can't make much of the help for that dialog.

I've read a bunch here on connecting windows and ubuntu, but maybe because of the different subnet issue I've not had any success so far.

---

### Post by neander on 2007-02-26
No tips for the needy??? <g>

---

### Post by sadjack on 2007-02-26
Neander

This is obviously a routing issue. You have in effect two networks. The routers know about their own network but not the other.

I only have one router, but in its advanced options it has the ability to set routing so that when other routers are added they can be configured to speak with each other.

There are probably ways to set this up within linux but have a look at your router set-up files first and see if you have the same options.

Hope this is of some help.

---

### Post by GnuSense on 2008-04-23
I'm still figuring this stuff out, but I'll chime in to this stale thread in the hopes that it will be useful to someone.  I have a gigabyte router attached to desktop machines with a wireless router hanging off of it that I use to connect to my laptop.  They have different subnets, 192.168.1.1 (wired router) & 192.168.2.1 (wireless).  In Windows and opensuse 10.2 Linux I don't have a problem browsing to my network shares on the different subnet from my laptop, but with Debian and Xubuntu Edgy on my laptop I do. 

However I just learned a command that will enable my Debian machine to see my wired subnet:

# route add  -net 192.168.1.0/24 gw 192.168.2.1

If I change my connection I have to issue that command again, I would prefer the situation I have on opensuse where I don't have to bother, but at least I can mount my shares.

I learned this trick from [COLOR="Navy"][this]("http://mydebian.blogdns.org/?cat=38")[/COLOR] page, which also makes some interesting other points.  I'm trying to decide whether I should enable 'wins support' in smb.conf and whether to enable ip forwarding.  [http://mydebian.blogdns.org/?cat=38](http://mydebian.blogdns.org/?cat=38)

---


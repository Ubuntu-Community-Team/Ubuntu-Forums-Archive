---
title: "Ubuntu Server, Two NICs (One Inet, One LAN)"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by beckols on 2008-06-17
I have a server that has two NICs, one is input for the internet, one goes to the LAN.  The LAN (eth0) works fine including dhcp. How do I configure eth1 to get internet? It doesn't show up on ifconfig unless I do ifconfig -a.

---

### Post by beckols on 2008-06-17
Ok, nvm it was a stupid mistake.. I actually have three network cards because I'm going to eventually have two DSL lines going into the server, so I just assumed that I was plugged into eth1, but it was actually eth2.

Now, my problem is that the server has internet, but it isn't sharing it on the LAN, so how do I get it to do that?

---

### Post by misterhead on 2008-06-23
I have the same problem with my Red Hat server. 2 NICs cable modem to one. Other to switch. Server has internet. Other connected machines IPs dhcp'd to them, but they still have no internet. help us.

---

### Post by superprash2003 on 2008-06-23
need to setup ICS.. hope this helps [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by misterhead on 2008-06-27
Well I tried to understand that wiki, but can't make heads or tails out of it. I guess because the server I'm trying to run is Red Hat ES 3 and not Ubuntu. Still better than the help I got at Linuxquestions.org. 3 weeks and not a single reply. that forum SUCKS. ubuntu forum rocks. at least people here try to help each other.

---

### Post by Iowan on 2008-06-27
[Another How-To]("http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.5.html") - but probably still not what you're looking for.

---

### Post by misterhead on 2008-06-29
> **Iowan said:**
> [Another How-To]("http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.5.html") - but probably still not what you're looking for.

That one at least makes a little more sense to me, but it seems to be going in a whole different direction than I've been going so far. Someone at work mentioned a DNS problem. but that ICS mentioned above sounds valid as well. I just can't follow it.

---

### Post by RuthlessK on 2008-11-26
Hi Guys,
I'm a complete noob to Ubuntu and have set myself a major task :confused: Ubuntu server 8.10 and I've added the desktop to it, i've also installed webmin 1.441 which and it is working fine.

**So my Task!**

I have 2 broadbands (Vodafone-adsl & NTL-cable) my server has 3 nics. I'm hoping to connect both BB to the serv via 2 nics and the 3rd I will connect my LAN. Once all configured I'm hoping to setup a intranet, files storage, mail server etc. I would like the mail.server to collect both sets of email that I have with ISP's as I cannot send from VF to NTL. I will only use the VF as my default for all internet traffic, the NTL will only be used for downloading and collecting mail.

Where should I start first configuring the nics, DNS, webmail? Only got 2 nics at mo, expecting the 3rd in the post tommorow sweex 1ghz:)

[SIZE="3"]My other question is it possible for me to achieve this?[/SIZE]

TY :-)

---


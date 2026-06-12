---
title: "problems with static ip"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by Moridin333 on 2008-10-28
Hi all,

What I'm trying to do is set up a ltsp on a wired network.

I've got all the programs installed but I am having the worst time with the networking.  Namely DHCP and just getting my server box to connect through my router.

In my setup I have one router with dhcp turned off, a server with one nic and a laptop with a wired connection.

right now I've been trying to get my server to connect to the net with the ip of 192.168.1.0.  it seems that the last number has to be 0 for it to work as a dhcp server.  this is my /etc/networking/interfaces 

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.254

```

I can ping all the other computers on my network and I can even ssh into the server.  But I can't ping google.com or any web page.  I have been working on this off and on for a few months and I'm completely lost.

Any help would be appreciated

---

### Post by jms1989 on 2008-10-28
Hmm, I think your ltsp server needs to have two nics, one connected to the router and one to your network so all connections go through it.

---

### Post by Moridin333 on 2008-10-28
> **jms1989 said:**
> Hmm, I think your ltsp server needs to have two nics, one connected to the router and one to your network so all connections go through it.

that's what I thought at first too.  This web page says that it should be possible

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring")

---

### Post by ilrudie on 2008-10-28
Most likely your problem is that you are no longer getting dns settings from dhcp.  When you setup a static IP you should setup static name servers in /etc/resolv.conf.
You may also need to change /etc/nsswitch.conf to tell the server to use dns if no local name resolution can be done (e.g. the hostname does not appear in /etc/hosts)

---

### Post by Iowan on 2008-10-28
Address seems strange - "0" and "255" are both usually considered broadcast addresses. (But then, I really haven't worked with ltsp.)

---


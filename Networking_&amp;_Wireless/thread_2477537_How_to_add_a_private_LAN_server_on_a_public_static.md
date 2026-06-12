---
title: "How to add a private LAN server on a public static server (Gateway)?"
date: 2022-07-28
forum: Networking &amp; Wireless
---

### Post by hphaas on 2022-07-28
This seems like it should be so simple, but.....

I have an Ubuntu server which is on a public, static IP address from the machine's primary Ethernet interface. This works great.
I wish for the server to act as a gateway (router) using a second Ethernet interface. This interface would then act as a DHCP server for a LAN.

Internet --->  public static IP -- interface one -- SERVER -- interface two - local LAN server (192.168.1.1) -- DHCP -- LAN machines.

Seems simple, but after many hours of googling, I have come up with nothing definitive.
I'm basically using a Linux machine as a hardware firewall for my LAN, with the complication that the server is not getting DHCP from a
modem/router, but is actually a public static IP.

I looked at Netplan and frankly... uh... no.
I would prefer to use Network Manager, but I am open to any and all suggestions.

Thanks!

---

### Post by TheFu on 2022-07-29
If you want a router, then best to use a router distro like OPNSense.
If you insist on running Linux or Ubuntu, then there is an Ars Technica article about setting up your own router by Jim Salter.  [https://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/](https://arstechnica.com/gadgets/2016/01/numbers-dont-lie-its-time-to-build-your-own-router/) Using a well maintained router distro is much easier.  Beware that BSD and Realtek NICs don't play well together, so you'll want Intel NICs.  There is an x86-64 port of OpenWRT, if you want a router distro, but not BSD-based.

I've been running my WAN router on an APU2 box ($144 new) with pfSense, then OPNSense since 2015. It is fanless, low power requirements, and silent.  If the APU2 breaks, I'll order the newer version of the same thing, perhaps with 1 more port.  It is an extremely capable router distro, typically used by Universities and can be scaled up or down on compatible hardware.  I have a small public set of IPs that are forwarded to different systems on the public-facing server LAN.  Desktops are on a different LAN.  Wifi devices, on yet another LAN (never trust wifi!), and guest devices and IoT crap are completely untrusted - outside the APU2 ... on a subnet the ISP's router provides.  OPNsense manages plenty of firewall rules easily for the outside world AND between devices on different LANs.  If you are a "router guy", then you'll appreciate the power.

OTOH, if you aren't a router guy, then I suspect you'd be happier with something less hard-core.

WAN routers shouldn't be general purpose devices. They should do 2 things.  Routing and firewalling.  I suppose a case could be made for running  bandwidth tracking/graphing on the router, if you won't setup an SNMP server elsewhere and grab the router data from that system.   If you want other stuff, do that elsewhere.  Stuff like running a VPN don't belong on your primary security device against all the bad guys of the world.  More features means more bugs. More bugs means more holes for attackers.  Just sayin'.

---

### Post by hphaas on 2022-07-29
Thanks very much for the reply.

Yes, I do plan to have a standalone (security) gateway.  My plan was to use the Ubiquiti USG:
[https://store.ui.com/products/unifi-security-gateway](https://store.ui.com/products/unifi-security-gateway)
but it is currently unavailable and possibly may be discontinued.
Alternatives would be to build my own as you suggested.That's not today's project.

In the meantime, I was really looking for - well - answers to the question at hand.  I do appreciate alternative suggestions for what my question implies, but I do really, simply, want my Ubuntu 22.04 machine to be used as a gateway for now. I am transitioning many things at the moment, and everything is in place to speed up my LAN by 5x to 10x by "simply" turning on the second interface as a DHCP sub-net.

(and yes, I've seen the Ars guide - and subsequent mods to it - but the guide is from 6 years ago and is based on /etc/network/interfaces which is now "obsolete". I suppose I could just switch back to that.)

Thanks again!

Hap

---

### Post by hphaas on 2022-07-29
> **hphaas said:**
> Thanks very much for the reply.

(and yes, I've seen the Ars guide - and subsequent mods to it - but the guide is from 6 years ago and is based on /etc/network/interfaces which is now "obsolete". I suppose I could just switch back to that.)

Hap
[SIZE=2]
March 4, 2022:
[/SIZE][h=1][B][SIZE=2]How to switch back networking to /etc/network/interfaces on Ubuntu 22.04 Jammy Jellyfish Linux
[/SIZE][/B][/h][SIZE=2][FONT=&amp][SIZE=2][FONT=arial]https://linuxconfig.org/how-to-switch-back-networking-to-etc-network-interfaces-on-ubuntu-22-04-jammy-jellyfish-linux[/FONT][/SIZE]

[/FONT][/SIZE][COLOR=#721C24][FONT=&amp]WARNING[/FONT][/COLOR]
[COLOR=#721C24][FONT=&amp]Switching back from NetPlan/CloudInit to the now obsolete networking daemon is not supported nor recommended as you might end up with a broken system. It has been obsolete now for multiple [/FONT][/COLOR][Ubuntu versions]("https://linuxconfig.org/how-to-check-ubuntu-version")[COLOR=#721C24][FONT=&amp].

[/FONT][/COLOR]

---

### Post by TheFu on 2022-07-29
Sorry, the Ars Technica article I linked wasn't the how-to.  It was the "why-to".  There is another with steps-by-step instructions for the 'how-to'.   [https://jrs-s.net/presentations/2016-Routing-With-Linux/](https://jrs-s.net/presentations/2016-Routing-With-Linux/) seems to be Jim's presentation on setting up a router on Ubuntu.  [https://jrs-s.net/presentations/2016-Routing-With-Linux/img10.html](https://jrs-s.net/presentations/2016-Routing-With-Linux/img10.html) is an overview of the steps (from the middle of the presentation). Details are in there.   Just translate {16.04} --> {whatever release you are using}.  Typically, that would be using netplan YAML files instead of the old interfaces files but all the other stuff should be basically the same.  I haven't done this in a few decades and after discussing security with experts in the field who I've known for over a decade that warned me off of trying to make a multi-purpose WAN router, I've decided to take their advice.  That's all I'm trying to do here, so you can avoid mistakes.

If you have specific questions about any part of the steps, someone here will be happy to help.  I assume you've enabled routing on the system already? That's just a setting in /etc/sysctl.conf.  
Next, you'll want to use the newest interface for the kernel firewall to setup default DENY inbound rules from the WAN and masquerading.  22.04 supports both iptables and the newer nftables.  His example assumes iptables. You'll likely want some more for more security. Lots of people post their iptables firewall rules and some commercial companies have F/LOSS versions of their scripts that can be used.  These would include logging abusers and slowing down their connections dynamically. Nobody likes bandwidth hogs.

Ubiquiti makes reasonable stuff, though their router OS CLI stuff is 'different'.  I've managed ubiquiti wifi APs for a few clients. Those are straight forward enough, so if there is a GUI, it shouldn't be too hard.  I never had to deal with Ubiquiti's new requirement for java-based AP management which sends traffic data back to the company.  Did they ever enable a way to turn that off?  The management server only needs to be up to make changes to the network, not all the time. Some people keep it in a VM and spin it up when needed.  I don't know if it has to be running when a device boots or not. I wouldn't be surprised either way.

Making a Linux system perform routing isn't hard. Lots of how-to guides on the internet.
Making a Linux system a DHCP server isn't hard. Lots of how-to guides on the internet.
Making a DNS server isn't hard. Lots of how-to guides on the internet.  Jim used ISC's bind. I use a different method - long, long, ago my bind server was hacked because I was a few months behind on patches.  This was over 20 yrs ago - the world was different, but hackers were still out there.  I'd been running bind at work since 1995, so I wasn't exactly completely new, just ignorant.

But it is still much easier to start with a router distro. If I had, I would never have been hacked and the router defaults are usually 'reasonable' to keep me out of trouble.  It is a different world these days.

---

### Post by SeijiSensei on 2022-07-29
One key thing to remember. TCP/IP packet forwarding is disabled on Ubuntu by default. That means the machine cannot operate as a router unless this restriction is removed. Edit (as root with sudo) the file /etc/sysctl.conf and remove the hash mark ("#") at the beginning of the line
```
#net.ipv4.ip_forward=1
```

Then reload the sysctl.conf file with
```
sudo sysctl -p
```

---

### Post by Doug S on 2022-07-29
I implement my WAN to/from LAN firewall/router function on a linux server (currently Debian, but has been Ubuntu) with iptables. There is a learning curve to iptables, and it can consume a lot of time. The DHCP server function is via isc-dhcp-server.

---


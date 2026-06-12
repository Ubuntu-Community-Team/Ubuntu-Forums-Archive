---
title: "routing with two NICs"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2015-08-18
I have two network interfaces on a headless server. wlan0 and eth0. wlan0 is assigned a dynamic ip address from a wireless hotspot and is the access to the outside world. I would like to attach device(s) to eth0 and have non-local traffic on eth0 all be routed to wlan0.

What are the proper tools to set this up? I have looked at several posts and tried several methods, but before I get drowned in posting what failed, what is the correct direction?

Thanks,

Deron

---

### Post by TheFu on 2015-08-19
Edit the /etc/network/interfaces file and add your special routing needs there. Basically, don't have a gateway for the local traffic.  The manpage for the **interfaces** config file is pretty good.
[http://www.cyberciti.biz/faq/ubuntu-linux-add-static-routing/](http://www.cyberciti.biz/faq/ubuntu-linux-add-static-routing/) has an example.

You could also use the **route** or/and **ip** cmds to fine-tune routes. 

Don't know if this works with wifi NICs. Definitely works with multiple wired ethernet devices.

---

### Post by SeijiSensei on 2015-08-19
Is the wireless "hotspot" a router, or do you need to have the Linux box do all the routing?  If you have a router upstream, then you just need to [configure the Ethernet adapter]("https://help.ubuntu.com/lts/serverguide/network-configuration.html") in /etc/network/interfaces, or through NetworkManager, and uncomment the line 
```
net.ipv4.ip_forward=1
```
in the file /etc/sysctl.conf.  You'll need to reboot to put that into effect.

Don't include a "gateway" in the eth0 specification.  Linux will then manage all the routing for you and forward any traffic for addresses outside your network on to the upstream router.

---

### Post by faroutliving on 2015-08-23
Thank you both for your suggestions, but nothing led me to a solution. I suppose now would be a good time for a little more detail.

The linux server is using wlan0 to connect to a wireless hotspot and is dynamically assigned an ip address. The hotspot is always 192.168.1.1 and only allows 5 connections so the server is setup as a dhcp server on eth0 and that is working fine. I've assigned the address range 192.168.100.0/24 to eth0.

Other devices on eth0 can "see" the server, and the server can see the outside world (but simple things like ping google.com take an inordinate amount of time initially).

route shows just the one gateway.

Nothing I tried in network/interfaces worked using info gleaned from [http://www.cyberciti.biz/faq/ubuntu-linux-add-static-routing/](http://www.cyberciti.biz/faq/ubuntu-linux-add-static-routing/) and net.ipv4.ip_forward=1 was already set.

Anything raise a flag or does some other tool need to be brought into play? iptables is my next rock to look under.

Thanks again,
Deron

---

### Post by Doug S on 2015-08-23
> **faroutliving said:**
> Anything raise a flag or does some other tool need to be brought into play? iptables is my next rock to look under.Yes, you want to turn your server into a router and you should use iptables to do it. You already have net.ipv4.ip_forward=1, which is required. In its simplest form, and with default policies of ACCEPT, all you should need is:
```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```However, typically the rule set is much much more complicated, also implementing firewall protection.

---


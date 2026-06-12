---
title: "Simple router in Ubuntu"
date: 2005-07-20
forum: Networking &amp; Wireless
---

### Post by PcPixel on 2005-07-20
I used to use Mandrake, but am really starting to like Ubuntu. However, I'm having a problem making a router.

I'm looking to make a very simple router. One that will route packets from a 12.XX.XX.XX to/from 10.XX.XX.XX.  I've got two NICs, both configured properly & work (I can talk to the respective networks from the Ubuntu box). However, I'm trying to make the routes permanent (ie if it reboots). I asked in the #unbuntu IRC room and they said to modify my /etc/network/interfaces file. I did so. It looks like the following:

iface eth1 inet static
address 10.100.104.1
netmask 255.255.255.0
up route add -net 12.XX.XX.0 netmask 255.255.255.0 dev eth0

auto eth1

iface eth0 inet static
address 12.XX.XX.250
netmask 255.255.255.0
gateway 12.XX.XX.XX
up route add -net 10.100.104.0 netmask 255.255.255.0 dev eth1

auto eth0
----------------------------------------------------------------------------------------
If I do a netstat -rn, I get:
12.XX.XX.XX ....... eth0
12.XX.XX.XX ....... eth0
10.100.104.1 ..... eth1

Did I use the "up" command incorrectly? Or would I add the static route commands somewhere else? The routes work if I type them into a terminal window.

Help! :)

---

### Post by gruepig on 2005-07-20
You shouldn't need the up commands; the routes should be brought up automatically. What you need to do is turn IP forwarding on and enable masquerading (NAT).

To turn on IP forwarding, 'echo 1 > /proc/sys/net/ipv4/ip_forward'  To make this change permanent (persist after reboots), edit /etc/network/options to contain the line 'ip_forward=yes'.

To enable masquerading, you need an iptables rule.  Something like 'iptables -t nat -A POSTROUTING -j MASQUERADE'.  To make this rule be loaded whenever you bring up networking, you'll want to have this line in a file somewhere in /etc/network/if-up.d/.

---


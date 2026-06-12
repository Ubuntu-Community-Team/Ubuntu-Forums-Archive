---
title: "Can't access internal network but Internet"
date: 2018-09-26
forum: Networking &amp; Wireless
---

### Post by Elmi77 on 2018-09-26
[COLOR=#242729][FONT=Arial]Hi,

I have a strange problem with one Ubuntu-system in my network. As well as some other Linux-boxes it is located in an internal network in IP range 192.168.1.x with full access to all other systems in this network and with access to the internet via a separate firewall (IP/Gateway 192.168.1.1).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]All Linux-boxes are working fine except this one box (let's name it X) which is an Ubuntu 16.04 LTS ARMHF system on an BeagleBone: Internet access works properly but it can't ping or even SSH an other system in same network. On the other hand when I ping from an other system in this network to X, ping works but SSH not. Funny again: ping or SSH from X to some other server in _Internet _works![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Network configuration on this one system X is default/the same as on all other (as far as I can tell) Any idea what could cause this or where I could look for a reason for this strange behaviour?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks!

[/FONT][/COLOR]

---

### Post by The Cog on 2018-09-26
Duplicate IP address perhaps. Can you ping X from another machine when it's switched off?

The output from the commands **ip addr** and **ip route** might give a clue.

---


---
title: "Internet connection sharing with 3 network cards problem"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by _Darm on 2008-06-06
Hi, I've got a compuiter running 8.04 with all the latest updates that is connected to the Internet via a adsl modem that is on network card called eth1. I got Ppoe sesion running.
My computer also has eth0 and eth 2, and I want to share internet to two offices throught it. So it would be a gateway. All computers in the offices have Windows XP, and I need them not to be able to access each other.
So I installed firestarter and got it to share internet to eth0, but I don't know how to get it sharing to eth2 too.
I searched all around and couldn't find an easy way to do this. I tried reading about configuring iptables (that's what firestarter does, right?) but I think its too hard for me, I can't get it right.
I would love to get any kind of help... Maybe there is another gui to IP tables that supports 3 network cards?

---

### Post by _Darm on 2008-06-06
Yeah, and later on I am planning on configuring an email server on the same gateway computer. So I would need a solution that would not harm the SMTP traffic

---

### Post by superprash2003 on 2008-06-06
read this [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by ilrudie on 2008-06-06
Or you could just buy a router with a 4 port switch if you aren't interested in learning about networking.

---

### Post by _Darm on 2008-06-06
Kinda got it.
Both eth0 and eth2 are sharing internet now (after running 
"iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE" (thanx 2 supersprash, although I didn't setup a DHCP server since I am setting the IP adresses on computers manually))
But now both of the offices see each other too.
I mean now I can access one office from another one, and I don't want that.
Guess that I need to set up a firewall in the iptables to block the traffic comning in between the network cards.

---


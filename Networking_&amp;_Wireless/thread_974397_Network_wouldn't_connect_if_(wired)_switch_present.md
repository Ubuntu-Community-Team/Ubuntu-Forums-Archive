---
title: "Network wouldn't connect if (wired) switch present"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by pinegreen on 2008-11-07
I have a really bizarre problem that I have never encountered before.

We have a set up where mac address of the machine is registred with the central network guys and we're supposed to use DHCP, which then gives a static address. The systems works, but it is a bit flakey, basically, dhcp often takes long to actually get the address and even if you hardcode IP and try to ping the gateway, you get a couple of network not reachable bounces before it starts to work.


However, if I plug it through a switch, a vanilla netgear wired swtich, it doesn't work at all. The problem is that a mac on the same switch works ok, that the we tried two switches, that wireshark sees some traffic: I see my computer ARPing the gateway and getting no response, I see some external traffic coming it, so the basic connectivity is there.

I've tried disabling ipv6 and arp (blind shots, I know), but have no other ideas. Has anybody ever seen anything like that?

anze

---

### Post by jonobr on 2008-11-07
Hello


From the first part of your post it sounds as if there are just plain network connectivity/reliability problems?

FOr the second, if I am understanding you right, it sounds like you may be trying to get layer 2 messages through a layer 3 device?

It sounds as if your arps will not go through it.
The only way to get to the bottom of that is wiresharking on the remote end to see if the requests are getting through?

---

### Post by pinegreen on 2008-11-11
Ok, I've solved my problem.

The e1000 network card has trouble talking to some netgear routers. It is really surprising, as the motherboard in question is a high end sever motherboard! As soon as I installed $5 network card in, everything begun to work as expected!

jonbor -thanks for you suggestions.

---

### Post by Iowan on 2008-11-11
> **pinegreen said:**
> 
The e1000 network card has trouble talking to some netgear routers.  Interesting proposition that might explain some of the "No DHCP offer received" threads I've seen.

---


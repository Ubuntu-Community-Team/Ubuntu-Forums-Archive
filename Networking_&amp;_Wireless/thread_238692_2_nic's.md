---
title: "2 nic's"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by kristof_v on 2006-08-18
hi,

i installed 2 nic's in my system.
lspci recognizes these nic's correct.

i edited /etc/network/interfaces so that both nic's get a static ip address:
eth1: 192.168.22.50
eth2: 192.168.22.51

there's also a eth0 (onboard lan), but that one doesn't get loaded on boot

now the problem is as following:
when i boot the system with the cable plugged in eth1, i can login to the computer using ssh.
however when it is plugged into eth2, i can't login to ssh.
then when i plug it in again in eth1 en do ifdown -a and ifup -a i can login to ssh again.

but there's more:
i can't even ping with eth2 to other computers in the network :s
when i do:
ping 192.168.22.49 (my laptop), it doesn't get a reply, sometimes it even gives the message destination host unreachable
how is that possible??
they are in the same network right, no need for gateway etc...
i even configured the gateway out of desperation, with no result...

in short:
eth1 seems to work correct,
but eth2 doesn't work correct, it can't even ping other computers in the network

i hope anyone can help me on this one.

grtz

---

### Post by spd106 on 2006-08-18
Have you checked that the routing table changes the default route to use eth2 after you swap the cable?

It sounds more likely to be a hardware error though. Do you dual boot or could you use a live cd to check that it's not software.

Hope this helps

---

### Post by Dan Luevano on 2006-08-18
I would check your route tables...I had a similar problem and found that the system created two DEFAULT entries in my route table, one for eth0 and the other for eth1...this was causing a problem. When I removed the DEFAULT entry for eth1, both nic cards started working.  See other Threads by Dan Luevano (NETWORKING).  Hope this helps.

Dan

---


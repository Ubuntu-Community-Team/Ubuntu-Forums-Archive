---
title: "Can't detect second ethernet interface"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by Kosika on 2007-04-03
I'm setting up my ubuntu machine to act as an router/firewall.
I have an integrated NIC on the motherboard thats works OK, I'm using/connecting through it right now and have attached an PCI NIC to act as secondary interface, eth1. But the problem is that ubuntu can't detect it. The NIC has worked on another linux machine before. 
I've tried ifconfig, dmesg, lspci -v. Nothing of these command shows anything that could possibly be the NIC I'm looking for. I've also have an wireless NIC, ath0 that seams to work ok (not tested it thought).
What shall I'll do? Do you want some outputs from some commands or?
Thanks!

---

### Post by ndefontenay on 2007-04-03
Hi.

I think the outputs would help.
Can you try to swap your 2 cards to see how it behaves?
This would tell you if the problem is on the card, Ubuntu or even maybe the slot where you plug it.

---

### Post by Kosika on 2007-04-03
Ok, thanks for the quick answer.
I've removed the wireless NIC and put the PCI NIC in that slot instead.
And now now I have both eth0 and eth1, with correct MAC's and all, HURRAY! I'll see if I can put back the wireless later,
But...Now firestarter have problems when I shall share the connection, an "Unknown error", I shall search and experiment some.
But it was really strange that just moving the card made a diffrence, or uif it was that I'll removed the wireless card, what can it be?

---


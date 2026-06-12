---
title: "Xircom / PCMCIA / After install network does not work"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by rmalta on 2006-07-22
Hi,

I'm installing Drapper in a Thinkpad notebook for some days now ;) 

I've been having the problem with a Xircom card (driver xirc2ps_cs).

During installation the card works fine. I can change to the second vt and see the card got an IP adress from my DHCP server and I'm able to ping any server in the net.

Well after rebooting I get no IP address from DHCP more :(
Even using a static IP address doesn't work. The led in blinks, the card is identified and actualy it should work, but it doesn't ;-/

I've tried really many things, but nothing helped. So I installed breezy :D and :mrgreen: 

It worked during installation and also afterwards :)

Ok ... now I tried to dist-upgrade online. I've changed the sources.list file and "apt-get update" and "apt-get dist-upgrade"

The laptop worked a while and after I rebooted ... :evil: network is not working any more!!!

I'll try to boot with an old kernel tomorrow(actually today ;)
Perhaps it is a module problem.

I'll inform the results here.
If anyone already knows about this problem, or even better ... the solution, please post it here :)

Thx
Ricardo

---

### Post by rmalta on 2006-07-24
All right!!

It seems to be a problem with the kernel 2.6.15!
I booted the system with kernel 2.6.10 and it works!

I'll check now for a newer kernel, or try to compile 2.6.15 myself.

I'll post the result here again.

Regards,
Ricardo

---

### Post by stani on 2006-08-26
Do you have more news? Are you still using 2.6.10?

I have a fresh installed Xubuntu Dapper with a not working xircom card. How can I downgrade my kernel? It should be possible through synaptic, but I can't find the package there. Which repository should I add to my sources.list and how do I prevent my dapper sources to take over?

Is it possible to just downgrade the kernel?

Stani

---


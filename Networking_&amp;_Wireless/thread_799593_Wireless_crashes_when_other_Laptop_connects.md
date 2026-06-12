---
title: "Wireless crashes when other Laptop connects"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by CHW on 2008-05-19
Hi,

I use now Ubuntu 8.04 since two weeks and have bought a Dell Laptop (Vostro 1500) to install it on.

Normally my Internet connection (wireless) works fine, but when an other Laptop connects the wireless Network I get problems. The other Laptops are running Windows Vista or XP.

Then the network crashes and I have to try to reconnect. When I change my (static) IP address, click ok, and then rechange it to the original IP address I can reconnect, but it is possible that I loose the connection again.

Here my card: (sudo lspci -v in console)

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1021
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

Because I am a Linux beginner I don't have much the knowledge about it, so if I have not posted enough informations, you have to say it ;)

thank you

---

### Post by ocpistol on 2008-05-20
im having the same problem

---

### Post by CHW on 2008-05-26
Meanwhile I searched the internet and read some posts in forums to find new ideas.

I tried the hints with the network manager and the "better iwl3945" chili555 gave in

[http://ubuntuforums.org/showthread.php?t=800357&highlight=3945]("http://ubuntuforums.org/showthread.php?t=800357&highlight=3945")

but I still have the problems. The only advantage is that with the new network manager I can reconnect faster.

May someone have an other idea what I could try?
Maybe I should install the "Windows" driver?

---


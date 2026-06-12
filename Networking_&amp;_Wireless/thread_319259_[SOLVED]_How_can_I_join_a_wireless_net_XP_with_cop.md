---
title: "[SOLVED] How can I join a wireless net XP with copper"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by pappo on 2006-12-15
My home systems are two computers.

Computer 1:  XP with two network cards.  One copper and one wireless.  I don't use the copper and have it disabled on the XP machine.  I connect from my XP box to a D-Link wireless router and then to my cable modem.

Computer 2:  Ubuntu PC with only a copper network card.

My idea was to use a crossover cable and connect my Ubuntu to the XP using the copper connections.  Enable the copper network connection in the XP.  That all worked.
But, how do I configure the XP box to pass the traffic from the Ubuntu PC, from the copper network card to the wireless card so I can reach the Internet.

I considered using "bridging" feature of XP, but when you do that it assigns 192.168.0.1 address to the bridge, and that conflicts with the wireless router which also uses 192.168.0.1.

I know I could just go buy anothe wireless card for Ubuntu, but what technical fun is that ?

---

### Post by jruschme on 2006-12-15
I suppose that there is the obvious question of why not just cable the Ubuntu PC to the directly to the router, but I'll assume that that is logistically impossible.

That said...

On the Windows box, open the Properties on the wireless connection. Select the Advanced tab and check the option to share this computer's Internet connection.

This should set the Windows box up as a NAT-based router and DHCP server for computers on the wired connection.

---

### Post by spd106 on 2006-12-15
Why not shift the wireless router to another subnet? 192.168.1.1 for example. I know that you will have double NAT, but I can't see any other way. ICS can be so frustrating, there seems to be almost no way to change the settings. I suspect you could hack the registry, but I wouldn't know where to begin.

You could always install Ubuntu on the XP machine. That would solve all your problems:D

---

### Post by pappo on 2006-12-18
As you said, it is logistically not possible to wire directly to the router.  I would like to make the XP box an Ubuntu one,but I can't get Dungeons & Dragons Online to play on anything but XP, so I am still using one XP machine.
I tried ICS but it wants to make the XP have a 192.168.0.1 IP and that is the same as my D-Link router address, so I had conflicts.
I read spd106's reply about changing the router to 192.168.1.1 and I may give that a try also.

---


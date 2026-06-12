---
title: "[SOLVED] nm-applet (or whatever) not selecting my connection at startup"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by flick152 on 2007-11-24
I have one connection, ethernet LAN but after login nm-applet doesn't select it and I have to do it manually, irritating for me, anger inducing for the rest of my less savvy family.

How can I make nm-applet (or whatever) use my ethernet automatically?

THanks

---

### Post by daengbo on 2007-11-24
If you are using a desktop which won't change locations, you can just manually set the network interface. To do that, go to System -> Administration -> Network and type in your password.

Choose your wired interface (probably eth0) and check "Enable this connection."
In the "Configuration" pull-down box, choose your preference (most likely "Automatic configuration(DHCP)." Click OK.

When you're finished, check the box next to the wired interface to activate it.

Network Admin will now complately ignore your interface and it will always be on when you turn on your computer.

Cheers

Daengbo

---

### Post by flick152 on 2007-11-24
Many thanks, working now.

---

### Post by daengbo on 2007-11-25
If so, please mark the thread [Solved].

---


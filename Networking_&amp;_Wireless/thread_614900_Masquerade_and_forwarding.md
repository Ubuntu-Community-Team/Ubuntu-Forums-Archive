---
title: "Masquerade and forwarding"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Keps on 2007-11-16
Hi, i have a little problem.
I have 3 pc (A, B, C). A is connected to B and B is connected to C.
All this pc use static ip (So i don't use dhcp!).
I want to send a packet from A to C and viceversa.

I found this howto
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

i followed each step, but it didn't work so good... :(
Infact A can ping B, C can ping B but A and B can't ping C.
I setted ip of A at 192.168.0.1
I setted ip of B (eth0) at 192.168.0.2
I setted ip of B (eth1) at 192.168.0.3
I setted ip of C at 192.168.0.4

In the masqueradescript.sh i setted intif=eth0 and extif=eth1.

someone can help me?

Maybe i have to install something???

thank to all

---


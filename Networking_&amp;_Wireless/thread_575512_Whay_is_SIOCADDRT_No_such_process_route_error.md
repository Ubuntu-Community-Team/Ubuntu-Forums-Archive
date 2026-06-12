---
title: "Whay is SIOCADDRT: No such process route error?"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by uobejct on 2007-10-14
I have  installed Ubuntu 7.10 and have a little problem:)
when i am trying to do  sudo route add -host 195.22.112.12 gw 10.0.10.1 dev eth0
it failes with message SIOCADDRT: No such process
my ethernet card is /dev/eth0 and in Debian etch this command runs successfully.
What is  "SIOCADDRT: No such process" error?

Can someone help me?

---

### Post by uobejct on 2007-10-14
I solved the problem:)
There is a switch in network manager appelt.
And if DHCP is an active one, route command executes normaly:)
:guitar: :guitar: :guitar:

:lolflag:

:popcorn:

:KS

---

### Post by hibernate on 2007-11-25
Hello.

I have static IP.
So, let's pretend, my network configuration looks like this:
IP x.x.x.x
netmask n.n.n.n
gateway g.g.g.g
DNS1: d1.d1.d1.d1
DNS2: d2.d2.d2.d2
Also i have 2 routes to add:
route r1.r1.r1.r1 mask m1.m1.m1.m1 g.g.g.g
route r2.r2.r2.r2 mask m2.m2.m2.m2 g.g.g.g

I tried to set up the network via applet and recognized that it doesn't set the gateway on the gateway tab (it clears after i apply changes and open manager again). Then i setted gateway via console.
And then when i tried to add routes, i got that SIOCADDRT error.
Then i setted DHCP in network manager and configured the network in console (i'm not really sure if i did it right). Tried to specify a route - it really works. But i still don't have network! I also have XP installed, so now i'm using it for internet.
Please help me configure the network properly. That's my first try with Ubutu - intalled Gutsy 2 days ago...

---

### Post by ryukent on 2008-02-08
I had the same problem and ended up solving it by replacing the network manager with WICD.

Please see:

[https://help.ubuntu.com/community/WICD]("https://help.ubuntu.com/community/WICD")

---


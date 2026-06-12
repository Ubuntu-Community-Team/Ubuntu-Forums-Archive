---
title: "few routing questions"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by extracted on 2007-10-11
I just recently bought a few more things that require internet and, I am looking to basicly rebuild my home network.
 Now the basic lay out is like this

3 Computers  
    A. is a Windows Box that is in the front room (192.168.1.187)
    B. is a Fedora core 7 In my spare room.   192.168.1.2
    c. is a Ubuntu 7.04 in my spare room.      192.168.1.121
x-Box 360          192.168.1.111
normal x-box a. 192.168.1.5
                         b. 192.168.1.6
                         c. 192.168.1.7
Nintendo wii       192.168.1.8
and the router  192.168.1.1

 What I am wanting to do is have my 360 a normal xbox and my 2 linux installs in my spare room all on a switch that connects to one of the linux installs to route packets back to the router wireless via a wireless card.
 Could this be a possible solution ?

---

### Post by mpokrywka on 2007-10-12
I assume that all your machines are in the same IP network (netmask 255.255.255.0). If yes, then you should use bridging instead of routing. On linux machine with wifi card and ethernet nic create a bridge and add both interfaces. BUT... that will work ONLY if there will be no problem with bridging through wifi, and support of this feature may not be available in wifi driver. Atheros wifi should work, I don't know about others...

---


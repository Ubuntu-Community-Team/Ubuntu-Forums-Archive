---
title: "Impromptu network sharing?"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by bieber on 2007-06-03
Hello, everyone.  Right now I have one desktop machine in a room, with a single ethernet cable from a router in another room connecting it to my home network, running Feisty Fawn.  What I'm wondering is, if I stick another Ethernet adapter in the machine, will I then be able to connect that to another laptop, also running Feisty, and have it connect to the network as well?  If so, what sort of ethernet cable do I need (is it crossover that you use to connect two computers directly?), and how do I set this up in software?  I remember bridging connections in Windows ages ago, but I have no idea how to do it with ubuntu.

Also, if I pick up a cheap 10/100 card from Best Buy, there shouldn't be any driver issues, should there?  Wired networking is pretty much safe, correct?

---

### Post by Ken_Lewis81 on 2007-06-03
Wired networking's pretty much safe, and you will need to read up on the linux interfaces setup (try 'man interfaces' in a terminal window) to see how to add bridges in linux, as well as grabbing the 'bridge-utils' package from the repositories which contains tools and documentation.  Good luck!

Take care.
Ken.

---


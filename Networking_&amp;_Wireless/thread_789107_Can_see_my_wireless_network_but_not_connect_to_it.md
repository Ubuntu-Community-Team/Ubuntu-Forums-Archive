---
title: "Can see my wireless network but not connect to it"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by gjb1002 on 2008-05-10
Hi all,

After installing Hardy Heron (Kubuntu) last night I've spent much of the intervening time trying to persuade it to talk to my wireless network. So far without success.

My wireless card seems to be "RaLink Unknown device 0781", so I downloaded and built the driver source from RaLink's website. So far so good. If I do "sudo iwlist scan" I can see my network. But if I open KNetworkManager no networks are listed, although my wireless interface is. In fact KNetworkManager seems to behave erratically, and information entered there has a tendency to disappear.

So I tried the guide for connecting via the command line (top of the sticky threads on this forum), but that didn't work either, it said

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help gratefully received.

---

### Post by gjb1002 on 2008-05-10
I fixed it myself, I needed the "additional command" given in the tutorial, so my card was evidently not among "most cards"...

sudo iwconfig <interface> key open

It now works, the only remaining issue being that firefox always seems to start in offline mode. When I manually swap this it can then reach the internet...

---


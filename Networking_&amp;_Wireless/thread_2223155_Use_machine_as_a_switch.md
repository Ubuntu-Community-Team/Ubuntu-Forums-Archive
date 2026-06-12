---
title: "Use machine as a switch?"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by futureslay on 2014-05-09
Hi,

First off, I don't know if this is at all possible, so shoot me if it's not!
I'm in a residential environment running a small home server for media streaming (primarily), as a NAS and web serving functions. I currently have it in my bedroom, but it's a little noisy and has a tendency to warm the room a little more than is preferable. I want to move it into my spare room, which currently has a wireless AP connected to Powerline. It only has two LAN ports, however and is 100Mbit, whereas the Powerline and my server are both gigabit.
[B]I'd rather avoid buying a switch if I can.

[/B]What I'm hoping to do, in order to not bottleneck my server's connection to my network down to 100Mbit, is to have the server directly connected to my Powerline (i.e. gig to gig) on eth1, and then to have the AP connected to eth0 (i.e. gig to 100Mbit) so I'm not bottlenecking by going the other way round.

As below:

Powerline (1000) - No bottleneck.
Server (1000) - No bottleneck.
AP (100) - No bottleneck.

**Not**:

Powerline (1000) - No bottleneck.
AP (100) - No bottleneck.
Server (100) - Bottlenecked to a max of 100Mbit.

Hopefully you can see that I have a spare ethernet interface on my motherboard (eth0), as I use a PCI NIC (eth1).

Hopefully that makes sense - if not, ask, and I'll try my best to clarify!

Dom

---


---
title: "Weird router DMZ mode prevents workgroup computers from seeing each other"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Zeroangel on 2008-03-02
Hi all,

I've put my Ubuntu computer on the DMZ for my network, however I'm having a big problem with Samba now, on ALL of the computers.

They cannot see each other.

And I believe this is partially due to the fact that when I put my computer on the DMZ, it is assigned a vastly different IP than the rest of the computers.

Taking my PC off of DMZ allows all computers on the network to see each other temporarily (including ability to see mine), but after awhile I lose ability and have to instead type in manually the IP addresses of the computers in order to browse their files. Changing the DHCP settings doesnt help (because it wont let me assign the DHCP to the same w.x.y range as the DMZ'd computer)

How do I get around this problem?

(P.S.: Damn my ISP and their accursed 2-wire routers that I have no choice but to use)

---

### Post by SpaceTeddy on 2008-03-02
if i remeber the specifications of the windows name resolution right, then it is done via broadcasting. If you put your computer on a different subnet, or worse, with a router inbetween, broadcasts will not reach you anymore. Also, windows-hostname do not use the "normal" dns queries, they solve that though the nmbd process (on your ubuntu box) - again via broadcasts... i think.

I think what you need is a wins-server... samba can act as one (afaik).

---


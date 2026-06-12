---
title: "Netware gateway problem"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Fresh Spam on 2007-11-17
Shall begin with description of our network.
In our organization (ORG1) Ethernet-based network (Win & Lin computers), with no Domain controller (workgroups only), DHCP & WINS & gateway to Internet working on W2kAS.
Besides we have Novell 3.12 (NW1) server, which is gateway to ARKNet in 2nd organization (ORG2)(Win9x/DOS). On the other hand ORG2 connected to 3rd organization (ORG3), which have Ethernet-based network (Win NT/2K/XP computers),Novell 4.11 (NW2) server  and gateway on Novell 3.12 (NW3) server (to ORG2).
Next protocols are used in Win NT/2K/XP (ORG1): TCP/IP, NetBEUI, NWLink, NetBIOS (IPX/SPX compatible...)
What we see in Win network: ORG1 network &#8211; almost (MS network &#8211; Win & Lin computers, Netware or &#8230; -- NW1), ORG2 &#8211; nothing, but ORG3 &#8211; almost  (in the same "Network" with OGR1)
In Ubuntu 7.04 GSAMBAD & ncpfs are installed, but we see only ORG1 (Win & Lin --in the "Network", NW1 by "slist") and Internet gateway + NW2 from ORG3 ("slist").
 1.Can we tune Linux like Windows (for users comfort) and have access to ORG3 Win computers?
2. Can we see all?
P.S. I'm sorry, my English is bad :cry: , but Russian forums can't answer my questions (I have much more questions;);))

---


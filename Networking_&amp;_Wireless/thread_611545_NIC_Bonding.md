---
title: "NIC Bonding"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by prodezigner on 2007-11-13
Alright, I've never bonded cards, I don't have two of the same NIC, and was wondering if I could pull that off with different cards?

Would bonding help my home server ANY at all? Lots of downloading and uploading to it...

Another question, is there a way I can pick outbound data for one NIC and inbound data for another NIC?

---

### Post by Fire_Chief on 2007-11-13
Yes, bonding can be done with two different cards however....

In all but a very few cases, it won't make a difference in the speeds you see uploading and downloading.

One such exception is if you have a gigabit managed switch which is capable of etherchannel/bonding AND the server only has 100Mb NICs AND the workstations you are uploading and downloading to/from have gigabit NICs.

Lastly, no, you can't specify one NIC for inbound traffic to the server and one NIC for outbound traffic from the server. The remote system connecting to the server would get confused by the communication with two different destinations on the network (assuming they are not bonded).

---


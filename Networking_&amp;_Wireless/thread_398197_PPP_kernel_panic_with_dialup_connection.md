---
title: "PPP kernel panic with dialup connection"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by stonedyak on 2007-03-31
I'm getting a kernel panic in pppd every time I make a dial-up connection to my ISP. The panic always happens within a few minutes of connecting. This happened in Edgy, and it's also happening in Feisty Beta. I've also confirmed it in SuSe and Knoppix so it's not just an Ubuntu or Debian thing. I've attached a photo of wvdial just after connecting, and another showing the kernel panic.

The odd thing is that it only happens when I connect to my normal ISP. If I dial up a different ISP everything is fine. Unfortunately I can't switch since I use a freephone number for my normal connection (i.e. no call charges). I also happen to work for the ISP so I get it for free :).

Clearly there's something odd about this connection that other ISP's don't have. On the other hand, connecting to the Internet should never cause a kernel panic (connecting from Windows works fine).  

Can anyone give me some suggestions on where to go from here? I've Googled for various bits from the stack trace, but found nothing helpful. How can I get some better logs/debug information to help diagnose this?

---


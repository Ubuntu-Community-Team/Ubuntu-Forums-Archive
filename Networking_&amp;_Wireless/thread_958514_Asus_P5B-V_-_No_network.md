---
title: "Asus P5B-V - No network"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by bbhsoft on 2008-10-25
Hello,

I have installed Ubuntu 8.04 on a Desktop machine with Asus P5B-v motherboard, but i can't get the network to work, i've tried various solutions i found on the net and i could not get it up and running.

The network card is:
Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller

Does anyone had this problem ?

Thank you.

---

### Post by cariboo on 2008-10-25
You will have to do this in a Applications-->Accessories-->Termianl type:

```
sudo lshw -C network
```

and post the output in your next post.

Jim

---


---
title: "Accessing the network requires root"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by bubblenut on 2007-03-20
I have been a Kubuntu user for a couple of years now. Yesterday I installed Ubuntu (Edgy) and it's working well apart from the fact that all Internet applications need to be started as root. If I start Firefox by clicking the Firefox button in the top bar I cannot access the Internet, but if I fire up a terminal and start Firefox with "sudo firefox" I can. Similarly, if I start Gaim through the Applications menu it doesn't see the network, but if I start it with "sudo gaim" it works fine.

What can I do to change this?

Thanks
Rob

---

### Post by bubblenut on 2007-03-20
Horay, I've discovered the answer!
When I did the initial install I copied my resolv.conf over from my previous Kubuntu install. However, I had mounted the Kubuntu partition as root and as such resolv.conf was readable only by root.

---


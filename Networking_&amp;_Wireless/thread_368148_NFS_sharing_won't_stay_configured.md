---
title: "NFS sharing won't stay configured"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Eschatokyrios on 2007-02-22
I have a desktop with SuSE 10.1 and a laptop wiht ubuntu 6.06. I have a crossover ethernet cable between the two, which is represented by eth0 on both of them. Both computers are also on the same wireless network, wlan0. I want to share a /media/hdc2 on the ubuntu computer between the two over the ethernet cable, and not over the slow wlan.

I went system>administration>shared folders, and added /media/hdc2. I set it to share with NFS, and I added hosts in the eth0 network in the allowed hosts section. It had hosts in wlan0 network there by default, which I removed. But when I go onto the SuSE computer, its NFS client utility can't see the laptop or the nfs server. And when I go back into the ubuntu shared folders dialogue, I find that the settings for /media/hdc2 have been reset to just allowing hosts in the wlan0 network. What gives, and how do I fix it?

---


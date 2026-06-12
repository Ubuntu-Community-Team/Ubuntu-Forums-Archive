---
title: "How to check if I'm in a specific network"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by Muffe on 2007-02-10
I have a small network at home with a server and a few PCs. Some of my files are stored on that server, and I also use it for backup purposes.

What I want is a bash script (or at least a part of it) that checks if I'm connected to my home network (if a **specific** machine is available on 192.168.1.1 (or another address)). How do I do that in the best way? It does not help to ping 192.168.1.1, and see if I get a reply, because I could for example be connected to a friend's network. I need to do this in a relatively safe and quick way on each boot. The boot process must not be delayed more than a very few seconds if I'm not at home either.

The plan is that after it has been confirmed that I'm on my home network, it will automatically mount some shares and start some backup scripts.

Thanks in advance.

---

### Post by spd106 on 2007-02-10
You could still use ping, but then check the arp cache for the MAC address. I know this can be spoofed easily, but what is the chance that someone would know what's going on?
You can also do this in one go with arping, though that will involve installing a new package.

---


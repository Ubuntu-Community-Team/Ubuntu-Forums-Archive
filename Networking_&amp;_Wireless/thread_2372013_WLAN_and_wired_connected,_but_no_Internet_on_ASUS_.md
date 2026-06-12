---
title: "WLAN and wired connected, but no Internet on ASUS ROG G751JY"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by The Bright Side on 2017-09-20
Hey guys! Bought myself a used ROG G751JY gaming laptop and already have Windows 10 on it, all set up and configured. Now, I'm trying to install Ubuntu. UEFI, Secure Boot and Fast Boot off. I'm in a live session right now to do some preps, but I can't get online.

Both wired and wireless are connected. I can access my router by going to 192.168.1.1, and everything is hunky dory there. Plus, my desktop PC is online. Plus, when I boot into Windows, everything works.

But when I try to actually access the Internet from the Ubuntu live session: no dice.

Any ideas what I could do? Any help is appreciated at this point, I really couldn't find any good troubleshooting steps for this situation so far.

---

### Post by The Bright Side on 2017-09-20
Found a solution!

[https://askubuntu.com/questions/907763/ubuntu-17-04-connected-to-wifi-but-cant-browse-internet](https://askubuntu.com/questions/907763/ubuntu-17-04-connected-to-wifi-but-cant-browse-internet)

Had to do both the DNS thing and then *sudo service network-manager restart*.

---


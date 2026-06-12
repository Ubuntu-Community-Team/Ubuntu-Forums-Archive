---
title: "Prioritizing wireless networks with network-manager"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by AusIV4 on 2007-04-23
I use KNetworkManager on my Kubuntu installation. I'm a student, and when I'm at my dorm, I want my laptop to connect my personal network, but when I'm out and about, I need it to connect to the campus network.

The problem I'm having is that my campus wireless network has a fairly weak signal in the vicinity of my room, and about half the time my laptop will connect to the campus wireless instead of my network. All I have to do to fix it is click on the icon and select my network, but then it takes about 15 seconds to connect.

This isn't a huge issue, but it would be nice if I could tell it to connect to my network if its available and the campus network if it's not. So far, I haven't seen any way to do this.

Any tips?

---

### Post by spd106 on 2007-04-25
At the moment there isn't a solution to this, Network Manager will automatically connect to the last network, it does this based on the time stored in gconf. 
See [http://mail.gnome.org/archives/networkmanager-list/2007-April/msg00007.html](http://mail.gnome.org/archives/networkmanager-list/2007-April/msg00007.html)

So I'm afraid you are stuck with this at the moment.

---


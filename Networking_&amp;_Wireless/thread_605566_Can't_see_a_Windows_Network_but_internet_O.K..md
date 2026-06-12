---
title: "Can't see a Windows Network but internet O.K."
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by trumants on 2007-11-07
I installed Ubuntu 7.10 which is connected to a windows newtwok by ethernet cable.  I have access to the internet, but I can't see any of the other computers on the network.  What am I missing?

---

### Post by callan79 on 2007-11-07
> **trumants said:**
> I installed Ubuntu 7.10 which is connected to a windows newtwok by ethernet cable.  I have access to the internet, but I can't see any of the other computers on the network.  What am I missing?

Hi There,

I've found that the 'network neighborhood' functions within Windows sometimes would not show all the machines, and I have found that the 'browse network' function within Ubuntu is much the same in that it might be unpredictable (especially if your Windows machines have a firewall).

So what you need to do is find out the IP Address of a Windows computer on the network, say 192.168.1.21.

Then on your Ubuntu computer go to PLACES >> Computer, click the button on the left so you can see an address bar rather than buttons. In the address bar, erase everything and type in smb://192.168.1.21, or whatever the IP is of the Windows machine.

Once you have that working, you can set up proper mount points so it appears on your places menu, you'll need to install the smbfs package before you can do this.

Good luck :)

Callan

---


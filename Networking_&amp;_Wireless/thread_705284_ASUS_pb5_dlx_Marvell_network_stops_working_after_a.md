---
title: "ASUS pb5 dlx: Marvell network stops working after a while"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by kwaanens on 2008-02-23
Hello there.

I have been using this mobo for quite a while with Gutsy, but I'm experiencing problems now. Ethernet works fine on upstart, but when leaving the computer on for some hours (typically I realise this the next morning), the network is not working, meaning I can't get online, and there is no way I'm able to connect via VNC from my laptop.
However this used to work just fine.
I typically leave it on with only Ktorrent running (although I'm using Gnome). Networkmanager has the active network icon on. Clicking on it and just choosing the same network brings me back online within 5 secs.

Some vital info:
$ lspci | grep Ethernet
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

Both connectors work the same way.
The computer is not set to sleep or hibernate at any points (moving the mouse brings back the computer instantly).

The computer is otherwise running with a core2duo on 64 bit Gutsy. The GPU is an Nvidia 7600 GT.

---


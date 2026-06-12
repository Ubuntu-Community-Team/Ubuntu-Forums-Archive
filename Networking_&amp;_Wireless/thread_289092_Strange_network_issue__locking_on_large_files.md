---
title: "Strange network issue:  locking on large files"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by tagren on 2006-10-30
I have something very strange going on.  I have just installed Ubuntu 6.1 (Edgy Eft) 32 bit on a Gateway Laptop (7510GX).

It has a Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller.  

The network works just fine for browsing the net (Firefox 2.0), but as soon as I do anything network intensive (Add Applications or fire up Evolution, etc), the ethernet (wired) locks up.  I have to disable and enable the network to get it going.

When it happens, I get a message like this in /var/log/messages:

Oct 30 13:53:20 localhost kernel: [17182088.708000] sky2 eth1: rx error, status 0x670002 length 103

I have verified that it happens regardless of which port on my hub is being used.  All other machines in the network still have connectivity.

Does anyone have any idea why this might be happening?

Thanks.

Tagren Hawk

---

### Post by tagren on 2006-11-01
Another thing happened.  After I had been browsing a while the connection died.  This didn't used to happen in Fedora Core 4.  I wanted to try out Ubuntu, but if I can't get this fixed I might have to go back.  Help!

Is no one else seeing this?

---


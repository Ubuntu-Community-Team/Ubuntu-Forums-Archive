---
title: "[Wireless] Connection fine at startup but stops working whilst still connected"
date: 2015-01-30
forum: Networking &amp; Wireless
---

### Post by sam114 on 2015-01-30
I'm using a wireless adapter to connect to my router, the connection is fine at startup I can connect to my router access it's settings and browse the web. The connection then just stops working. 

I try to connect to the router main page and it is unable. However Ubuntu still says I'm connected to my router and my other windows system has no trouble.

The problem can be fixed by disconnecting then reconnecting in Ubuntu without rebooting but the problem occurs again shortly after.

A real pain, can anyone offer any insight?

Edit: I'm using Ubuntu 13.10 by the way

---

### Post by Retro_Trinity on 2015-02-01
Interesting, same problem on this end (Lubuntu 14.10) with a generic RTL8187 USB NIC.  Pulling the NIC and letting it sit for awhile seems to get it working again, though it will quickly fail in the same fashion as yours unless a fan is pointed at it.  It tends to get pretty warm which is when it begins to fail under Lubuntu.

The other odd thing about it is that it seems to do okay with long sequential downloads, such as a file download, so long as the download starts before failure conditions begin (again, using a fan helps), though it is still erratic and it still wants a fan pointed at it for prolonged operation in this manner  Sometimes it spontaneously stops downloading, waits for a bit, and then starts again.  But web browsing breaks down quickly.  It seems to have issues with DNS once failure conditions begin as well.  Use of ping indicates some packet loss once it starts to get cranky, and if it goes for too long, it may refuse to send packets to the router at all, and even spontaneously disconnect (it will sometimes disconnect after several hours of downloading).

In Windows 7 or Windows 10 preview, it runs just fine using an RTL8187L driver, no matter how warm it gets or anything else.

edit: If you are using an RTL8187 as well, you may find these links to be handy:

[http://askubuntu.com/questions/453110/rtl8187-wireless-card-drops-signal-within-seconds](http://askubuntu.com/questions/453110/rtl8187-wireless-card-drops-signal-within-seconds)
[http://www.backtrack-linux.org/forums/showthread.php?t=54375](http://www.backtrack-linux.org/forums/showthread.php?t=54375)

No idea if this is going to work for the cranky NIC on this end, but it might help you.

---


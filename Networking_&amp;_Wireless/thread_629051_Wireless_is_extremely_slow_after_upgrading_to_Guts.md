---
title: "Wireless is extremely slow after upgrading to Gutsy"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by mssever on 2007-12-01
I have a Broadcom 4306 wireless card, and I've been successfully using the bcm43xx driver from Dapper until now. Since I've upgraded to Gutsy, I've had intermittent extreme wireless slowdowns. For example, I've seen ping times as high as 10 seconds (average 2-4 seconds) when pinging my desktop computer. By comparison, when I plug into a wired connection, ping times are usually under 2 ms. Of course, I expect slower times when wireless, since the connection is slower, but 4 seconds makes the network useless.

Sometimes, like right now, the wireless network behaves itself. Often--especially after I've been connected wirelessly for a while--it acts up. I'm at my wits' end trying to figure out what could be the problem. Any ideas?

---

### Post by AJB2K3 on 2007-12-02
Join the club, its a know fault but try wifiradar instead of nm_applet as the connection manager.

---

### Post by mssever on 2007-12-02
So does that mean that the bug is in NetworkManager? I couldn't get wifi-radar to work (and it's a lame program, anyway, requiring extensive configuration of stuff it should be able to figure out on its own). The docs are inadequate, and the interface gives false information. For example, when I hit the connect button if I'm using a static IP, it says that it connects, but ping says, "Network unreachable." Obviously, then, it isn't connected.

---


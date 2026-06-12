---
title: "special/odd network"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by Akacko on 2007-10-27
Hi,
i've got a big problem (hope it's a big problem just for me). I have 3 PCs at home ([sketch](http://www.imagehosting.com/out.php/i1305201_connection2.gif)).

If i want to have internet on my laptop or 2nd PC i have to solve it ([ this way](http://www.imagehosting.com/out.php/i1305181_connection1.gif)).

But i want to have internet connection on all my PCs. And the only way i can do it is ([ this way](http://www.imagehosting.com/out.php/i1305142_connection.gif))

The problem is that i don't know how to configure all PCs and ethernet broadband router. 

I can connect to router 4 LAN cables and 1 internet connection (LAN cable). But my DSL router has USB connection. So i can't do it like this: DSL router -> ETH router -> 3PCs.


can you help me to configure my LAN network?

---

### Post by netztier on 2007-10-27
> **Akacko said:**
> can you help me to configure my LAN network?

Is that DSL Router actually a Router? or is it just a modem?

What you could do is this:

Use XP as a "router": connect the USB-DSL device towards the internet, and connect a Hub or switch instead of the broadband router to the internal NIC. Then you have to activate "Internet Connection Sharing" on the XP box - which you probably already have. This is something that definitely will work, but since the setup depends on the XP box, it is probably not what you want.

The other solution: find a broadband router that has a built-in DSL Modem and a DSL Port as it's "WAN Port" (instead of Ethernet), and a 4-port switch for the LAN. This is probably the best solution there is.

A third solution: find an older DSL Modem or DSL Bridge (or an old DSL Router configured as Bridge that has a single Ethernet LAN port instead of an USB Port. You should be able to connect that port to the WAN-Ethernet port of the broadband router you already have.

best regards

Marc

---


---
title: "How to get wired to trump wireless when both present"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by teachop on 2007-05-13
On my Acer Aspire w. Atheros I cannot use Network Manager.  It constantly disconnects and reconnects and is slow and useless.  With Network Manager disabled in Sessions, the wireless is stable and fast.

That being said, I have a problem, in that when I plug into the ethernet here at home, the laptop still connects on the wireless.  The ethernet connection is alive, but it doesn't use it.  If I disable the wireless, then the ethernet gets used.  I have tried changing the order of stuff in /etc/network/interfaces.

What I want it to do is to connect to the wired link if available, and then the wireless is the second choice.  Maybe that cannot be done without Network Manager?

(I also cannot get vpn working without Network Manager but that is for another post another day...)

P.S.  Network Manager works fine at work, where there are only two access points visible.  At home I can see sometimes seven.  Since ath0 is stable and fast with manual config, I suspect the root of the problem is whatever Network Manager is trying to do in support of roaming.  A guess...

---

### Post by spd106 on 2007-05-13
I'm not quite sure why you still need the wireless connection if you are plugged in, but that's no reason to avoid the question.

The problem you are probably having is the default route assignment. There isn't really a simple way to handle this, that's why network manager was developed. You can modify the /etc/network/interfaces file to change the default route when a new interface is added, but this is tricky to achieve unless you know what you are doing.

The tool to use is probably "ip" or the older "route" tool, it will show you the current routing table and allow you to modify it to your own design.

---

### Post by teachop on 2007-05-13
Thank you for the reply.  I was not clear.  I don't want to use both at once.  My Windows laptop uses the wired network if it is connected, else uses the wireless.  I take no steps for that, it is automatic.  I believe the Network Manager would do that for Ubuntu if it worked correctly on this wireless adapter, but it doesn't.  I am looking for a way that the Ubuntu laptop will use the wired link if it is available, and if not, will use the wireless, without the need to manually reconfigure the settings.  Maybe that is not possible without Network Manager in place?

---

### Post by spd106 on 2007-05-13
Sorry, I'm afraid you will have to disable the wireless interface manually.

---

### Post by teachop on 2007-05-13
Ok.  Thanks for the info.

---


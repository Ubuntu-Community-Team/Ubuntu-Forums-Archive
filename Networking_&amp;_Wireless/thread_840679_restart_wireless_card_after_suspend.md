---
title: "restart wireless card after suspend?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by gopher38 on 2008-06-25
Hello, small question, but annoying.

I'm running Hardy on a laptop with a Linksys WPC54G versionn 2 wireless card.  I use WICD. Everything seems to work well, but if I suspend the PC and then bring it back, the wireless connection is gone. However, if I physically remove the card and then put it back, it will reconnect.  On the other hand, exiting WICD and restarting doesn't work.  

I'm wondering if there's a command line command that I can use to make it re-search for the card without having to physically remove it.  I figure if I can find that, there's probably an RC level something that I can add it to in order to get wireless back automatically.

Thanks.

---

### Post by nixscripter on 2008-06-26
One common suggestion: try restarting the Network Manager Applet. I don't know about card detection, but it can solve problems with the driver being in a bad state:

```

/etc/dbus-1/event.d/25NetworkManager restart
/etc/dbus-1/event.d/26NetworkManagerDispatcher restart

```

Hope this helps.

---

### Post by gopher38 on 2008-06-26
Thanks for the tip.  I'll try that next time I suspend and post back if it works.  Thanks in advance in any case though.

---


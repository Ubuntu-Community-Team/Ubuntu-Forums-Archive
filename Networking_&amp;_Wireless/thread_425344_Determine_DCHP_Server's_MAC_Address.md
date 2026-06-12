---
title: "Determine DCHP Server's MAC Address?"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by thornomad on 2007-04-27
Is there a way from the command line that I can, in effect, ping my DCHP server and see what MAC address the server is using ?  I need a way to determine, via a script, if I am connected to my home network or not ... when I travel, I want my computer to behave different when it is on a different network.

Thanks,
Damon

---

### Post by deadlines on 2007-04-27
```
 $ arp -n <ip address or hostname>
```

Actually you can probably do without the '-n' option and be just fine, just "man arp" to see the various switches.

Cheers

---


---
title: "linksys network pc card wpc11 suddenly stopped working"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by cal66 on 2007-08-16
Hello,

I'm running Feisty Fawn and the Linksys WPC11 card had been working fine until this morning.  When  I booted it said the disk hadn't been scanned in 25 starts, so it ran the scan and the card has worked since.  Not sure if it's related.  

Any advice would be very appreciated.  I'm very new to linux.

---

### Post by noob12 on 2007-08-16
People on the forum can help but you'll need to provide some more info about your situation.

Can you post the output of these commands for starters?
```

lspci -nn

sudo lshw -C network

ifconfig -a

dmesg

```

---


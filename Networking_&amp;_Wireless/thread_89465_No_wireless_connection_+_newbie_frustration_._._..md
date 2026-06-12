---
title: "No wireless connection + newbie frustration . . ."
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by just1m on 2005-11-12
I just got breezy working, want to get my wireless up. I have a Netgear WG311T in my PC. The OS reads the card and says it's connected but I am unable to get a website. Any thoughts?

---

### Post by Lambert on 2005-11-12
Have you tried to ping the router and (if available) any other  pcs you may have connected to the network?

Open a terminal and post the results of
```
iwconfig
```

Also type this and see if you get any output

```
 cat /etc/resolv.conf
```

If you get nothing you will need to set up a dns server.

---


---
title: "Problems with Wired Network - Realtek"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by neoghost on 2008-01-19
Hey Everyone

new to ubuntu, great system, works smooth on my pentium III (server)
one problem i didn't solve is the networking card problem
i can connect to the internet and local network, but after 5 minutes of work, the network seems to disconnect.
if i do network restart. all is back for another 5 mins.

if i use my windows xp, all is working fine without problems...

Please help me, i don't want to use my windows station...

---

### Post by evanchu on 2008-01-19
You have asked a very broad question.  Let's see if we can narrow it down.
Run each of the following commands and post its output.
```

ifconfig
route -n
cat /etc/resolv.conf
cat /etc/hosts

```

---


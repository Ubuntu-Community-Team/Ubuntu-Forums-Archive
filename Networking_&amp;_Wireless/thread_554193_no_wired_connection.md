---
title: "no wired connection"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by gmcallis on 2007-09-18
I had feisty installed, but was having some hang up issues, so thought I'd re-install. Oddly, I couldn't seem to get wireless connection to work before, now I don't see a wired connection in network manager ??
Any commands or tips appreciated.. 
btw - i didn't have the network cable plugged in on the first attempt, so plugged it in on the second - still no joy (Toshiba P30 laptop)

---

### Post by noob12 on 2007-09-18
Post the results for help:

```

lspci -nn

sudo lshw -C network

ifconfig -a

cat /etc/network/interfaces

```

---


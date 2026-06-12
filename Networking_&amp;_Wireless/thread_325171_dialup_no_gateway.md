---
title: "dialup no gateway"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by ernestmogg on 2006-12-25
I'm having great difficulty in getting my external serial modem to access websites. Although it appears to connect properly using kppp I cant' browse the internet. If I try nslookup for any site I might get a correct answer once or twice but then it fails. After a few minutes the line drops by itself.

Before I try to connect "route -n" shows no entries at all. After connecting it shows only two lines something like:

194.247.47.5  0.0.0.0    255.255.255.255  UH   0   0   0  ppp0
0.0.0.0           0.0.0.0     0.0.0.0                  U     0   0   0  ppp0

That bottom line looks definitely odd to me, where's the remote peer? There doesn't seem to be a default gateway although I have ticked "Default Gateway" and "Assign the default route to this gateway" in kppp's Gateway tab.

I've trawled the forum pages and the internet in general for days and can't find any answer to my problems. I've tried wvdial with just the same results. Anyone have any pointers?:-k

---


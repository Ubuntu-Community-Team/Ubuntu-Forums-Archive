---
title: "Firefox not starting up."
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by baldwinian on 2007-05-13
I am running Ubuntu 6.10 and (Edgy Eft) and have managed to laod the RT61 dirvers fro the Ralink chipset on the Linksys wireless card. iwconfig recognises the card. iwlist ra0 scanning detets the card...but Firefox comes up empty handed! Help!!! I am frustrated.
Thanks!

---

### Post by mssever on 2007-05-14
> **baldwinian said:**
> I am running Ubuntu 6.10 and (Edgy Eft) and have managed to laod the RT61 dirvers fro the Ralink chipset on the Linksys wireless card. iwconfig recognises the card. iwlist ra0 scanning detets the card...but Firefox comes up empty handed! Help!!! I am frustrated.
Thanks!

Please post the output of ```
ifconfig
```

Also, can you ping? Try ```
ping google.com
``` and see if you get replies. (Ctrl+C cancels ping--and most other command-line programs--if it's running for to long.)

---


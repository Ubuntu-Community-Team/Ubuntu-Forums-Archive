---
title: "What?"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Dvorakis on 2008-11-01
Ok,so I recently installed ibex on my machine...clean install...and my wireless card is supported...so I figured it would be fine.I had trouble with ibex saying my wireless card was disabled...and nobody could help me. So after reinstalling hardy and connecting the same way as always I figured out that even now internet on hardy won't work...even when im connected?

whats going on...

---

### Post by Kevbert on 2008-11-01
It's possible that your wireless driver has been blacklisted since you first installed on Hardy and therefore Intrepid by default. What's the output of
```
lspci
iwconfig
```

---


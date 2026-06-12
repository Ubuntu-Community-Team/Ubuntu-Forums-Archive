---
title: "nm-applet icon does not stay"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by ziggie216 on 2007-06-04
it seems like i have to manually run nm-applet in terminal w/o closing it in order to keep the icon near the clock to stay there. Is this suppose to happen?

---

### Post by spd106 on 2007-06-05
That shouldn't be necessary. Is it listed in the start-up tab of your sessions capplet? If not, add it.

You can also start it up by pressing Alt+F2, then running ```
nm-applet --sm-disable
```

---


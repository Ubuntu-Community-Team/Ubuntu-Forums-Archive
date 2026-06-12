---
title: "setting the default wireless network"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by EngDrewman on 2007-11-11
How do you change the order of preferred wireless networks? I know about using gconf-editor to delete keys, but that won't work because I need to be able to connect to both.

---

### Post by spd106 on 2007-11-12
You can't as such, NM automatically connects to the most recent network it's used that's currently available.

So unless you want to play around with the time info in gconf, all you can do is select the ssid after you log in.

Perhaps NM 0.7 will have more options when it's released.

---


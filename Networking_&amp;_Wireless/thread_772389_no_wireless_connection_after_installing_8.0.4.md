---
title: "no wireless connection after installing 8.0.4"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Alexcon on 2008-04-28
Hi
After installing 8.0.4 everything worked perfectly exept for my wireless internet connection. My lenovo laptop sees the network and connects to it in roaming mode but only at 0%, and I have been unable to connect to the internet since install.
What to do?

---

### Post by chili555 on 2008-04-28
First, find out which chipset you have:```
 sudo lshw -C network | grep ireless
```If you find out it's the lovely 3945ABG so common on newer Lenovos, search this forum and see the fix. Please post back if we can help.

---


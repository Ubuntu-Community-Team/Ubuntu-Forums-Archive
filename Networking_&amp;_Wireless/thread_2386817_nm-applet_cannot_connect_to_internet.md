---
title: "nm-applet cannot connect to internet"
date: 2018-03-10
forum: Networking &amp; Wireless
---

### Post by o-pos2 on 2018-03-10
Hello,

I just installed Lubuntu 17.10 on my laptop. Initially (at lest when I was at work) internet worked fine. At home, I can see that nm-applet connects to the wi-fi network but it doesn't load anything and the browser states "server not found". Of note, two my other computers at home connect to wifi just fine. Any suggestions where to start and how to solve this?

---

### Post by wildmanne39 on 2018-03-10
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by o-pos2 on 2018-03-10
Solved the issue by editing the file '/etc/resolv.conf' and adding the line 'nameserver 8.8.8.8'

---


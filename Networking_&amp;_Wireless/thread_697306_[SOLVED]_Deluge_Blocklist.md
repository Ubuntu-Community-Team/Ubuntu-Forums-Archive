---
title: "[SOLVED] Deluge Blocklist"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by Aquaman420 on 2008-02-15
When I installed the blocklist plugin a message popped up saying "Deluge was expecting a gzip file but did not get it"  or close to it.  Here is my blocklist.conf.  If someone could tell me what is wrong/missing that would make my week.  Thanks once again.  Version is 0.5.8.4.

```
(dp1
S'url'
p2
S''
sS'listtype'
p3
S'p2bgz'
p4
sS'load_on_start'
p5
I00
s.
```

---

### Post by Aquaman420 on 2008-02-15
Ok after searching other sites I figured it out.  You have to delete your blocklist.conf found in /home/username/.config/deluge.  Then you can go into Deluge's gui and fix it from there.  plugins<blocklist_importer<preferences. And you can find the lists on Deluge's site and fill in the details in the dialogue box that pops up.

---


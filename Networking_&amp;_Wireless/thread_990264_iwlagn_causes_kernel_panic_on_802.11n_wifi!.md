---
title: "iwlagn causes kernel panic on 802.11n wifi!"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by skyggen on 2008-11-22
Hey. I got myself a new router today and now i get kernel panics all over the place! When i start downloading stuff the panics start and the caps lock start to blink.

I found bugreports for the same problem with intrepid, the iwlagn driver causes panics on 802.11n wifi networks. but i am using hardy.
How can i fix this please?

---

### Post by clietz on 2008-11-23
There is a workaround posted in the release notes for 8.10 here-
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)
look for 'System lock-ups with Intel 4965 wireless'.  Just installed the backports hoping it resolves the same for me.

---

### Post by skyggen on 2008-11-25
> **clietz said:**
> There is a workaround posted in the release notes for 8.10 here-
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)
look for 'System lock-ups with Intel 4965 wireless'.  Just installed the backports hoping it resolves the same for me.

How did it go?

---


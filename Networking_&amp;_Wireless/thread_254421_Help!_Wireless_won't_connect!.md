---
title: "Help! Wireless won't connect!"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by ThrobbingBrain66 on 2006-09-09
Has anyone had a situation where wireless will work with kubuntu but not ubuntu?  thats the problem i have now.  when i ran kubuntu only, i never had trouble with wireless.  when i ran both ubuntu and kubuntu, the only way i could get wireless to work in ubuntu is to set the essid and wep key in kubuntu.  now that i only run ubuntu, i cant get it to work at all.

the problem is that no matter how many times i enter the essid, it gets truncated.  this is at my girlfriends apartment, so the essid is "Jill&Laura".  but if i go back in to the properties it always gets shortened down to only "Jill".  I'm attempting to play with my /etc/network/interfaces file right now, but not having any luck.

thanks for any help!

---

### Post by lukew on 2006-09-10
I would not use something like &. Stay aware from reserved characters. I am not saying that it is in this case but something is causing you problems and looking at that I suspect it is that.

You can always try and escape the & with \& but I would just stay away from &!!!

Luke

---


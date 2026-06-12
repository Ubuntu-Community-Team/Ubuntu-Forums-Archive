---
title: "Realtek RTL8111/8168 Wireless problems - no wireless detected."
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by spdmrphy on 2014-03-04
I've been struggling to get my wifi up and running, but the 8111/8168 shows up as a wired connection "cable unplugged" and wont detect any wifi networks at all. 
I have followed ssolutions for similar issues which involved installing alternate realtek drivers, but to no avail.
 
Being a bit of a newbie, I'm at a loss as to how to tackle this issue other than following solutions and walkthroughs from forum posts, but I seem to have run out of options on that front so it's time to beg for help!!

Is there any more info I can post to help you figure this out?

Thanks,
Spud

---

### Post by chili555 on 2014-03-04
> but the 8111/8168 shows up as a wired connection "cable unplugged" Because that's exactly what it is. Your wireless is something different. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my keyboard on the same key with \. Thanks.

---


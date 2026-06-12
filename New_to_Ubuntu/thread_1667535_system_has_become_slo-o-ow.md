---
title: "system has become slo-o-ow"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by wog on 2011-01-15
How do I track down whatever's bogging down my system so I can do something about it?

---

### Post by hansdown on 2011-01-15
Hi wog.

Click system> administration> system monitor> processes.

Let it run for a while, and see what shows up.

---

### Post by wog on 2011-01-15
Thank you!

Can I Google processes to see what they are for, same as Windows? Where's a good site to look for such things?

---

### Post by zeroseven0183 on 2011-01-15
> **wog said:**
> Thank you!

Can I Google processes to see what they are for, same as Windows? Where's a good site to look for such things?

Yes, you can Google them. Although of course, most of them are different from what you will see in Windows. I don't of a particular site where these processes are listed and defined but I suggest you post here those you think seem to slow down your machine then we'll help you identify what are they and what you can do with them.

By the way, you can also monitor the processes through the Terminal by typing:
```
top
```

---

### Post by Nickjpost on 2011-01-15
This also helped me improve performance, though it my just mask your problem:
[https://help.ubuntu.ocm.community/SwapFaq](https://help.ubuntu.ocm.community/SwapFaq)

---

### Post by Nickjpost on 2011-01-15
sorry, duplicate post by mistake

---

### Post by wog on 2011-01-15
Beautiful.

Does gvfs-gdu-volume and gvfs-afc-volume run under normal circumstances, or is it time to change my password and restart my system?

---

### Post by wog on 2011-01-15
> **Nickjpost said:**
> This also helped me improve performance, though it my just mask your problem:
[https://help.ubuntu.ocm.community/SwapFaq](https://help.ubuntu.ocm.community/SwapFaq)

link is insecure. trying to go to it takes me to the Ubuntu Documentation page. another link?

---

### Post by zeroseven0183 on 2011-01-16
The link was mistyped. Here is the correct one [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by zeroseven0183 on 2011-01-16
> **wog said:**
> Beautiful.

Does gvfs-gdu-volume and gvfs-afc-volume run under normal circumstances, or is it time to change my password and restart my system?

Yes, I have both running on my laptop. Do those two consume the highest CPU and/or memory usage?

---

### Post by wog on 2011-01-18
I rebooted and now those two files aren't consuming the same amount of processor. Is there a way to find out which processes are used by which applications? I had a Windows program that did that, but I'm betting that wouldn't work here. :)

Thank you for all this advice, btw.

---


---
title: "top vs ps - CPU Usage"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by ittiam on 2010-04-28
Can someone explain as what is the difference between CPU% showed in top and in ps? I mean the way in which they are calculated. I can see each of these commands giving different numbers for the same process at the same instant.

---

### Post by wilee-nilee on 2010-04-28
> **ittiam said:**
> Can someone explain as what is the difference between CPU% showed in top and in ps? I mean the way in which they are calculated. I can see each of these commands giving different numbers for the same process at the same instant.

They are two different programs running at different intervals of read.

---

### Post by ittiam on 2010-04-29
And I would assume top samples at a higher rate. top always shows me low CPU% compared to ps and the difference is quite big. For the process I tested with top showed around 1% whereas ps showed around 20% and the value showed by ps was exactly the same for 5 minutes I monitored whereas top was fluctuating between 0-2%.

Why this big a difference? And how to interpret the CPU usage from ps compared to that of top?

---

### Post by Funnnny on 2010-04-29
top is realtime.
ps is the average CPU in an interval.

---


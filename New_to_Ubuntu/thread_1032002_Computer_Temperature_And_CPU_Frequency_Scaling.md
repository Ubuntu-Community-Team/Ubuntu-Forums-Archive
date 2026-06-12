---
title: "Computer Temperature And CPU Frequency Scaling"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by furialis on 2009-01-05
I have just installed CPU frequency scaling monitor and Computer temperature monitor.

First question is how do I find out what temperatures are being monitored? They are listed as hwmon0(1,2,3) and hwmon1(1,2,3). I also selected Kernel i2c sensors. Am I wrong in my assumption that the highest temp one is the CPU?

Question 2, is there anything wrong with leaving the CPU at max? It was originally set to Ondemand, but I set it to the max with no noticable difference in temperature. However there was a significant difference in response from my programs starting. Is there any chance that I'll damage my CPU?

---

### Post by coolbrook on 2009-01-05
You'll see more detail in terminal by typing

sensors

---


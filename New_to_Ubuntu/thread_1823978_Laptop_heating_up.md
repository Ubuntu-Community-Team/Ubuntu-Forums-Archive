---
title: "Laptop heating up"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by spirited on 2011-08-12
I am using a Asus F8S with Intel Core(TM)2 Duo CPU T8300@2.40GHz 3GB RAM , just upgraded to ubuntu 11.04 however I notice my laptop heating up more significantly that when I am using an windowsVista. Is there a solution to the problem or is it a bug? Thanks for the help.

---

### Post by LowSky on 2011-08-13
Its kinda a kernel issue.. The next release you will notice things run much cooler, and battery life will increase as well.

---

### Post by kaldor on 2011-08-13
> **LowSky said:**
> Its kinda a kernel issue.. The next release you will notice things run much cooler, and battery life will increase as well.

I do not agree. It varies.

What graphics card do you use? If it is NVIDIA or ATI/AMD, install the proprietary drivers. If it's Intel, it might just be a regression like implied.

---

### Post by el_koraco on 2011-08-13
First, install cpufrequtils

Then run [FONT=Verdana]

[/FONT]```
[FONT=Verdana][/FONT]sudo cpufreq-set -g ondemand
```

If it doesn't help, try [URL="http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972"]this
[/URL]
You may need to upgrade the kernel in order to have everything working.

---

### Post by kaldor on 2011-08-13
Or, it could just be the lack of power/heat management in the open source graphics drivers.

---

### Post by akand074 on 2011-08-13
> **kaldor said:**
> I do not agree. It varies.

Although it does vary. There is an overheating problem that was introduced in kernel 2.6.38 and is still not fixed in kernel 3.0.0. Apparently it causes up to a 33% increase in power consumption, though not everyone has reported to have been affected by it which suggests that it only occurs with particular hardware I'd imagine. I'm not very familiar with the details of the issue but I've seen articles and posts in this forum about it.

---

### Post by kaldor on 2011-08-13
> **akand074 said:**
> Although it does vary. There is an overheating problem that was introduced in kernel 2.6.38 and is still not fixed in kernel 3.0.0. Apparently it causes up to a 33% increase in power consumption, though not everyone has reported to have been affected by it which suggests that it only occurs with particular hardware I'd imagine. I'm not very familiar with the details of the issue but I've seen articles and posts in this forum about it.

I'm running kernel 2.6.38 and 2.6.39. Temperatures are super low, and power consumption no more than usual. Under load, my desktop heats to ~25 celcius. It idles as low as 12 to 15 degrees.

I highly recommend the proprietary drivers in the Additional Hardware application, as this can make a huge difference on laptops.

---

### Post by joncorp on 2011-08-13
just but an external ventilator for laptops and it should be fine

---

### Post by akand074 on 2011-08-13
> **kaldor said:**
> I'm running kernel 2.6.38 and 2.6.39. Temperatures are super low, and power consumption no more than usual. Under load, my desktop heats to ~25 celcius. It idles as low as 12 to 15 degrees.

I highly recommend the proprietary drivers in the Additional Hardware application, as this can make a huge difference on laptops.

I haven't noticed anything either. I'm just mentioning what I've heard, and not prematurely overlooking a kernel issue.

---


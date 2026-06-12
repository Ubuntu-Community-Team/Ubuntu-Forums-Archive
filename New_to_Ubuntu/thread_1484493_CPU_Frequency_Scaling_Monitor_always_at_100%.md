---
title: "CPU Frequency Scaling Monitor always at 100%"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by occams_beard on 2010-05-15
Hi,

I have a fresh install of Lucid, and it appears that my cpu is freq is not scaling down. I have the CPU Frequency Scaling Monitor applet on my panel, and after a couple hours of usage it stays stuck at 100%. This is the case even if my cpu usage is at 0%, with nothing running.

In previous versions of ubuntu I hardly ever saw the cpu scale up to 100%. Only during a cpu high load, like it should. 

How can I check if the cpu is actually throttled or not? 


My cpu is a Core 2 quad Q6600.

Any advice?

---

### Post by -humanaut- on 2010-05-15
I could be wrong here because I use AMD, but are those even Scalable the last Pentium chip I used wasn't but that was also a Prescott chip.

---

### Post by occams_beard on 2010-05-15
Yes, they are indeed scalable.

It scales down to 1.6 Ghz when idle, and then scales up to 2.4ghz under a load.

For some reason it gets "stuck" at 2.4ghz, even when there is nothing using the cpu.

I am not sure if it's just the panel applet, or if the cpu is actually not scaling down.

---

### Post by -humanaut- on 2010-05-16
> **occams_beard said:**
> Yes, they are indeed scalable.

It scales down to 1.6 Ghz when idle, and then scales up to 2.4ghz under a load.

For some reason it gets "stuck" at 2.4ghz, even when there is nothing using the cpu.

I am not sure if it's just the panel applet, or if the cpu is actually not scaling down.

Ok, thanks for letting me know. I was messing around with the Panel Applet last night and I'd honestly believe that might be the problem mine would consistently bounce between 2.2ghz and 1ghz when my computer was basically Idol and the system resource manager would show no spike in usage that would represent such a radical bounce.

---


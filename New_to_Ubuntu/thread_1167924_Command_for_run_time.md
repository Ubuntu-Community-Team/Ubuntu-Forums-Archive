---
title: "Command for run time?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by peakshysteria on 2009-05-23
Is there a command so one can check the run time (up time) of the system/session?

---

### Post by _Purple_ on 2009-05-23
```
uptime
```

---

### Post by peakshysteria on 2009-05-23
I love you man:

```
19:58:36 up 28 days,  5:35,  2 users,  load average: 0.23, 0.67, 0.84
```

What does the load average mean? And do you have a good link to commands like this?

---

### Post by _Purple_ on 2009-05-23
System load averages is the average number of processes that are either in a runnable or uninterruptable state. Please check the man page for details:
```
man uptime
```
Are you looking for any other specific command?

---

### Post by eeeandrew on 2009-05-23
there was a post on here a few days ago with cheat sheet links. search the forum for "cheat sheet"

Hope this helps,
Andrew

---

### Post by mcduck on 2009-05-23
load average tells the system load as average over three different time spans, past 1, 5 and 15 minutes.

Simplified the load is counted like this: 1.0 equals single CPU core running at 100% load. But load can be higher than that, if you run a program that would do things faster if it only could, the load will be higher than 1. And if you run many programs that all use all the CPU power they can get the load will be even higher. So, load isn't same as CPU utilization. It tells about how much work the computer *would* do if it only was possible.

Also notice that if you have a dual-core processor, both cores running at 100% would equal load of 2.0. For quad-core the full load (without exceeding what the system can actually do) would be 4.0..

If you run "man uptime" you'll get a better definition for load values.

---


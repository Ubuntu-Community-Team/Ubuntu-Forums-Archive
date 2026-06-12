---
title: "Ubuntu 8.04 crashes consistently all of the sudden"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by masterofthemelee on 2008-12-09
I've been using Ubuntu on this laptop for four months, no problems, when all of the sudden (a few days ago) it began crashing about once an hour.

I have been unable to find a pattern for what triggers it except one: it only crashes when it is given user instruction.  It can sit there for days with the screen saver on, downloading a torrent or whatever, just fine.  The second I tell it to open firefox, close a window, change settings, or some other task it seems to stand a chance of crashing.

---

### Post by w4ett on 2008-12-09
Check /var/log/syslog and /var/log/messages for events related to your crash.

---

### Post by scott_g on 2008-12-09
I'd also run a memtest on your laptop...  Should be an option on the grub-boot menu.

Scott

---

### Post by Tatty on 2008-12-09
What sort of crash does it exhibit?  Is it a hard lock-up or something else?  Are there any sort of error messages given?

---

### Post by masterofthemelee on 2008-12-09
What am I looking for in the syslog?  The next time it has a problem I'll save everything roughly before and after the crash.

Also, it simply freezes.  The mouse still moves around the screen but the computer otherwise does not respond.

Also, today it had its first crash without me giving any input (during the screen saver).

Its a year old laptop that I've run three different operating systems on, I don't think its a RAM problem, soonest I will be able to try memtest is tomorrow night.

---

### Post by masterofthemelee on 2008-12-09
Akk, double post.

---

### Post by scott_g on 2008-12-09
> **masterofthemelee said:**
> Its a year old laptop that I've run three different operating systems on, I don't think its a RAM problem, soonest I will be able to try memtest is tomorrow night.

You never really know...  I had some ram go bad about 6 months after I bought my computer...  

Do you dual-boot at all?  Are the crashes specific to Ubuntu?  

Scott

---

### Post by masterofthemelee on 2008-12-09
Ubuntu is currently this computer's only OS.

Oh, and about that crash:

```
Dec  9 19:48:46 LAPTOP1 kernel: [11749.743273] CPU1 attaching sched-domain:
Dec  9 19:48:46 LAPTOP1 kernel: [11749.743275]  domain 0: span 03
Dec  9 19:48:46 LAPTOP1 kernel: [11749.743277]   groups: 02 01
Dec  9 20:05:58 LAPTOP1 -- MARK --
Dec  9 20:17:01 LAPTOP1 /USR/SBIN/CRON[6352]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  9 20:45:59 LAPTOP1 -- MARK --
Dec  9 20:59:53 LAPTOP1 syslogd 1.5.0#1ubuntu1: restart.
```

---

### Post by masterofthemelee on 2008-12-11
bump

---

### Post by vishal_mala on 2008-12-11
I also experienced this problem some while ago. But for me this problem came up when i changed my default human skin, and i corrected it by resetting my x graphics server and it worked fine. you  can try that by booting into the recovery mode (That is the second option below the normal boot) and then selecting fix x server from the grey screen that will subsequently comeup. hope this solves your problem. 
:guitar:

---


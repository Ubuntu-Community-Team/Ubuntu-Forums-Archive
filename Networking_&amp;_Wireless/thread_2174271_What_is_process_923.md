---
title: "What is process 923?"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by Rachel_Bunker on 2013-09-13
I'm trying to get my bluetooth running.  So, in effort to try to determine if bluetooth is even turned on, I typed sudo service bluetooth status.

I got [PHP]bluetooth start/running, process 923[/PHP]

What is process 923?

---

### Post by chili555 on 2013-09-13
Linux, including Ubuntu, numbers running processes on your system. They are sometimes called, PID; roughly, process identification. The exact number has no special significance. Here is an example from my machine:```
chili@Think410:~$ sudo service bluetooth status
[sudo] password for chili: 
bluetooth start/running, process 1245
```Your and my bluetooths (blueteeht??) are running.

---

### Post by Rachel_Bunker on 2013-09-13
Thank you!  Now if only I could get my bluetooth to actually work...

---

### Post by chili555 on 2013-09-13
> **Rachel_Bunker said:**
> Thank you!  Now if only I could get my bluetooth to actually work...I am no bluetooth student. They only let me play with the easiest questions here. I suggest you start a new thread and fully describe your trials so far, your devices, etc. Someone knows how to fix it.

---


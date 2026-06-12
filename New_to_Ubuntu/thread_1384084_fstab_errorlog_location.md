---
title: "fstab errorlog location"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ozzyprv on 2010-01-18
Where is the log of the error generated during fstab 'execution'.

A NFS share is not being mounted on start-up as per my fstab but I do not know what the error is.

Thank you.

---

### Post by cariboo on 2010-01-18
You should be able to find something in dmesg, or /var/log/messages.

---

### Post by ozzyprv on 2010-01-18
Could not find anything in either of those two.

---

### Post by ozzyprv on 2010-01-20
* bump *

---

### Post by eddified on 2010-01-20
I also need to know this...

update:
I don't need to know this because I fixed the fs mounting problem .. but it'd still be nice to know.

---

### Post by sandyd on 2010-01-20
if you run
```

sudo mount -a

```
. everything in the fstab will be mounted again.
errors are shown in the terminal

p.s. not likely, but have you checked the mess in /var/log/syslog?

---

### Post by ozzyprv on 2010-01-21
@Carlee,

Didn't see the error at ../syslog

But the command you suggested did the trick!

Thank you.

---


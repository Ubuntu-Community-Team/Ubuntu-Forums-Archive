---
title: "shutdown command does not work"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by ramly on 2010-05-01
Hi,

I installed 10.04 today, but when trying to shutdown the system, the shutdown command does not work- both graphical and command line. Please help - thanks in advance

Ramly

---

### Post by oldmankit on 2010-05-01
What happens if you type:
```
sudo poweroff
```

---

### Post by llamabr on 2010-05-01
Yes,  Copy the actual command, along with whatever error messages you receive.

---

### Post by karthick87 on 2010-05-01
Try

```

sudo init 0
```

---

### Post by anewguy on 2010-05-01
> **ramly said:**
> Hi,

I installed 10.04 today, but when trying to shutdown the system, the shutdown command does not work- both graphical and command line. Please help - thanks in advance

Ramly

So you've tried things like:

sudo shutdown -P now  -> to shutdown and power off

- or -

sudo shutdown -h now  -> to shutdown and either halt or power off (the system makes the choice)



Remember you must use the "sudo " and that everything is case sensitive (and yes, that is a capital "P" in the first example).

Dave

---


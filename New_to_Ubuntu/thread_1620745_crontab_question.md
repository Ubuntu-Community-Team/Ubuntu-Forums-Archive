---
title: "crontab question"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-13
i am just learning how to use crontab. and i know how to schedual jobs in either for either my daughter or myself. (we both have our own desktops). however how would i enter a job that will run for both if either is logged on.  eg. if i want the computer to shutdown at x time-this command would run regardless of who is logged on. did some google searching but i am lost/tks

---

### Post by CharlesA on 2010-11-13
You could always run it in a root crontab, but you'd get no prompt on the GUI that the machine is going to shutdown.

---

### Post by toekneewood on 2010-11-13
This is what I have in my root crontab.  First you need to edit the root crontab.  My Server will shutdown at 23:15hrs every night.  The BIOS turns it back on at 06:00hrs
```

sudo crontab -e

```Then add the following
```

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin

15 23 * * *  /sbin/shutdown -h now

```save and exit

---

### Post by rburkartjo on 2010-11-13
toe tks that is what i needed

---


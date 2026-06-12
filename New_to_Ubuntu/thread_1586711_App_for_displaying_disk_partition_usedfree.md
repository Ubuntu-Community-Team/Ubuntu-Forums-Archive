---
title: "App for displaying disk partition used/free?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by dkjMusic on 2010-10-02
...besides GParted that is...like the Windows bar graph shown in the attached screenshot.

---

### Post by surfer on 2010-10-02
what about 
System -> Administration -> Disk Utility
?

---

### Post by Darkness Des on 2010-10-02
Or Applications -> Accessories -> Disk Usage Analyzer?

---

### Post by dkjMusic on 2010-10-02
> **surfer said:**
> what about 
System -> Administration -> Disk Utility
?

It only gives total disk space, not used vs. free.

---

### Post by dkjMusic on 2010-10-02
> **Darkness Des said:**
> Or Applications -> Accessories -> Disk Usage Analyzer?

It only gives **total** disk used/free, not for individual partitions.

---

### Post by srs5694 on 2010-10-02
The text-mode df command does this job. I use it with -h:

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              30G  4.2G   24G  15% /
/dev/sda5             151M   19M  125M  13% /boot
/dev/sda4              80G  200M   80G   1% /home
/dev/sdb6              12G  6.2G  5.4G  54% /other/shared

```

I'm sure there must be a GUI equivalent (or more likely several of them), but I don't know offhand what it/they might be.

---

### Post by coffeecat on 2010-10-02
Places menu > Computer > right-click on mounted partition > Properties.

See screenshot.

---

### Post by dkjMusic on 2010-10-02
Thank you all for your replies.

I found what I was looking for in the Sysmonitor screenlet (Show disks sensor).

---


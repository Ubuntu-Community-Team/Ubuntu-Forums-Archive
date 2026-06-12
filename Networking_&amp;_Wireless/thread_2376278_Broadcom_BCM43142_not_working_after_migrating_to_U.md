---
title: "Broadcom BCM43142 not working after migrating to Ubuntu 17.10"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by weisz-michael on 2017-11-01
just updated from Ubuntu 17.04 to 17.10

Output of wireless-info:
[http://paste.ubuntu.com/25864348/](http://paste.ubuntu.com/25864348/)

Reinstalling bcmwl-kernel-source of says:
```
Building for 4.13.0-16-lowlatency
Building for architecture x86_64
Module build for kernel 4.13.0-16-lowlatency was skipped since the
kernel headers for this kernel does not seem to be installed.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.13.0-16-lowlatency
```

---

### Post by weisz-michael on 2017-11-02
Duplicate. Solution found in [https://ubuntuforums.org/showthread.php?t=2375063](https://ubuntuforums.org/showthread.php?t=2375063)

---

### Post by chili555 on 2017-11-02
I would add to the solution:```
sudo apt-get install linux-headers-generic
```Updates to the kernel version will then also cause updates to the header version and, most importantly, to the wireless driver.

---


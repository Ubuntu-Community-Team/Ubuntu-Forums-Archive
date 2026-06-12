---
title: "swapon - operation not permitted"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by back on 2009-11-17
Hi, I am trying to create swap file for my VPS server. I used this guide to do that: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 

It looks simple, but when I try this command it gives me headache :
root@back:~# sudo swapon /mnt/1024Mb.swap
swapon: /mnt/1024Mb.swap: Operation not permitted

I don't know what to do and what permission do I need, because I'm logged in as root:

root@back:~# whoami
root


If you have any ideas how to fix this, please share it. Thanks!

---

### Post by blazemore on 2009-11-17
try (as root)
```
chown root: /mnt/1024Mb.swap
```

---

### Post by back on 2009-11-17
Still same problem:

root@back:~# chown root: /mnt/1024Mb.swap
root@back:~# sudo swapon /mnt/1024Mb.swap
swapon: /mnt/1024Mb.swap: Operation not permitted


free -m output

total                         used       free     shared    buffers     cached
Mem:                        512        262        249          0          0          0
-/+ buffers/cach:       262        249
Swap:                           0          0          0

---

### Post by ukripper on 2009-11-17
you can add extra swap in your /etc/fstab which is much easier way.

check my post here for more info:
[http://ubuntuforums.org/showthread.php?t=1325363&page=3](http://ubuntuforums.org/showthread.php?t=1325363&page=3)

---

### Post by anaconda on 2009-11-17
did you remember to make the file swap before running the swapon command?

eg.
sudo mkswap /mnt/1024Mb.swap
sudo swapon /mnt/1024Mb.swap

---

### Post by back on 2009-11-17
Yes, I done these steps.

And now I added line "/mnt/512Mb.swap none swap sw 0 0" in /etc/fstab file, rebooted system, but still having same problem.

---

### Post by ukripper on 2009-11-17
> **back said:**
> Yes, I done these steps.

And now I added line "/mnt/512Mb.swap none swap sw 0 0" in /etc/fstab file, rebooted system, but still having same problem.

can you run this:
```
sudo swapoff -a
```

and then 
```
sudo swapon -a
```

check whether swaps running:
```
cat /proc/swaps
```

---

### Post by back on 2009-11-17
root@back:~# su -
root@back:~# swapoff -a
Not superuser.


I think this is a problem. Now I sent email to my VPS provider and asked about root privileges they give.

---


---
title: "Synaptic crashes once started"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by davidbowie on 2010-07-23
Synaptic flashes for a second then crashes. GUI and terminal have same result. Any help appreciated!

log
```
kernel: [85255.952553] synaptic[8248]: segfault at 7fd5b3f332e0 ip 00007fd2bdcc0654 sp 00007fff0c77ec40 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[7fd2bdc5b000+c5000]
update-apt-xapi[8253]: segfault at 7f33fe30a2e0 ip 00007f30feaaa654 sp 00007fff920cc370 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[7f30fea45000+c5000]
```

---

### Post by varunendra on 2010-07-24
See if [this]("http://ubuntuforums.org/showthread.php?t=104906") helps.

The problem there is a bit different, but the same solution may work for you also.

---

### Post by davidbowie on 2010-07-25
>< sweet ><  the same thing that worked for him 5 years ago, worked like a charm for me! Thank you thank you.:KS

---

### Post by varunendra on 2010-07-25
> **davidbowie said:**
>  the same thing that worked for him 5 years ago, worked like a charm for me!

You're welcome! It's nice to see things working. :)

---


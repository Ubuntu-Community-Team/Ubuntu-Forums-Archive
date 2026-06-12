---
title: "Question about unmounted hard disks."
date: 2009-01-07
forum: New to Ubuntu
---

### Post by kajman on 2009-01-07
I have 2 hard disks on my laptop, and I've noticed that only the Ubuntu system partition is mounted when I start the system (it's located on the 1st drive). Other partitions are dismounted at first, and I was wondering what state is the other hard drive in? Is it in something like "sleep mode"? Is it working at all before I mount it (or does it turn off when I dismount it?)? What about power consumption? (and so on.. )

---

### Post by hyper_ch on 2009-01-07
no clue what state it is exactely in, but it's powered to some part otherwise you wouldn't even be able detect it.

---

### Post by Efros on 2009-01-07
You probably just need to put a mount command in your fstab file. have a look [here]("http://ubuntuforums.org/showthread.php?t=283131") for some hints.

---


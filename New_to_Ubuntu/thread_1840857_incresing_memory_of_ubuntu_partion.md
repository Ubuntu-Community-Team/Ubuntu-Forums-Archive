---
title: "incresing memory of ubuntu partion"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by nrmlptl on 2011-09-08
i have install ubuntu inside windows and memory of ubuntu partition is less than 1 gb how to increase my ubuntu memory

---

### Post by tommpogg on 2011-09-08
With "memory" you mean space on your hard disk, don't you? Or do you mean RAM?

In the first case you can:
1) shrink the Windows partition from within Windows by using a disk management tool
2) use GParted on a ubuntu live cd to extend the ubuntu partition without having Ubuntu mounted

Be careful: back-up your data. I believe that working with partition could harm your systems and cause data loss. Honestly I never tried it, so I'm not 100% sure that steps will succeed.

If I were you, I would shrink the windows partition as needed and then reinstall Ubuntu on the new bigger partition.

Anyway, I have found [this thread]("http://ubuntuforums.org/showthread.php?t=1675322") that deals with your problem. You could ask to the thread starter if his/her attempt to resize the partitions succeeded.

---

### Post by ajgreeny on 2011-09-08
> **tommpogg said:**
> With "memory" you mean space on your hard disk, don't you? Or do you mean RAM?

In the first case you can:
1) shrink the Windows partition from within Windows by using a disk management tool
2) use GParted on a ubuntu live cd to extend the ubuntu partition without having Ubuntu mounted

Be careful: back-up your data. I believe that working with partition could harm your systems and cause data loss. Honestly I never tried it, so I'm not 100% sure that steps will succeed.

If I were you, I would shrink the windows partition as needed and then reinstall Ubuntu on the new bigger partition.

Anyway, I have found [this thread]("http://ubuntuforums.org/showthread.php?t=1675322") that deals with your problem. You could ask to the thread starter if his/her attempt to resize the partitions succeeded.
No, no.  This is a wubi installation, not a partitioned installation so that will not work.

See [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371) for all the details.  Better still consider turning your wubi into a proper partitioned installation,  see [https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by evilsoup on 2011-09-08
Stop. Before you do any of that, please tell us what you mean by 'installed Ubuntu inside Windows' - did you use the 'Windows Installer' (Wubi) or install from the CD while windows was turned on?

---

### Post by tommpogg on 2011-09-08
> **ajgreeny said:**
> No, no.  This is a wubi installation, not a partitioned installation so that will not work.


Sorry! I didn't understand properly the meaning of "ubuntu inside windows"

---


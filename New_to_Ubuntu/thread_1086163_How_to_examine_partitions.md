---
title: "How to examine partitions?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by matteojg on 2009-03-03
How can I browse the files on partitions other than sda1?

fdisk -l gives me: ```
  

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3555    28555506   83  Linux
/dev/sda2            3556        3648      747022+   5  Extended
/dev/sda5            3556        3648      746991   82  Linux swap / Solaris

```

The files on sda1 can be accessed via Places>Computer>Filesystem (on a GNOME desktop), right? But what about files on sda2 and sda5?

Any help and/or illumination greatly appreciated.

Ubuntu 8.10
GNOME desktop

---

### Post by kevin11951 on 2009-03-03
> **matteojg said:**
> How can I browse the files on partitions other than sda1?

fdisk -l gives me: ```
  

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3555    28555506   83  Linux
/dev/sda2            3556        3648      747022+   5  Extended
/dev/sda5            3556        3648      746991   82  Linux swap / Solaris

```

The files on sda1 can be accessed via Places>Computer>Filesystem (on a GNOME desktop), right? But what about files on sda2 and sda5?

Any help and/or illumination greatly appreciated.

Ubuntu 8.10
GNOME desktop

there is nothing there... those are your swap partition, sort of like emergency memory.

---


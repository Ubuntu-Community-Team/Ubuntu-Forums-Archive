---
title: "Need help setting up grub after ubuntu install(dual boot)"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by mhoy06 on 2009-05-26
Have windows on a different partition(xp). After an Ubuntu install I had no entry for windows. So I tried to add this:

```

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```

That was based on a post I read on this forum. I have gotten various errors trying different ways of typing in root. For example: root(hd0,1) didn't work either.

This is fdisk -l output:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3071    24659775    f  W95 Ext'd (LBA)
/dev/sda2            3072        3320     2000092+  82  Linux swap / Solaris
/dev/sda3   *        3321        7296    31937220   83  Linux
/dev/sda5               2        3071    24659743+   7  HPFS/NTFS

```
Any help appreciated. I need the Windows install for work this week.

---

### Post by freak42 on 2009-05-26
Hi
I am no expert in these things, but it looks like sda1 is just an extended partition ( apparently a container for other partitions), I looked at my dualboot fdisk output and my windows vista partition looks very similar to your sda5 (NTFS) partition, so maybe try booting from it? (hd0,4) ? As you can see from the Start/End Sections sda1 and sda5 are occupying the same area).
My ntfs partition also has the Boot flag set (whatever that means).

hth a little

---

### Post by mhoy06 on 2009-05-26
> **freak42 said:**
> Hi
I am no expert in these things, but it looks like sda1 is just an extended partition ( apparently a container for other partitions), I looked at my dualboot fdisk output and my windows vista partition looks very similar to your sda5 (NTFS) partition, so maybe try booting from it? (hd0,4) ? As you can see from the Start/End Sections sda1 and sda5 are occupying the same area).
My ntfs partition also has the Boot flag set (whatever that means).

hth a little

That results in error 12 invalid device requested.

Does that mean that there is some files missing on the windows partition?

I can mount that partition and AFAIK they are all there.

---


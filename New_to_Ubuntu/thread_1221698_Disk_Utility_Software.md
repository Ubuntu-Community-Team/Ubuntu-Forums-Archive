---
title: "Disk Utility Software?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by mammalsauceman on 2009-07-24
is there a piece of software for ubuntu that i can use to manage partitions, but not only on my hard drive but on other external media like thumb drives etc.

---

### Post by ajgreeny on 2009-07-24
System > Administration > Partiton Editor on the live CD or can be installed to your installed ubuntu with synaptic or Add/Remove.  If you install it you will not be able to use it for your ubuntu partitions, but can still use it for external disks ot other partitions on your computer, as long as they are unmounted.

It's a terrific tool which I have used a lot for all types of partitioning work, and so far it has never let me down.  Whether it's for shrinking, enlarging, moving, formatting to any file system I have ever needed, or anything else, it has been a great tool.

---

### Post by zeroseven0183 on 2009-07-24
> **ajgreeny said:**
> System > Administration > Partiton Editor on the live CD or can be installed to your installed ubuntu with synaptic or Add/Remove.  If you install it you will not be able to use it for your ubuntu partitions, but can still use it for external disks ot other partitions on your computer, as long as they are unmounted.

It's a terrific tool which I have used a lot for all types of partitioning work, and so far it has never let me down.  Whether it's for shrinking, enlarging, moving, formatting to any file system I have ever needed, or anything else, it has been a great tool.

And to install it using the Terminal,

```
sudo apt-get install gparted
```

---

### Post by mikechant on 2009-07-24
> System > Administration > Partiton Editor on the live CD or can be installed to your installed ubuntu with synaptic or Add/Remove. **If you install it you will not be able to use it for your ubuntu partitions**, but can still use it for external disks ot other partitions on your computer, as long as they are unmounted.

This isn't strictly true. It depends on your partition layout.
The thing you really can't do is operate on your ubuntu root partition while running off it. You may be able to operate on your swap, /boot, /home, shared data or other ubuntu partitions depending on whether they are primary or logical partitions, and if they are logical partitions depending what order they are in.
There's no harm in trying if you're not sure - gparted won't allow you to do anything to a locked partition and won't allow you to unmount it if it is in use.
You might think 'why not just use the Live CD always'. The answer is that it takes quite a long time to switch between your normal installed ubuntu to the liveCd and back again.

---

### Post by ajgreeny on 2009-07-24
Good point, but I think it's worth suggesting the live CD as a general rule, to avoid the possible confusion that comes when users find they can't do something simple to a partition simply because it is mounted, they may not know how to unmount it, and they then get very frustrated with the whole business.

A running system, even if using a separate /home, /boot, and anyb other partitions set up at install will normally have these partitions mounted and therefore not available for editing with gparted.  Use the liveCD and that problem disappears.

---


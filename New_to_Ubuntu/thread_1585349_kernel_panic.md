---
title: "kernel panic"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by PurpleF on 2010-09-30
Got msg Kernel panic - not syncing: VFS: Unable to mount root f's on un-block (0,0).  I can see that others have posted on this, but I AM an ABSOLUTE beginner and I don't understand the answers.  This week I've hardly been able to use my computer at all after continual crashing, can't be the hard drive, it was new 4 weeks ago!  I re-installed 10.04 Lucid Lynx for about the 10th time this week, and I'm getting desperate, please help.

---

### Post by ikt on 2010-09-30
> **PurpleF said:**
> can't be the hard drive, it was new 4 weeks ago!

Heya!

It's entirely possible for a new hard drive to be broken, however before you change hard drives give ubuntu 9.10 a go since that used an older kernel and may fix the issue.

You can download 9.10 from here:

[http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

Burn the ISO to cd/iso if you can :)


> Here's an explanation of the problem, step by step:

"Kernel panic - " The computer has reached a point where it is unable to continue; it has no choice but to halt.

"- not syncing" "The good news is, I wasn't in the middle of trying to write un-saved changes to disk when I died." Linux tries to do this ("to sync the filesystem") just before it halts, and it's telling you .. albeit in a backwards sort of way .. that it succeeded in doing that.

"Unable to mount root filesystem" One of the first things that the kernel must do is to "mount" (make available) the "root" (that is, "/") file system. It could not do that.

"On unknown block(0,0)" This is the device-number (0) and the partition-number (0) of the device where the kernel expects the root filesystem to be.

Probable causes: (in order)

   1. The most likely cause is that the root= parameter, which must be specified in the boot-loader's kernel command line, is incorrect or specifies the wrong device. You're supposed to be able to identify the device by label; I've never gotten that to work. I use something like root=/dev/hda1.
   2. Boot-loaders like Grub may count partitions starting from #0; Linux counts them from #1.
   3. Some distros use a complicated "initrd" mechanism to load disk drivers. If this process isn't working for your particular device, there can be grief.

[http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-0-0-a-458751/](http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-0-0-a-458751/)

---

### Post by PurpleF on 2010-10-02
Thank you so much for your splendid explanation, I learnt a thing or two which is excellent.  After spending a couple of days with more crashing, a friend suggested I, or rather he, replace the power unit, I'm allergig to screwdrivers!   That seems to have done the trick, so I'm breathing again.

I really appreciate you taking the time to lead me by the hand further into Ubuntuland.

---


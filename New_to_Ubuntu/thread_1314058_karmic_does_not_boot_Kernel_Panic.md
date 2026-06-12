---
title: "karmic does not boot: Kernel Panic"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by MelDJ on 2009-11-04
i tried booting into karmic and this comes up:

kernel panic- not syncing: VFS: unable to mount root fs on unknown wn=block(8,3)

anyone can help me out?

---

### Post by ukripper on 2009-11-04
> **MelDJ said:**
> i tried booting into karmic and this comes up:

kernel panic- not syncing: VFS: unable to mount root fs on unknown wn=block(8,3)

anyone can help me out?

What happens if you boot in recovery mode?

---

### Post by philinux on 2009-11-04
Either try the an older kernel or choose recovery mode and use fsck to check the file system.

---

### Post by MelDJ on 2009-11-04
> **ukripper said:**
> What happens if you boot in recovery mode?

the same thing happens. i cant boot either way. it just hangs.

installed with wubi under vista

---

### Post by philinux on 2009-11-04
Ah Wubi...

[http://ubuntuforums.org/showthread.php?t=495366](http://ubuntuforums.org/showthread.php?t=495366)

See last post. They suggest a defrag of the /wubi folder.

---

### Post by MelDJ on 2009-11-04
This will take a while...):P

---

### Post by philinux on 2009-11-04
> **MelDJ said:**
> This will take a while...):P

If it doesn't work I would uninstall wubi and go for dual boot.

---

### Post by ukripper on 2009-11-04
> **philinux said:**
> If it doesn't work I would uninstall wubi and go for dual boot.

+1, go for dual boot if nothing else works.

---

### Post by LacrimaMax on 2009-11-23
> **philinux said:**
> Either try the an older kernel or choose recovery mode and use fsck to check the file system.


Could you please explain how I can try an older kernel? I am newbie.
I have Ubuntu 9.10 installed with Wubi.

---

### Post by adabwebmaster on 2010-03-04
look here:
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
and replace C:\_wubildr_ with the file attached.

---

### Post by MelDJ on 2010-03-06
> **LacrimaMax said:**
> Could you please explain how I can try an older kernel? I am newbie.
I have Ubuntu 9.10 installed with Wubi.

after selecting ubuntu, press escape then select the older kernel

---

### Post by tejashs on 2010-03-06
I had a similar problem when i updated ubuntu 9.10 and new linux kernel was installed
and this thing worked for me.

> **adabwebmaster said:**
> look here:
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
and replace C:\_wubildr_ with the file attached.

i had been suggested the following link

[http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---


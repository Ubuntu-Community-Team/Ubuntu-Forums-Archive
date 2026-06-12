---
title: "e2label error"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Matt26 on 2009-12-19
i'm trying to set the label for an ntfs volume in ubuntu 9.10 using e2label and i'm getting the following error message:

> e2label: Permission denied while trying to open /dev/sdb5
Couldn't find valid filesystem superblock.

i've tried this command while the volume is unmounted and mounted and i get the same error either way.

i've tried using sudo with the command which gives a similar error:

> e2label: Bad magic number in super-block while trying to open /dev/sdb6
Couldn't find valid filesystem superblock.


what am i doing wrong here?

---

### Post by coffeecat on 2009-12-19
> **Matt26 said:**
> what am i doing wrong here?

You're using e2label to try to set the label on a NTFS partition. e2label is for ext2/3/4.

Install the package ntfsprogs and use ntfslabel from the terminal.

---


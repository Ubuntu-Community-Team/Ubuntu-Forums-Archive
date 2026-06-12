---
title: "Dual booting XP installed 1st. How do I give ubuntu lower cylinders?"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by mvalviar on 2009-08-21
I read psychocat's guide on this. Is it possible to dual boot xp/ubuntu with xp installed 1st and still give ubuntu lower cylinders for faster disk access? I have a 160GB HD with 2 NTFS partitions xp installed on the 1st partition any tips on how I go about doing it? I plan on giving minimal space to xp since I'll just be using it for games and such.

Regards,
mvalviar

---

### Post by mapes12 on 2009-08-21
Having XP on the first partition of the HDD in a dual boot configuration will not slow down Ubu. Create some free space then just install Ubu selecting "use free space" (or something like that) when you get to the partitioning section. Grub will detect XP and create boot options at start up.

---

### Post by mvalviar on 2009-08-21
Ok cool. Is it possible to reinstall xp on the ntfs partition without any hassle when the dual boot setup is complete?

---

### Post by LewRockwell on 2009-08-21
> **mvalviar said:**
> Ok cool. Is it possible to reinstall xp on the ntfs partition without any hassle when the dual boot setup is complete?

yes






it is possible

---

### Post by brookie on 2009-08-21
but would ubuntu have higher performance if it was installed first followed by winxp?

---

### Post by LewRockwell on 2009-08-21
> **brookie said:**
> but would ubuntu have higher performance if it was installed first followed by winxp?

no

.

---

### Post by egalvan on 2009-08-21
> **mvalviar said:**
> Is it possible to reinstall xp on the ntfs partition without any hassle when the dual boot setup is complete?

Yes, it is possible.

But reinstalling XP will wipe out the GRUB MBR;
that will need reinstalling.

This can be done, and the level of "hassle" can be reduced by taking precautions and notes before the XP reinstall.

SuperGRUB LiveCD will also make this process easier.

---

### Post by egalvan on 2009-08-21
> **brookie said:**
> would ubuntu have higher performance if it was installed first followed by winxp?

Yes, in theory there is a higher transfer rate on the outer cylinders...

but in practice, it's not really noticeable...

---

### Post by mvalviar on 2009-09-10
> **egalvan said:**
> Yes, in theory there is a higher transfer rate on the outer cylinders...

but in practice, it's not really noticeable...


Solved! I'll take your word for it.

---


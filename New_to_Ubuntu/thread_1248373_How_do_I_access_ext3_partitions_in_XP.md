---
title: "How do I access ext3 partitions in XP?"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by mvalviar on 2009-08-24
Hi! I'm dual booting XP and Jaunty. I use XP for games and IE testing. For testing I need to access my scripts which is in the ubuntu partition. How do I access it? I partitioned my drive as suggested my pyschocats and tried to use fsdrive. The partition is visible however windows says it is unformatted. Any suggestions?

---

### Post by nhasian on 2009-08-24
yes you can use:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Paddy Landau on 2009-08-24
FS driver supports ext3 incompletely.

Better to use [Ext2FSD]("http://www.ext2fsd.com/"), which does support ext3.

Unless you want it read-only, in which case it doesn't matter.

I haven't found anything that supports ext4.

---

### Post by riazrahaman on 2009-08-24
don't advice on mounting your linux partition in Windows.

If you still plan on mounting it, please choose the read only option.

---

### Post by jacksaff on 2009-08-24
The ext2 driver is fine with windows and there's no reason to be afraid of it. 
I would use a dedicated data partition though, and keep windows unable to write to my /home.
If nothing else the thumbnail index files xp seems to want to dump everywhere are very annoying!

---

### Post by Paqman on 2009-08-24
> **mvalviar said:**
> Any suggestions?

If it's just a few scripts you could always use some remote storage such as UbuntuOne, DropBox or Gmail.

---


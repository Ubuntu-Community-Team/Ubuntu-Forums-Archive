---
title: "Which backup program to use?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-31
I am currently evaluating back up solution for ubuntu installs and add/remove and synaptic throw up more than one good utility. [Sometimes I wish there weren't so many good programs for everything]

Which of these do people recommend:

1) File Backup Manager [from add/remove]

2) Simple backup [Sbackup from add/remove]

3) Clonezilla

4) Partimage

Everything I want to back up is on a separate Data/Multimedia partition so I can either back up the files or the whole partition.

Would using Clonezilla/partimage to clone my ubuntu partition work well if restored to other computers (likely issues with grub? MBR table? partition numbers? driver incompatibilities such as video?)

Thanks a lot

---

### Post by emarkd on 2009-01-31
Well, if all your backing up is data/multimedia, you shouldn't have any trouble restoring it to a working condition because there shouldn't be anything there that's system dependent.

As for the tool to use, I'll actually recommend another one:  rsync.  It's in the repositories.  It's commandline but is very easy to use.

---

### Post by stoogiebuncho on 2009-01-31
> **emarkd said:**
> As for the tool to use, I'll actually recommend another one:  rsync.  It's in the repositories.  It's commandline but is very easy to use.

I second that.  And if you aren't crazy about the command line, just get Grsync, which is the same thing with a nice GUI to make things simple.

---

### Post by mdpalow on 2009-02-03
QuickStart is an option.

See my signature for link.

---


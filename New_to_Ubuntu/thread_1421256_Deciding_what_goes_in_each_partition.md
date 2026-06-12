---
title: "Deciding what goes in each partition"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by krapp on 2010-03-04
Hi all—I am interested in dual-booting Windows 7 and Ubuntu on one 320 gigabyte hard drive; the process itself seems straightforward, but not the thinking behind it. My question is as follows: should I store my music files, documents, movies, etc. in a neutral partition so to speak, or in the largest of the Windows 7 partitions? Would Windows 7 throw a fit in the first case? Or, conversely, Ubuntu in the second? Thanks in advance!

---

### Post by undecim on 2010-03-04
Ubuntu can read Windows partitions, but Windows cannot read Ubuntu partitions.

That being said, either option would work. Having a separate partition has the added bonus that if one partition gets corrupted the others are fine, and you can replace either OS without worrying about losing the Music, docs, folders on your drive.

The disadvantage to using a separate partition is that you need to set the space you will use in advance. If you need to resize it later, you risk losing your data if something goes wrong during that procedure.

Also, I would like to say that you can link specific directories (Music, Documents, etc) in your home folder on Ubuntu. This will make it seem like the two OSs are sharing those folders between each other, which should make it much more convenient when switching between them. This works with or without a separate partition.

---

### Post by mastablasta on 2010-03-04
It is always a good thing to have data on a separate partition from the system partition. Linux is created like that by"default". 
 
Windows - have a partition with the system on it and the one with data (always a good idea). If something is wrong with the system you can easilly re-install it or even re-format the partition and then re-install the system while your precious data remains intact on another partition.

---

### Post by krapp on 2010-03-04
So then would the following plan work best?

3 primary partitions for Windows 7 (I read somewhere that this is what 7 and Vista default to).

1 primary partition divided in 3: 1 for Ubuntu, 1 for files I want to access from within both OSes, and 1 for swap space for Linux updates/installations.

Am I understanding how this works, more or less? If I am coming at this in completely the wrong way, please don't hesitate to indicate so. Thanks for the help.

---


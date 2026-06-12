---
title: "ubuntu freezes when copying large files please confirm"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by paul_anders on 2009-05-29
ubuntu 9.04 with all the latest updates freezes when copying large files

im copying a 4.4 gig and it freezes on every attemp. using gnome or cli 

please can you confirm

thanks

---

### Post by s.fox on 2009-05-29
Hi,

Out of interest can you tell us your hardware specifications?

Thanks

-Ash R

---

### Post by x33a on 2009-05-29
which file system are you using?

ext4 is known to have problems with heavy disk I/O.

---

### Post by BugBuster on 2009-05-30
I would like to second this issue as well...
My computer almost comes to a grind when there is a high disk activity like copying large files to my SATA II disk..
Also out of curiosity would like to confirm one thing..
While copying large files to sata2 disk i never get above 25-50MB data copy rate. Is this normal in Ubuntu or am i missing something?

My Specifications:
Ubuntu 9.04 amd64 fully updated.
AMD Athlon64 X2 4000+
Seagate 250 GB SATA2
MSI K9AGM4-L, AMIBIOS v2.0B11
2 GB 800MHZ DDR2 Transcend

Thanks.

---

### Post by BugBuster on 2009-05-30
> **BugBuster said:**
> I would like to second this issue as well...
My computer almost comes to a grind when there is a high disk activity like copying large files to my SATA II disk..
Also out of curiosity would like to confirm one thing..
While copying large files to sata2 disk i never get above 25-50MB data copy rate. Is this normal in Ubuntu or am i missing something?

My Specifications:
Ubuntu 9.04 amd64 fully updated.
AMD Athlon64 X2 4000+
Seagate 250 GB SATA2
MSI K9AGM4-L, AMIBIOS v2.0B11
2 GB 800MHZ DDR2 Transcend

Thanks.

Forgot to mention, that I had this issue using Hardy 32 bit as well.
Also with ext3 as well as ext4 file systems...

---

### Post by juancarlospaco on 2009-05-30
No. *+80Gb copied HD to HD, Ubuntu 9.04 EXT4, Clonezilla img.*

---

### Post by rado3105 on 2010-12-11
I have the same problem, updating to ubuntu 10.10 my one system after gnome start screen completely freezed. I had to reinstall the whole system. Now when I copy files(more than 500MB) it freezes every time. Using parted cd copying of file of anysize is without any problem. So this is problem of UBUNTU. Can anybody help?

---

### Post by iilkevych on 2011-02-02
I posted issue in launchpad. it looks similar to posted here but still have no fix.
[https://bugs.launchpad.net/ubuntu/+bug/694875](https://bugs.launchpad.net/ubuntu/+bug/694875)

---


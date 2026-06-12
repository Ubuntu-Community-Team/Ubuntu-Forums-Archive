---
title: "Single dektop, 2OSes, 1 Anti-virus?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by ubunron on 2010-10-09
[FONT=&quot]I want to have Windows XP and Ubuntu at the same time on my Pentium 4 PC. I have purchased Mc Afee Total Security for my desktop. Will a single Mc Afee product work for both XP and Fedora 13 on my system when these two operating systems co-exist on my system? [/FONT]

---

### Post by cascade9 on 2010-10-09
In most cases, you dont need antivirus for linux systems. 

If you did want antivirus for your linux system (pretty useless really, the few bits of malware for linux are normally 'socially engineered') then no, McAffee wont search your linux partitions for viruses. Unless you have windows 'seeing' your linux filesysmtes (with things like EXT2 IFS for windows) , then it *might* scan the drives.

---

### Post by coffeecat on 2010-10-09
> **cascade9 said:**
>  then it *might* scan the drives.

It probably will. I discovered this by accident a few years ago when I had Windows and about six different Linux distros installed on the one multi-booting machine. I'd installed one of the ext drivers for Windows and this had designated my Linux partitions G:, H:, I:, J: and so on.

One day I started a full system scan in Windows with AVG and came back a few hours later to find it methodically working its way through my Linux partitions.

It didn't find any viruses. :rolleyes:

Is there are Windows driver for ext4 yet? I don't know. And if Fedora is on a LVM partition - which is Fedora's obsession and default - then I doubt whether there is any Windows driver that could read that.

---


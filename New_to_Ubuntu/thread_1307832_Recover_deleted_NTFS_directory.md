---
title: "Recover deleted NTFS directory"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by AlanRick on 2009-10-31
Hi,
I accidentally deleted a directory on my NTFS partition and I can't find it in my bin (bottom right hand corner).

I've installed testdisk (cgsecurity) but the "recover" folder option is not displayed when I navigate to the "advanced" menu (contrary to to tutorial).

I'm  stuck. Any ideas?
Alan

(PS I scanned the forum and found the testdisk utility mentioned - but I can't find a solution to this problem)

---

### Post by dresden on 2009-10-31
try  foremost maybe you will have luck

[https://help.ubuntu.com/community/DataRecovery#Foremost](https://help.ubuntu.com/community/DataRecovery#Foremost)

---

### Post by lavinog on 2009-10-31
photorec is good at recovering all sorts of files (it is part of the testdisk package)

---

### Post by sazan on 2009-10-31
Photorec is a companion tool of testdisk.

---

### Post by AlanRick on 2009-10-31
Many thanks for your answers.
Luckily it turned out that my last backup was up-to-date. Before I could verify that I'd already run *foremost* and this did recover the files (but not the timestamps or directory structure) so it was useful practice.
Also, for the record, the undelete utility from a windows boot could not find the missing directory so it seems that ubuntu does a pretty thorough job deleting.

Nevertheless, my head is still reeling from the discovery of there being no undelete from nautilus for ntfs partititions. 
Is this worth a feature request?

---


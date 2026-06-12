---
title: "How to install 2 ubuntus"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by pdlethbridge on 2010-06-09
I would like to install 9.04 and 10.04 on the same computer. What is the best way to do this? How do I get them to use their own home folders?
 What I want to do is this but it won't let me.
Ext 2 / 9.04 10 gig
ext 3 /home  24 gig
ext 4 /10.04 10 gig
ext 4 /home  24 gig
swap         2 gig 
Fat 32       10 gig

---

### Post by 4Orbs on 2010-06-09
> What I want to do is this but it won't let me.
WHAT won't let you? gparted?

---

### Post by oldfred on 2010-06-10
I have 2 Ubuntu installs on two disks and XP on a third disk. You just need to set up the partitions in advance and use manual install.

I would also recommend a shared /data partition so for each install you can have the same data like your firefox profile, thunderbird profile and other data. I do not recommend FAT but NTFS for windows data sharing.

---


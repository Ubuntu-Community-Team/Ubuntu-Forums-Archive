---
title: "Will private folder remain intact after a re-install from 8.10 to 8.04?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-03
Hello,

Because of many problems with Ubuntu 8,10 I want to "re-install" 8.04 again while keeping my home folder (it is already on a separate partition). I make use of the encrypted Private directory in the home folder.

If I re-install 8.04 while keeping the home folder, will the encrypted directory remain in tact and usable?

Thanks!

---

### Post by django0909 on 2009-01-03
It will if you keep it in the seperate partition and then copy it back once you're done re-installing 8.04......

---

### Post by Paqman on 2009-01-03
> **kramer65 said:**
> will the encrypted directory remain in tact and usable?


It should do. The ecryptfs-utils package needed to make it work are in the Hardy repos. I would take a backup of the folder's contents just in case.

---

### Post by kramer65 on 2009-01-03
Alright thank you. I will do are-install tomorrow!

---

### Post by sdennie on 2009-01-03
Hardy has encfs and there is nothing special about the drives location or OS that would prevent it from being read.  I literally tarred up my home directory yesterday, untarred it to a different partition/fs and my encfs ~/Private directory still works as usual.  You should have no problems.

---


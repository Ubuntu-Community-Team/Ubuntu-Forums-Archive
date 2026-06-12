---
title: "trying to create a backup script"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-04-26
using
rsync -av /home/mick/Main/ /dev/sda/home/mick/backup/ --delete

I get a "not a directory" error

Can someone help, oh yes its the second HD

---

### Post by steve101101 on 2009-04-26
do both directories exist in the noted places.

---

### Post by adult swim on 2009-04-26
instead of /dev/sda you are going to have to use the directory that the disk is mounted to

---

### Post by Mick8882003 on 2009-04-26
umm, how do i find that out?

thankyou

Mick

---

### Post by sadicote on 2009-04-26
No offence guys, but we do not have to rub two stones together to start a fire nowadays--haven't you heard of Remastersys? It beats Norton ghost, mondorescue, sbackup, and all that came before, together, by itself. With the cost of CDs being as low as 20 cents, why would anyone want to go through the trouble of these backup scripts? There is also this other great utility that i recently read about, it's called Back in Time...:)

---

### Post by adult swim on 2009-04-26
looking again, are you trying to back up MAIN on the same disk in a folder named backup?

---


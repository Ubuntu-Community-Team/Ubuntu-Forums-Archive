---
title: "hi i have just bought an external hard drive what is a good back up software"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by blake7 on 2009-10-11
yea what is the best back up software thats simple to use and very reliable and no comand lines (why would any one want to use commoand line ???).

thank you

---

### Post by yeats on 2009-10-11
If you're comfortable on the command line, rdiff-backup is quite simple.  You basically do:

```
[sudo] rdiff-backup [/original/directory] [/backup/directory]
```

sudo is necessary for backup up files/directories that are not owned by you.

---

### Post by stmiller on 2009-10-11
Try grsync:

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by CharlesA on 2009-10-11
I use rsync. :-)

---

### Post by Tomone on 2009-10-11
I use [rsnapshot]("http://rsnapshot.org/"), which is a command line utility, based on rsync. It's nice because once you have it set up, it's very simple to use.

---


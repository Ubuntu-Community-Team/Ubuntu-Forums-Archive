---
title: "rsync to backup complete system"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by steve101101 on 2009-04-25
I want to use rsync instead of this command to backup my entire system.

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

---

### Post by cerealtx on 2009-04-25
> **steve101101 said:**
> I want to use rsync instead of this command to backup my entire system.

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

is there suppoused to be a questions somewhere in that? or are u just sharing?

---

### Post by steve101101 on 2009-04-25
sorry for not being clear ... how would i do a complete backup like this command

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

except doing it with rsync b/c it will not backup files that haven't changed which will be most of them.

---

### Post by wizard10000 on 2009-04-25
> **steve101101 said:**
> sorry for not being clear ... how would i do a complete backup like this command

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

except doing it with rsync b/c it will not backup files that haven't changed which will be most of them.

I replied in your other thread.  Here's what I said -

> **steve101101 said:**
> does rsync skip files that haven't been changed since last update and if so what command would i run to backup everything on the computer like my previous command.

Yeah, by default rsync will only back up files that have changed or don't exist on the target.  The stuff I posted above will get you started but you're still gonna have to read a man page or two  ;-)

The hardest part for me was the exclude file - took me awhile to understand that directory names have to have a trailing slash - but you can exclude stuff on the command line too.

The stuff I posted meets my needs but probably wouldn't meet yours - but the simple line that copies my /etc directory to another folder would be a good place to start.  Get that working, then learn how to use an exclude file, then set rsync options - and there are a lot of them.

---


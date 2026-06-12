---
title: "File syncronization tool"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by richiewrt on 2009-03-21
I am looking for a file synchronization tool. I am using dropbox on all my computers, and I want to be able to sync some files automatically with my dropbox account so that the latest one will always be available from dropbox. Has anyone done this, and what tools did you use?

EDIT** it looks like Komparator would work, but I really don't want a KDE app. Anything similar in gnome?

---

### Post by Nxion on 2009-03-21
If you are using Dropbox, it actually updates al the other clients automatically. So lets say you have a desktop and laptop that both have Dropbox installed. If you upload a file from the desktop to dropbox. After it is finished uploading, the other machine, the laptop in this case, get a popup saying that this file has been added. That is the buty with Dropbox. It all does it on its own, no need for anything additional!

---

### Post by richiewrt on 2009-03-22
Yeah, I know that, what I am looking for is something to sync another directory, say my "documents" directory on my local ubuntu install, with my "dropbox" directory on my local machine, and thus syncing it with my other computers.

**edit**
I have tried grsync and I get permission errors. Here is the output.
```
rsync: mkstemp "/home/rich/Dropbox/.Database.kdb.ihRX5W" failed: Permission denied (13)
rsync: mkstemp "/home/rich/Dropbox/.testmove.doc.xHGo9b" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]

```

---

### Post by MrWES on 2009-03-22
> **richiewrt said:**
> Yeah, I know that, what I am looking for is something to sync another directory, say my "documents" directory on my local ubuntu install, with my "dropbox" directory on my local machine, and thus syncing it with my other computers.

rsync and grsync the GUI

---

### Post by richiewrt on 2009-03-22
Sorry, I edited the above to include that I have tried grsync and had errors. thanks for the quick response though. any ideas on fixing the errors?

---

### Post by MrWES on 2009-03-22
> **richiewrt said:**
> Sorry, I edited the above to include that I have tried grsync and had errors. thanks for the quick response though. any ideas on fixing the errors?

Hrmm...it appears there are some permission issues with either where you're copying from and/or to. I haven't run rsync in awhile.
Do you have perms to access those files and directories?

Bill

---

### Post by Nxion on 2009-03-22
The simplest way is just to remap dropbox to use a different directory...

---


---
title: "Errors trying to backup system"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Whatrymes on 2010-07-12
Hey again:

I'm trying to back up my Ubuntu partion using a method posted by "Heliode." The terminal scrolls for a long time and ends as follows:

 "tar: /: file changed as we read it
tar: Exiting with failure status due to previous errors"

That's happened twice????

---

### Post by mikewhatever on 2010-07-12
It looks like you haven't excluded the backup file itself. Make sure you do that.

---

### Post by Whatrymes on 2010-07-12
> **mikewhatever said:**
> It looks like you haven't excluded the backup file itself. Make sure you do that.

This is the command I put in the terminal:

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I think the backup file is meant to be excluded??

---

### Post by mikewhatever on 2010-07-12
Where is your backup.tgz saved? Is it saved as /backup.tgz or is it saved into your home folder (/home/user_name/backup.tgz)? The command you posted excludes /backup.tgz, and you have to either cd into root first or save the file as /backup.tgz.
```
cd /
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

or

```
tar cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

---

### Post by Whatrymes on 2010-07-12
> **mikewhatever said:**
> Where is your backup.tgz saved? Is it saved as /backup.tgz or is it saved into your home folder (/home/user_name/backup.tgz)? The command you posted excludes /backup.tgz, and you have to either cd into root first or save the file as /backup.tgz.
```
cd /
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

or

```
tar cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

I "cd /" first. The .tgz file is created in /.

---

### Post by mikewhatever on 2010-07-12
Then it's probably another .tgz file.;)

---

### Post by Whatrymes on 2010-07-12
Thanks for all your help, something is wrong with the command somehow, I tried a clean install and then tried a backup but received the same error message. This is the link, I can't see what's wrong.

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by mikewhatever on 2010-07-12
Just to quote from the howto:
> EDIT2:
At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that.

Have you tried restoring from the backup?

---

### Post by Whatrymes on 2010-07-12
> **mikewhatever said:**
> Just to quote from the howto:


Have you tried restoring from the backup?

No I have not.Gulp!

---

### Post by Whatrymes on 2010-07-13
> **mikewhatever said:**
> Just to quote from the howto:


Have you tried restoring from the backup?

Ran back up and ended with this:
```
root/.esd_auth

tar: Exiting with failure status due to previous errors

root@edsu-laptop:/# 
```

I also changed my desktop and my home page AFTER the backup was created. After running the backup, the changes are still there. I would expect these changes to revert back to their state before I created the backup.tgz file, no?

---


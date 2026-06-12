---
title: "How can I check the integrity of an external drive?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-11-11
I want to check the disk and file integrity of an external USB drive.  I know that Ubuntu automatically checks disks every 30 startups or so, but is there a utility that will let me do it directly, on any drive i want?

---

### Post by lotharmat on 2009-11-11
AFAIK. The drive has to be unmounted and then you can run fsck. on that device

i.e. fsck /dev/[your drive]

I think that is right - Hopefully someone will be along shortly to either confirm this or bitchslap me for being a retard!

Either way we wil lboth learn something :D

---

### Post by Joe Ker1086 on 2009-11-11
i believe the command you are looking for is ```
fschk 
``` see what the options are but i think you point it to the drive you are trying to check

---

### Post by brujoand on 2009-11-11
Yeah, karmic comes with a utility for this. Its located in Administration -> Disk utility if im not mistaking :)

---

### Post by muteXe on 2009-11-11
yup :)
[http://linuxmanpages.com/man8/fsck.8.php](http://linuxmanpages.com/man8/fsck.8.php)

---

### Post by Joe Ker1086 on 2009-11-11
Looks like I added a letter, lol, sorry

---

### Post by Dougie187 on 2009-11-11
I would just use the utility in karmic. it's way easier.

---


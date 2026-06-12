---
title: "Error in boot"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by nilsolaris on 2009-02-11
I woke up this morning, turned on my computer as usual but today i got the message.

/dev/sda5:Unattatched incode 14262277

/dev/sda5:UNEXPECTED INCONSISTENCY;RUN fsck MANUALLY
(i.e without -a or -p option)

fsck died with exit status 4

Checking drive /dev/sda5: 94% (stage 4/5, 1741/2359)

[fail]

*An automatic file system check (fsck) of the root filesystem failed.

A manual fsck must be performed, then the system restarted.

The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

*The root filesystem is currently mounted in read-only mode.

A maintenance shell will now be started

After performing system maintenance, press CONROL -D to terminate the maintenance shell and restart the system. 

bash: no job control in this shell





Would anyone know what happened here, and what i can do to fix this problem? Any help will be much appreciated.

---

### Post by kestrel1 on 2009-02-11
Have you done what it says & run fsck?

---

### Post by nilsolaris on 2009-02-11
thanks for the reply!
my screen was positioned to a point where i could see the type [y] for yes (to fix)

---

### Post by kestrel1 on 2009-02-11
did you just run fsck or did you use:```
fsck /dev/sda5
```

---


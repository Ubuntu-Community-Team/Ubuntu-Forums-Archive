---
title: "errors during startup drive check?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-09
The startup drive check is finding problems.

Inodes that were part of a corrupt orphaned link have been found...
unexpected inconsistency
run fsck manually w/o -a or -p options
fsck died w/ exit 4 status

fsck of root file system failed
manual fsck must be performed the restart system

in maintenance mode with root file system mounted in read only

hit ctrl D after maintenance

Then I get 8 lines of bash: <command> command not found

root@mike-laptop:~#

What do I do to correct this?  The thing boots fine as long as I skip the drive check but it seems like something that needs attention.  Can anyone explain to me whats going on.

---

### Post by sideaway on 2010-02-09
Try booting a live CD and doing the file system check from there.

---

### Post by hortstu on 2010-02-09
Sorry, I'm somewhat new to this... How do I do fsck from the live cd?


> **sideaway said:**
> Try booting a live CD and doing the file system check from there.

---

### Post by hortstu on 2010-02-09
So I'm running the laptop from a live cd right now.  How do I perform fsck on the internal drive from the terminal in live cd?

---

### Post by hortstu on 2010-02-10
OK I figured this out with an extensive search... anyone else that ends up here with a similar problem will want to avoid the live cd... that may work but I don't know how to do it.

At the end of the error message there is a root@ prompt

I entered ```
fsck /dev/sdxy
```  

xy is the appropriate drive.. the one showing the errors

then I answered all the questions yes and rebooted when it was done.

I think a Carla mentioned entering ```
fsck -y /dev/sdxy
```

apparently -y auto answers all the questions yes

Hope this works for you if you're having the same problem.

---


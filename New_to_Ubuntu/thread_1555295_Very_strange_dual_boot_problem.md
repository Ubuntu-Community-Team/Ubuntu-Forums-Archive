---
title: "Very strange dual boot problem"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2010-08-17
My parents are dual-booting Windows XP and Ubuntu 8.04 (I know I know, they're going to update soon).  A while back they had a strange problem where it started taking forever to boot into either OS.  The loading page would come up and it would just sit there for 5-7 minutes and then all the sudden the OS would load and everything would work normally.

I did a little searching but couldn't figure out what would cause the problem.  They said they had just installed some Windows updates so I used system restore and restored to a point before the problem started.  Everything worked fine after that.

Now, several months later, it's happened again.  I know I could probably fix it using System Restore again, but I'd like to know what is going on.  How can a Windows update cause Ubuntu to boot slowly?  Is there a way to fix it permanently?

Thanks.

---

### Post by skatinjj on 2010-08-17
> **stoogiebuncho said:**
> My parents are dual-booting Windows XP and Ubuntu 8.04 (I know I know, they're going to update soon).  A while back they had a strange problem where it started taking forever to boot into either OS.  The loading page would come up and it would just sit there for 5-7 minutes and then all the sudden the OS would load and everything would work normally.

I did a little searching but couldn't figure out what would cause the problem.  They said they had just installed some Windows updates so I used system restore and restored to a point before the problem started.  Everything worked fine after that.

Now, several months later, it's happened again.  I know I could probably fix it using System Restore again, but I'd like to know what is going on.  How can a Windows update cause Ubuntu to boot slowly?  Is there a way to fix it permanently?

Thanks.

I would run chkdsk in windows or if the hard drive uses SMART technology, install the smart-tools on either OS and run the extended test.

You can just google for it in windows or use the package manager in ubuntu.  If you need further assistance just ask.

---

### Post by audiomick on 2010-08-17
+1
It sounds like something is causing troubel reading the drive at boot up.

---

### Post by stoogiebuncho on 2010-08-18
Thanks, I'll try this and post back if it works or not (it may be a week or two before I'm out there again)

---


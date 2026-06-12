---
title: "Hard Disk has &quot;Bad Sectors&quot;?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Saito Chikara on 2010-03-20
Okay, i have Ubuntu 9.10 on my Laptop, which, until 2 hours ago, I was going to sell. I was powering it on to check to make sure it would run okay after installing over a crashed XP HOME, and it comes up with a Hard Disk Error logo in the top right. I looked at the report it generated, and it says:

_Reallocated Sectors_
Normalized: 100
Worst: 100
Threshold: 50
Value: 94 Sectors


What does this mean, and what is the step-by-step tutorial on fixing this? I appreciate any and all help on this!

---

### Post by drascus on 2010-03-20
What this means is that when the hard drive was tested there are some bad sectors on the disk. This happens over time and is an indication that the disk may be beginning to fail. Now you can run a computer with bad sectors no problem for a long time. The standard advice for your issue is to back up your computer securely wipe the drive (check out boot and nuke) and then securely dispose of the drive. then you will need to get a new hard drive.

---

### Post by Mark Phelps on 2010-03-21
> **Saito Chikara said:**
> What does this mean, and what is the step-by-step tutorial on fixing this? I appreciate any and all help on this!

There is no way to "fix" a hard drive that is failing; the only thing you can do is replace it outright.

But, you also need to be aware that the 9.10 app reporting this has a history of bugs and "false positives", meaning, there may be nothing at all wrong with your drive!

Suggestion is to find out who manufactured your drive, go to their website, and if the have a utility for diagnosing their drives, download and run that.  That's a much more reliable drive checker.

---


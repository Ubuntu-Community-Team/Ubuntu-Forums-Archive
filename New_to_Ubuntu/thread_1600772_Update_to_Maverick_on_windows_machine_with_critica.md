---
title: "Update to Maverick on windows machine with critical data on it"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Peterfc on 2010-10-19
I have updated to Maverick on my desktop and my laptop. I would like to update my windows machine. I keep the windows for Accounts and Payroll. I installed by using Wubi. I have backed up my Accounts and Payroll data to the program folder also to Two Usb memory sticks. Would i expect that the update goes ok without any damage to my windows partition. 

I only use windows for the two programs and then go back to Ubuntu.

---

### Post by CharlesA on 2010-10-19
since you installed via Wubi there really isn't any thing that can get hosed up in Windows.

In any case, before you do any sort of upgrade you need to make sure you have a good backup.

---

### Post by bcbc on 2010-10-19
See here for maverick upgrade issues on wubi: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

This doesn't affect windows. Just booting ubuntu.

---

### Post by Mark Phelps on 2010-10-19
> **Peterfc said:**
> I only use windows for the two programs and then go back to Ubuntu.

Then ... you would do better to have a true dual-boot setup in which Ubuntu is in its own partition(s).  Wubi is not intended for long-term usage and upgrades tend to be problematic -- as seen in the link that bcbc provided.

---

### Post by bcbc on 2010-10-19
> **Mark Phelps said:**
> Then ... you would do better to have a true dual-boot setup in which Ubuntu is in its own partition(s).  Wubi is not intended for long-term usage and upgrades tend to be problematic -- as seen in the link that bcbc provided.

I think Canonical is unclear on the matter about what wubi is intended for. For example, the windows-installer is now prominently displayed on the [ubuntu download site]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") (and wubi-installer.org now refers to it) and no mention is made of any limitations or advice regarding how short-term wubi is.

I'm not sure myself... but I just don't think it's quite so clear cut. The problems are identified bugs and will likely be fixed - one would hope.

---


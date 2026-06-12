---
title: "/home permissions changed overnight...help?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by OneEightyProof on 2010-06-01
I went to bed last night, had some really weird dreams, woke up this morning, and my /home directory had all been locked down as read only, with everything set to group 500. I rebooted, and got a message that Kubuntu couldn't find the disk, so I rebooted yet again, and everything seemed fine, except everything is still set to group 500, despite having full read/write access.  Should I be worried that I've had some kind of security breach, or is it a simple precursor to drive failure? The combination of everything here has got me very spooked, and having things change without any input from me gets me really worked up. Hoping for a response to calm my nerves, using Kubuntu 10.04, stock setup!

---

### Post by perlluver on 2010-06-01
With the couldn't find disk, I would say that the hard drive is getting ready to fail.  Under your administration tools, you should have a disk utility, there is smart controls in there for checking the disk.  I would run that and see if any problems are reported.

---

### Post by BoneKracker on 2010-06-01
> **OneEightyProof said:**
> I went to bed last night, had some really weird dreams, woke up this morning, and my /home directory had all been locked down as read only, with everything set to group 500.

You're not taking Ambien, are you? :P

---

### Post by ptn107 on 2010-06-01
Change them back.
```
sudo chmod 700 /home/$USER
```

---

### Post by OneEightyProof on 2010-06-01
Ran the disk check, and it came up with the disk being healthy. I guess having the groups (not just permissions, I know the difference) for all of my files and directories changed to 500 (group 500? what?) overnight was what got me concerned. None of the subfolders or files got changed, although they were read-only before I rebooted as well. I should probably write it off as a symptom of impending disk failure, but I wanted to check and be sure.

---


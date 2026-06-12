---
title: "1/Ubuntu 8.10 does not boot, 2/running on live CD,files not accessible"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Gyorgy on 2009-03-26
Dear Community,
I am asking (desperately) for help on below subjects:

1 / How can I restore the OS in such manner, that my previos files to be 'saved/rescued/restored/ or further usable..

2/ How can I access my files with usage of live CD. Up to now, I couldn't.

Description of phenomena :

A/ error messages during boot sequence 
(0.033494) ACPI : aborted because invalid compressed format (err=2)
(0.692987) invalid compressed format (err=2)
(0.694795) kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block (0,0)

B/ boot from Live CD, than 'Places'/navigating to the filesystem of HD, home/documents/. On the upper right corner of the icons of desired folders, there is a small envelope.
Clicking on th icon of the folder, it returns the below error message:

"the folder contents could not displayed. You do not have the permissions necessary to view the contents of 'foldername'

(I am not a root , perhaps ?)

In your kind answers please consider the fact as I am novice to Linux/UBUNTU 8.1.

Thanks a lot in advance.

Gyorgy

---

### Post by cariboo on 2009-03-27
When you are at the desktop of the LiveCD, press Alt-F2 and type:

```
gksu nautilus
```

the reason you can't access the files is that when running the LiveCD your user name is ubuntu, whereas running normally your username is Gyorgy, (or whatever your normal user name is). Linux is a multiuser system, and for security purposes normal users don't have access to each others documents.

Jim

---

### Post by James_Lochhead on 2009-03-27
> **Gyorgy said:**
> 
(I am not a root , perhaps ?)


Exactly. The afore mentioned instructions should help you solve this problem.

---


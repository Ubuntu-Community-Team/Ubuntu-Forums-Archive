---
title: "Cannot clone Virtualbox disks"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by sarc on 2010-10-18
Ubuntu10.4, Virtualbox 3 from repos, works fine but when I try different ways to use VBoxManage to clone a disk it works fine... except the cloned disk is not shown in the disk manager and I cannot find the VDI file anywhere on my hard disk.  Could it be that VBoxManager cannot write the new disk?  Here is what I tried:

1st way:
1. Go to my virtual machine folder
2. sudo VBoxManage clonehd source.vdi target.vdi

2nd way:
me@computer:/usr/lib/virtualbox$ sudo VBoxManage clonehd /media/Machines/WinXPclean/WinXPclean.vdi WinXP.vdi
Oracle VM VirtualBox Command Line Management Interface Version 3.2.10
(C) 2005-2010 Oracle Corporation
All rights reserved.

In both ways I get something like below, but no ned vdi file!!!

0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Clone hard disk created in format 'VDI'. UUID: d8993fcc-6022-45c7-82fc-bab5de6dff39

Thanks for help

---

### Post by jtarin on 2010-10-18
Example:
```
VBoxManage clonevdi ~/.VirtualBox/VDI/WindowsXP.vdi ~/WindowsXP_Backup.vdi
```

NOTE:  Although I&#8217;m not specifically sure, sometime after Version 2 of this software, the clonedvi command has been replaced with clonehd (see page 108 of the VirtualBox Manual), however, clonedvi will still work as they kept the backwards compatibility.

Then, wait for it to complete. It may take a while depending on the size of your .vdi file (or how much space you allocated towards your virtual machine).
What this actually does is create a new UUID (Universal Unique Identifier) for the cloned VM.
This should end up in you /home directory.

---

### Post by sarc on 2010-10-18
Thank you very much jtarin.  The solution was to include the full path for both source and target machines and to make sure the paths point to different folders!  Got it from the code you showed in your answer!  Thanks!

---

### Post by jtarin on 2010-10-18
Yea overwriting is a thing of mystery. :)
Your welcome.

---

### Post by raffen on 2010-10-28
> **sarc said:**
> 
me@computer:/usr/lib/virtualbox$ sudo VBoxManage clonehd /media/Machines/WinXPclean/WinXPclean.vdi WinXP.vdi

I apologize for updating an old thread, but I happen to be puzzled by the same thing: 

The result of the above command creates 

```
/root/.VirtualBox/HardDisks/WinXP.vdi

```

---


---
title: "Permission Problem Removing an Office12 Folder"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by mikodo on 2011-05-28
I thought for fun :( I would try using Wine for the first time. I installed Wine with Software Center (1.2 I think) and tried to install an old Microsoft Office 2007 disk and messed-up the install.

Now I have a locked file of it with an icon sitting on my Desktop, that I cannot send to the Trash or delete spewing the following:

```
the file "OFFICE12" cannot be moved to the trash.

Unable to trash file: Permission denied

```And when I try to delete it spits errors stating I cannot!

I know I have given very little information, but I don't know what to share.

Is there an easy way to make this file go away?

Oh .. I used Ubuntu Lucid for this fiasco. 

I am going to run a restore of my last backup of my /home to see if that will remove it.

I have to go ... Any forthcoming questions; I'll try to answer later today.

Thanks!

---

### Post by mikodo on 2011-05-28
I decided to remove the file (albeit dangerously) by:

Hitting Alt +F2 and entering gksudo nautilus to gain rootly powers. Found the directory and moved it to Trash successfully. Then got out of sudo, as I was afraid I would make a mistake and remove something needed for the system.

Thanks everyone.

---


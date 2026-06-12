---
title: "tips for copying files to external drive"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by AlanRick on 2009-07-12
I'm trying to copy a large file (14 Gbytes) to an external portable drive but ubuntu freezes during the copy. It freezes at different points so it's some sort of sporadic error.

Any hints about how to copy reliably (speed is not an issue)?

Here are the details:
[LIST=1]
[*]External drive is ntfs.
[*]I do a chksdk /f from a Windows PC to remove errors from last run.
[*]I've disabled wireless and lan before copying.
[*]I have managed to copy up to 12 GB before it freezes
[/LIST]

Suggestions more than welcome :-)
Alan

---

### Post by ~sHyLoCk~ on 2009-07-12
I've expereinced this while copying larger files over to a different partition. It seems that copying has frozen but it's actually going on and after a while things go back to normal. However I'm talking about copying 1-2Gb files so dunno how long you have to wait for 14gigs.

---

### Post by AlanRick on 2009-07-12
good point. It freezes after about 2 - 20 minutes. And it is definitely frozen (no more progress even if I wait for an hour).

---

### Post by MrWES on 2009-07-12
> **AlanRick said:**
> I'm trying to copy a large file (14 Gbytes) to an external portable drive but ubuntu freezes during the copy. It freezes at different points so it's some sort of sporadic error.

Any hints about how to copy reliably (speed is not an issue)?

Here are the details:
[LIST=1]
[*]External drive is ntfs.
[*]I do a chksdk /f from a Windows PC to remove errors from last run.
[*]I've disabled wireless and lan before copying.
[*]I have managed to copy up to 12 GB before it freezes
[/LIST]

Suggestions more than welcome :-)
Alan

Weird...seems like you're having issues with the VFAT 4gb limit. Can you output the following command from the terminal:
```
sudo fdisk -l
```(lower case L) -- just to make sure the drive is definitely being reported as ntfs.

~Bill

---

### Post by credobyte on 2009-07-12
The easiest way would be to split your file into smaller pieces and transfer them separately ( try 7zip ).

---


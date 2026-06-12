---
title: "Read Only File System"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by lile001 on 2011-08-27
I have a thumb drive with a strange problem.  I can't move files off if it, because it apparently has a "read only file system".  I can't modify permissions on the memory stick with sudo chmod, it always responds that it has a "read-only file system".    How can I change this?

---

### Post by quadproc on 2011-08-27
Perhaps you already checked this, but did you accidentally set the write protect switch on the thumb drive?

quadproc

---

### Post by lile001 on 2011-08-27
> **quadproc said:**
> Perhaps you already checked this, but did you accidentally set the write protect switch on the thumb drive?

quadproc

I never knew there was such a thing.  How do you set the write protect switch on a thumb drive?  And how do you unset it?

---

### Post by nothingspecial on 2011-08-27
Is it a non-native file system, eg ntfs or fat

---

### Post by lile001 on 2011-08-27
> **nothingspecial said:**
> Is it a non-native file system, eg ntfs or fat

How would I know?  I bought a thumb drive and plugged it into my computer.  Can you explain to me how to find out?

---

### Post by quadproc on 2011-08-27
> **lile001 said:**
> I never knew there was such a thing.  How do you set the write protect switch on a thumb drive?  And how do you unset it?
Not all thumb drives have the switch, but those that do usually implement it as a tiny rectangle of plastic near one corner of the drive.  It may not be obvious, and you may need a tiny screwdriver or something similar to move it.  Think of a little bitty slide switch.

Regarding the file system types, you can use gparted to report on the file system structure on the drive.  Just fire up gparted and select the thumb drive, then look at the table of partitions.  If you don't have gparted then you can get it using synaptic or apt-get.

quadproc

---

### Post by kyletstrand on 2011-08-27
What's the brand and model of your thumb drive?  We can look up the specs to see if that can be of any help.

---


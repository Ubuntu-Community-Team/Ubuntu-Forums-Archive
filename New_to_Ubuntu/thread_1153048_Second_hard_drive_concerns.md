---
title: "Second hard drive concerns"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by GreggyZed on 2009-05-08
Hello,

On Monday I plan on purchasing a nice 1000GB hard drive that I saw for a decent price around here.  I currently have a Windows XP / Ubuntu dual boot on one hard drive.

What I plan on doing is to copy my music, pictures, and documents onto the second hard drive (which are all accessed on the Windows partition and install any future Windows programs onto this hard drive.

Is it possible to have Ubuntu applications installed on this second hard drive as well?

In short, how do I set up a hard drive to be not the boot drive but have Ubuntu applications, Windows programs, and general files stored on it?

---

### Post by nandemonai on 2009-05-08
> **GreggyZed said:**
> Hello,

On Monday I plan on purchasing a nice 1000GB hard drive that I saw for a decent price around here.  I currently have a Windows XP / Ubuntu dual boot on one hard drive.

What I plan on doing is to copy my music, pictures, and documents onto the second hard drive (which are all accessed on the Windows partition and install any future Windows programs onto this hard drive.

Is it possible to have Ubuntu applications installed on this second hard drive as well?

In short, how do I set up a hard drive to be not the boot drive but have Ubuntu applications, Windows programs, and general files stored on it?

You don't. Linux applications are split over the file system in different places. To do what you want you'd need to mount the drive as your /

---

### Post by GreggyZed on 2009-05-08
> **nandemonai said:**
> To do what you want you'd need to mount the drive as your /

I'm sorry but I don't understand this statement...

---

### Post by Celauran on 2009-05-08
> **GreggyZed said:**
> I'm sorry but I don't understand this statement...

/ is the root mount point, roughly equivalent to C:\ in Windows.

Unlike Windows, Linux does not install applications to one directory. Configuration files for most applications will be in /etc, libraries (akin to .dll files) will be in /lib, and so on. As a result, what you're suggesting won't work out so well.

What I'd recommend would be to keep this second drive for data from both Windows and Linux, and use the existing drive only for applications. Under Linux, you could have the new drive mount under /home/username or /home/username/data or whatever.

---

### Post by GreggyZed on 2009-05-08
That's perfect, thanks for the tips.  In 14 minutes the question was answered, awesome!

---

### Post by powel212 on 2009-05-08
The question still remains. Why?

P.

---


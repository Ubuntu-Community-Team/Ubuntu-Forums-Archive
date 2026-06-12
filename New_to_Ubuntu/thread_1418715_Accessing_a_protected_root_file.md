---
title: "Accessing a protected root file"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by p3ar on 2010-02-28
I am trying to open a file system that is password protected with root-only access.  Since I am working from a different computer, how do I get into this system? If I try to use the sudo command, it works on the computer I'm typing on, and not the filesystem I'm trying to access.  Any ideas?

---

### Post by undecim on 2010-02-28
How are you trying to access this file system? Is it connected via USB to the computer you're working on?

And do you know how this system is protected? Is it an encryption, or does the OS require a user password to view it?

---

### Post by p3ar on 2010-03-01
> **undecim said:**
> How are you trying to access this file system? Is it connected via USB to the computer you're working on?

And do you know how this system is protected? Is it an encryption, or does the OS require a user password to view it?


I accidentally deleted the OS on my system through synpatic somehow and I desperately need to retrieve one of the files from the Desktop.  I can see it is still there if I navigate through the command line interface, but my attempts to copy the file onto a thumb drive have resulted in other computers saying the thumb drive needs to be formatted.  So now my attempt is in accessing the filesystem through a boot CD.  But if you have any other ideas, I'd be thrilled.

---

### Post by undecim on 2010-03-01
Is the thumb drive already formatted to a FAT filesystem? If you don't have any important files on the drive, try formatting it from the computer that you are trying to move it to (the one that says it needs to be formatted), then try copying it over from an Ubuntu Live CD to the thumb drive.

If the thumb drive is still giving you problems, you can try transferring it over the network, either by sharing the Desktop folder from the Live CD, or by drag-dropping it to a shared file on another computer.

---

### Post by p3ar on 2010-03-01
> **undecim said:**
> Is the thumb drive already formatted to a FAT filesystem? If you don't have any important files on the drive, try formatting it from the computer that you are trying to move it to (the one that says it needs to be formatted), then try copying it over from an Ubuntu Live CD to the thumb drive.

If the thumb drive is still giving you problems, you can try transferring it over the network, either by sharing the Desktop folder from the Live CD, or by drag-dropping it to a shared file on another computer.


I have formatted the thumbdrive to a FAT system on the working PC prior to transferring the file from the "broken" one, so I don't think that's going to work.

Your second option I do not know how to do.  This time, when I booted from the Live CD, I can't even see the filesystem.  I'm not sure how I got it to appear last time, either ..  And when I try to access the file that way, I run into the issue of not having permission to access the root-protected files.

---

### Post by undecim on 2010-03-01
You should be able to mount the filesystem by clicking the link to it in the sidebar in a file browser. If you mount it like that, you should also be able to view the files without root access.

---

### Post by p3ar on 2010-03-01
Last time I could access the file system, it would tell me I didn't have access to files under home/user/

---


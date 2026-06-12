---
title: "SSH Server and NTFS Partition"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-08-09
I plan on hosting an SSH server on my laptop so I can share music/videos with friends through sftp. To do this, I set up an account that essentially can only access its home directory with symlinks to my music/video folders. That's the first issue, you can't change permissions of symlinks but I don't want someone accidentally deleting one because I'd have to set it up again. What can I do about that? 

Secondly, one of the folders is on an NTFS removable hard drive and so I'd want that folder to be read-only, so users cannot delete my files by accident. However, I don't want to mount the whole drive as read-only because I have my laptop automatically backing up to it, so I'd need write permissions. Is there any way around this other than reformatting the drive to ext3?

-SMRT

---

### Post by dlmarti on 2009-08-09
There are like 10 questions, in this single post  :)

I will address the fundamental one.

What you are looking for is to create a group that has READ access, but not write access to that directory tree.  You will retain your WRITE access as owner.

Honestly though, I encourage you NOT to share files that you do not have rights too.
Take the morale high ground, the air is better up here.

---

### Post by I[AM]SMRT on 2009-08-10
Yea, I know how I *want* the permissions to be, it's just that for symlinks/NTFS drives it appears that I'm unable to change the permissions. I've decided to reformat my removable HD to ext3 so that solves that problem but I still don't know what to do about the symlinks.

---

### Post by dlmarti on 2009-08-10
> **'I[AM]SMRT said:**
> Yea, I know how I *want* the permissions to be, it's just that for symlinks/NTFS drives it appears that I'm unable to change the permissions. I've decided to reformat my removable HD to ext3 so that solves that problem but I still don't know what to do about the symlinks.

Not sure what the question about the symlinks are.
If you have a directory in your account with group read, and owner read/write, and everyone else has symlinks to it.  That should work.

---

### Post by I[AM]SMRT on 2009-08-10
> **dlmarti said:**
> Not sure what the question about the symlinks are.
If you have a directory in your account with group read, and owner read/write, and everyone else has symlinks to it.  That should work.
I don't want people deleting the symlinks by accident.

---

### Post by dlmarti on 2009-08-10
What exactly are you trying to do?

You don't actually need the symlinks anyways, they can always just go to your account if the group permissions are setup correctly on the directory.

---

### Post by I[AM]SMRT on 2009-08-10
I just want to make symlinks so they can easily navigate to the folders, otherwise, they probably wouldn't be able to find them.

---

### Post by dlmarti on 2009-08-10
you would have to play around with the permissions, maybe put the symlinks in a folder that they didn't have delete rights too.

---


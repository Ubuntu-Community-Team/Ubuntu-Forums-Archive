---
title: "NTFS permissions seem to change"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by w_barnes on 2010-12-24
Hi all,

I have an encrypted NTFS volume that I access using TrueCrypt. As I understand it, Linux cannot set permissions on an NTFS volume so permissions are defined at the time the volume is mounted and applied to all files.

On my volume, the permissions are "rwxr-xr-x user:root" however after creating/editing files some of the permissions have changed and these seem to be persistant. That is, when I dismount the volume and remount these files have the same odd permisions.

What's going on here? has my volume been corrupted? or are non-default permissions permissions stored somewhere else without actually changing the NTFS volume?

---

### Post by w_barnes on 2010-12-24
Well, I figured a few things out...

 I ran chmod on an ordinary NTFS volume it has no effect as expected but when I ran chmod on my TrueCrypt NTFS volume it succesfully changed the file permissions.

I'm thinking that TrueCrypt is maintaining the file permissions some how.

Anyone know how it is doing that? Does TrueCrypt change the permissions on the disk or does it maintain its own permissions for the volume elsewhere?

---


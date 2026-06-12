---
title: "Mounting a CIFS share from a Windows box.  Permissions issue."
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by 1clue on 2013-09-13
Hi.

I have a CIFS mount permissions issue, and I'm not really that good with this sort of thing.

I have a Windows box which is sharing a directory.  The share's access is limited to a single Windows user whose sole function is to be permissions for this share.

I have an Ubuntu Server box which has the directory mounted.  The mount specifies the Windows user to log in as.

As a user on the Linux system, I can 'sudo touch something' and get a 'something' file on the share.  As a normal user I can't create a file.

I have a nonhuman login on the Linux box (a service running as non-root user who can't log in) which is trying to read and write the shared directory.

I need the service user to be able to read and write this directory, and I need a human user to be able to read and write it, hopefully without changing anything on the Windows side.  Making the directory world-writable on the network is very bad.

I've briefly caused the share to be read/write for everyone, and suddenly things work fine.  Again, this is not acceptable.  I need to fix this on the Linux side if possible.

Thanks.

---


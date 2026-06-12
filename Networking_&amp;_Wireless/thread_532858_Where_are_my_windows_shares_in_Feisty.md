---
title: "Where are my windows shares in Feisty???"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by cudds on 2007-08-23
I've mounted my windows' share drives use the fancy wizard and I'm loving the way Ubuntu is holding them all together and placing links on my desktop.
What I don't know though is where all these are on my filesystem. When I've mounted stuff before with fstab I've put it in /media/ and that's where my 'c: drive' is, but I can't find my other SMB connections unless I go via my desktop. Please help!!!

---

### Post by gashcrumb on 2007-08-23
I believe when you use nautilus to access a windows share it doesn't actually mount that share in your filesystem.  The smb:// address uses "vfs" to make the share appear like it's a local filesystem, but it really isn't.

You can do "mount -t smbfs hostname://share /media/some_share" manually from a terminal, though really getting at remote shares via nautilus is much nicer.

---


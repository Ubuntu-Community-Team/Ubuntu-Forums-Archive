---
title: "fstab instructions?"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by spudley on 2005-06-19
Are there 'instructions' for fstab format somewhere?  I can't seem to find details on what goes where.

My latest fstab entry is this:
//nas-media/disk1 /media/r smbfs username=xyz,password=123,workgroup=abc,uid=me 0 0

I have RW access for user 'me' which was the initial account I setup when installing Hoary.  However, I now added user 'kids', and then put user 'kids' and 'me' into a group called 'nasusers' and then replaced 'uid=me' to 'gid=nasusers'.  After a reboot, 'me' and 'kids' have R only access.

//nas-media/disk1 /media/r smbfs username=xyz,password=123,workgroup=abc,gid=nasusers 0 0

I've seen 'umask' in various fstab entries, but haven't a clue what thats about.  Can anyone shed some light on fstab for me?

Thanks!

---

### Post by GilGalad on 2005-06-19
The options in fstab are sent to mount when mounting the filesystem. Therefore you can find about the meaning of them, including umask,  by looking at the manual page of mount, in your case the smbfs version ('man mount.smbfs').

---

### Post by xmastree on 2005-06-19
[QUOTE=spudley]I've seen 'umask' in various fstab entries, but haven't a clue what thats about.  Can anyone shed some light on fstab for me?[/QUOTE]

man fstab may also help.

---


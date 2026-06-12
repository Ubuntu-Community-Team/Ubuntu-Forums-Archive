---
title: "CIFS mount failed ( Unable to access NAS)"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by gav-the-lad on 2008-04-27
Hello all, I recently switched from xp to ubuntu a coupe of days ago and i have a Buffalo Linkstation Live (NAS) that has all my mp3's. I can play my mp3's through rythmbox, but when i try to access the drive from places > network > workgroup, the drive is showing as empty. What do i need to do to access the Linkstation? This is what i got when i accessed the terminal > dmesg:


[10120.595490] CIFS VFS: cifs_mount failed w/return code = -6
[10120.788807] CIFS VFS: cifs_mount failed w/return code = -6
[11586.766101] CIFS VFS: cifs_mount failed w/return code = -6
[11586.961049] CIFS VFS: cifs_mount failed w/return code = -6
[11716.727568] CIFS VFS: cifs_mount failed w/return code = -6
[11716.952565] CIFS VFS: cifs_mount failed w/return code = -6
[12046.244091] CIFS VFS: cifs_mount failed w/return code = -6
[12046.426883] CIFS VFS: cifs_mount failed w/return code = -6

---

### Post by gav-the-lad on 2008-04-27
can anyone help?

---

### Post by MountainX on 2008-06-04
Did you ever solve this? This is the same error I am getting in this thread:
[http://ubuntuforums.org/showthread.php?p=5113379#post5113379](http://ubuntuforums.org/showthread.php?p=5113379#post5113379)

What I have found so far is that this error apparently means that the server thinks that share isn't a valid share. I have no idea why because Windows can access that share.

---


---
title: "Admin for file browsing?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by TironN on 2009-11-01
Hey guys.
How would I get root privileges for file browser as I am trying to copy something from the desktop to another drive and it is giving me a permission error.
Ideas?

---

### Post by quinnten83 on 2009-11-01
In terminal type gksudo nautilus
enter your password and you can now browse as root.
what are you brwosing that is giving you permission errors? External drives should just work...

---

### Post by TironN on 2009-11-01
Well technically its not an external drive. Its a separate partition left over from my windows install but has been reformatted to FAT32 and fstabbed into the system (with read write privileges mind you) but its letting me browse just not copy a folder with music from the desktop to this partition!

---

### Post by shuttleworthwannabe on 2009-11-01
I seemed to remember there being a 'nautilus script' where we could right click the drive/folder/file and 'open as root'--does this exist anymore in GNOME? KDE has this I think?

S

---

### Post by TironN on 2009-11-01
No open as root. But gksu nautilus is fine for now! Thanks guys

---


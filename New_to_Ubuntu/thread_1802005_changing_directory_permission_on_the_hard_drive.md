---
title: "changing directory permission on the hard drive"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by vigeek on 2011-07-11
the permissions for the folders on my hardrive cant be changed what to do?and after changing the permissions will this be applicable for windows?

---

### Post by abybaddi on 2011-07-11
You can change the permissions only if you own the folders. eg. permissions for folders on /dev/sdx1 cannot be changed. But you can set the permissions of the folders in your home folder.

And the applied permissions would be only applicable to linux.

---

### Post by CatKiller on 2011-07-11
> **vigeek said:**
> the permissions for the folders on my hardrive cant be changed what to do?

You're unlikely to need to change the permissions. If you tell us what you're trying to do, we might be able to help you.

---

### Post by dcsoldschool53 on 2011-07-11
You can change any folder or directory that belongs to you. To see what the permission of the directory is,  start the code off by using```
ls -l
```

---

### Post by AlphaLexman on 2011-07-11
If your hard drive is formatted as a NTFS partition (Windows default), it cannot save *nix permissions after a reboot.

---

### Post by mapes12 on 2011-07-11
Your post isn't very clear but if you are referring to permissions on a Linux partition then what I do is launch nautilus with root permission like this. Applications>Terminal ```
gksudo nautilus 
```It will ask for your password. Then navigate to the folder where you want to change permissions, right click the folder>Properties>Permissions. Make the changes then close down the root nautilus session to avoid unnecessary mistakes as root.

Mark

---


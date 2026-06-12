---
title: "Permission help please"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Diametric on 2010-11-21
I downloaded a folder and I cannot copy it to my thumb drive.  The folder has a .rar in it - I changed the permissions of that folder to be: -rwxrwxrwx and when I attempt to copy the folder to the USB the error states that it is a read only file.  What am I missing?  

Thank you.

---

### Post by mapes12 on 2010-11-21
Launch Nautilus with su permissions like this ```
gksudo nautilus
```then try moving your folder. You can also reset the folder permissions when using Nautilus this way. Right click the folder, Properties>Permission.

Then close down su Nautilus to avoid doing something that may screw up your system. 

Don't delete anything with su Nautilus without holding the Shift key down at the same time as pressing delete otherwise it will not be properly deleted. Just a tip from a bad experience.

Mark

---

### Post by Diametric on 2010-11-21
Cool.  Thanks for the reply.  I just couldn't figure out why will all permissions assigned it still wouldn't let me move the folder...oh well.

---


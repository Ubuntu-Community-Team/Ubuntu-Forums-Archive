---
title: "Acrobat Save and Permissions"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by kendoori on 2009-08-03
I am running 9.04 with Acrobat Reader 9.10. I have a separate NTFS partition that I share with Windows that I'm trying to save documents from within Acrobat to. Whenever I try to save a file (Save a Copy) whether doing this from within the Firefox plugin, or from the Reader directly, Acrobat says "You do not have permissions to write to the file."

I have no issues writing to any of these directories from other applications (e.g. OpenOffice, or even saving via Firefox as HTML).

BTW, the owner of these directories is "Root"

I have no issues if I try to save to the native ext3 partitions.

---

### Post by llamabr on 2009-08-03
You'll need to change the permissions on the dir.

As a workaround, you can 'save a copy' to your home directory, then allow sudo to move it to the shared dir:

```
sudo mv ~/nameoffile.pdf /your/shared/dir/
```

---

### Post by panache on 2009-08-10
Hey,

I have a similar problem, except that the Adobe plugin won't even save to the native ext3 partitions.
I can save to the desktop no worries, but drilling down into the file system I encounter problems trying to save.

Changing the permissions of all the directories I may wish to save to seems like an odd solution, especially when it is possible for other plugins / firefox itself to save to these directories.

Is it possible to get the acrobat plugin to start with greater write privileges?

Cheers
Sam

---


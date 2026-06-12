---
title: "Accidentally deleted mnt folder from File System"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Oblivion4234 on 2010-07-31
Hello, just to clarify I am fairly new with ubuntu and linux in general so a little patience would be greatly appreciated. I installed Linux on my computer and afterwards tried to install MySQL and Apache on it from a CDrom. Long story short there was a bug so i deleted the mount file on my file system previously labeled mnt. Now it is gone and I do not know how to add a file/folder to the File System so as to start from scratch with my installation of MySQL and Apache. Could someone please tell me how to add a folder/file to the File System.

---

### Post by sydbat on 2010-07-31
> **Oblivion4234 said:**
> Hello, just to clarify I am fairly new with ubuntu and linux in general so a little patience would be greatly appreciated. I installed Linux on my computer and afterwards tried to install MySQL and Apache on it from a CDrom. Long story short there was a bug so i deleted the mount file on my file system previously labeled mnt. Now it is gone and I do not know how to add a file/folder to the File System so as to start from scratch with my installation of MySQL and Apache. Could someone please tell me how to add a folder/file to the File System.Press F2. The 'Run Application' windows pops up. Type **gksudo nautilus** in the top box. Click 'Run'. This will prompt you for your password. 

After entering your password, you will be in your root folder. On the left there should be a list, one of which is 'File System'. Once in 'File System', create a new mnt folder (or whatever folder you like).

When finished, remember to close the root window so you do not "accidentally" remove any important files/folders. :)

---

### Post by bodhi.zazen on 2010-07-31
Or simply```
sudo mkdir /mnt
```

---

### Post by Oblivion4234 on 2010-07-31
Thank you bodhi, that worked perfectly. I tried doing that last time and it did not show up, i guess I simply did not close my File System window for it to show that folder. Thank you very much for your assistance.

---

### Post by sydbat on 2010-07-31
> **bodhi.zazen said:**
> Or simply```
sudo mkdir /mnt
```Show off. :p

---

### Post by bodhi.zazen on 2010-07-31
> **sydbat said:**
> Show off. :p

:lolflag:

---


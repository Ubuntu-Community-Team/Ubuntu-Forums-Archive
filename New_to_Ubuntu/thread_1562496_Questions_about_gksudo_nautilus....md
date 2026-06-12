---
title: "Questions about gksudo nautilus..."
date: 2010-08-27
forum: New to Ubuntu
---

### Post by TheEddy on 2010-08-27
Hi, I just recently installed ubuntu and xampp and find the only way to be able to edit my files in the htdocs folder in the lamp directory is to use gksudo nautilus.  Is there another way to do this?

---

### Post by AlphaLexman on 2010-08-27
Are they really 'your' files, as in you are the owner? Or do they belong to 'root'?
Check the ownership by typing:
```
ls -l
```in a terminal.
If they belong to root, you can change ownership by:
```
chown username file
```But, you may not want to do that... Usually Linux standards dictate a system-wide config file and a user-specific config file. Look in your 'home' directory for a hidden file that might correlate with the 'root' file.

---

### Post by ajgreeny on 2010-08-27
The simplest way is to install nautilus-gksu.  Now you can right click on a folder or file and the context menu will have an added item, "Open as administrator".

Enter your password and a new nautilus window will open as root for a folder, or the file will open in the appropriate default application if a file and allow you to edit and save.

I have no idea about xampp or the htdocs folder to know who should own them.

---

### Post by wojox on 2010-08-27
You can also open a terminal and use *sudo nano*

---


---
title: "hiding folders in 8.04 or 9.04"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by misswham on 2009-11-26
First off Happy Holidays to all who celebrate and good evening to whom who dont.  I would like to know if i could lock a folder in my documents to keep someone from seeing the files?  Like, if I have personal documents in a certain folder and someone clicks on documents, can i fix it where you need a password to open just that one folder?

---

### Post by bwang on 2009-11-26
In 8.04, you can encrypt files by right-clicking and selecting Encrypt...
Use System>Preferences>Encryption and Keyrings to create a password.

---

### Post by herbertportillo on 2009-11-26
I'm not sure about putting a password on a folder and locking it, but if you put a period in front of a folder (for example, changing 'video' to '.video') the folder will be hidden from view.

If you press 'Ctrl + H' in the file manager, you can see the hidden folders. Also, 'ls -A' in the Terminal shows the folders that begin with a period.

---

### Post by koba101 on 2009-11-26
why don't you just change the permissions of the folder so that no one could see it?

sudo chmod -R 000 [folder name]

and to unlock it  something like 

sudo chmod -R 755 [folder name]

---


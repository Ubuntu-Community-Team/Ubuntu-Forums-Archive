---
title: "password protection"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-07-09
is there a way for me to enable a password for the files or folders of my choosing?

---

### Post by milton1 on 2009-07-09
you could set permissions to 000 and then you would use sudo to set them back and access them. This would require password access.

---

### Post by 289531.EXE on 2009-07-09
how do i go about doing this?

---

### Post by milton1 on 2009-07-09
```
man chmod
``` in the terminal will give you information on using the cmod command to change permissions. You can then change permissions for folders or files of your chosing. Example: ```
chmod 000 myfile.txt
``` sets the permissions for myfile.txt to forbidden to all users and groups, including the file owner.

---

### Post by pythonscript on 2009-07-09
milton1 beat me to it.

---

### Post by 289531.EXE on 2009-07-09
well i would like to set it so that i have access to the file with my regular password but that no one else would be able to get in without the password

---

### Post by milton1 on 2009-07-09
with chmod, you can easily switch the permissions back so you have access using sudo chmod.

---

### Post by 289531.EXE on 2009-07-09
im just not sure how to do that or undo it how do i choose the  specific file i want private?

---

### Post by Elep.Repu on 2009-07-09
Try out Truecrypt if you find this too difficult or lacking.
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by cariboo on 2009-07-10
Why not create seperate limited accounts for anyone else that uses your computer, and don't tell them your password. After all Linux was designed as a multi-user system.

A limited account that isn't in /etc/sudoers will only have access to and be able to change files in their own home directory.

---

### Post by 289531.EXE on 2009-07-10
actually how would i know if theres any infections on my computer

---

### Post by mthalis on 2009-07-10
what kind of infection?

---

### Post by 289531.EXE on 2009-07-10
i know i was told that i should forget about malware and trojans and viruses but im just very sceptical by "nature"

---

### Post by mthalis on 2009-07-10
Normaly less attack if you like you can use "clamav"

---

### Post by 289531.EXE on 2009-07-10
how does that work?  how do i install it and  do i need to register and all  that nonesense?

---

### Post by mthalis on 2009-07-10
Go synaptic package manage and search and install.

---

### Post by mthalis on 2009-07-10
Read this
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---


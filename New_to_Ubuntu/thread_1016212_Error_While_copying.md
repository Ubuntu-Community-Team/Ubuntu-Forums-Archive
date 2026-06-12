---
title: "Error While copying"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Archer Troy on 2008-12-19
I connect to a hard disk on my network though smb://xx.xx.xx.xx and im trying to pull some files off of it to another computer...but i get an error. it says

ERROR WHILE COPYING

The folder "FOLDER" cannot be copied because you do not have permissions to create it in the destination.

does anyone know how to set the permissions for it to allow me to do this?

---

### Post by GMachine_24 on 2008-12-19
Where are you trying to copy it to? It sounds as if you need to set the permissions to allow yourself to write to the drive (or whatever) where you want to paste/copy the folder

Usually, you use the "chmod" command to set read/write permissions for a particular location

You can use the

```


man chmod | more


```

command in a terminal to find which arguments you need to use. Typically, I enable read/write capability for all users on my computer which takes this form

```


sudo chmod 777 /media/nameofdrive


```

(instead of using "777" you can also use "rw" to set read/write permissions for users, group, etc. ... again, check the chmod man pages)

"nameofdrive" is, of course, the location where you want to copy the folder.

---

### Post by Fahuadai on 2008-12-19
Who owns the destination directory?

ls -l <destinationDir>


To change ownership: 
chown <yourUsername> <destinationDir>

---


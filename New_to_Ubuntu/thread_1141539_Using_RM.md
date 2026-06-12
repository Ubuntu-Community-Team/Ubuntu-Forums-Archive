---
title: "Using RM"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Drenriza on 2009-04-28
When i try to delete a folder, containing subfolders and files. the command rm (file name) won't work. So im wondering what i need to add to rm to be able to delete the folder and it's content in the command-line-interface. 

Thanks on advance, best regards Dren

---

### Post by nandemonai on 2009-04-28
```
man rm
```

You're after the -r switch but please.. Do take care using this command. One typo can mean losing a lot of data.

---

### Post by Pisi-Deff on 2009-04-28
You can always check the manual for the command :)
```
man rm
```

Together with other stuff, it says: 
```
       -r, -R, --recursive
              remove directories and their contents recursively
```

edit:// sniped >.<

---

### Post by kukibird1 on 2009-04-28
> **Drenriza said:**
> When i try to delete a folder, containing subfolders and files. the command rm (file name) won't work. So im wondering what i need to add to rm to be able to delete the folder and it's content in the command-line-interface. 

Thanks on advance, best regards Dren

rm -r

---

### Post by Drenriza on 2009-04-28
Thanks for the replies. But unfurtiantly i can't delete the file using
rm -r filename. what i wanna delete is a folder on my desk a "test folder" if u can call it that.

It's been given the name Usb Backup and putted some stuff into it.
but when i type rm -r Usb Backup it says it cannot delete the file or dictorary....???

---

### Post by SuperSonic4 on 2009-04-28
You need to be in the directory occupied by Usb backup. Plus you need to write it as Usb\ Backup to signify the space

---

### Post by kiridude on 2009-04-28
```
cd /home/username/Desktop
```

then rm -r [name of file]

note: substitute your username for "username"

or simply:

rm -r /home/username/Desktop/filename

---


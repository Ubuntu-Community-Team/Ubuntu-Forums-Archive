---
title: "Cant delete file in trash"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Swatfoot on 2009-04-09
Im trying to empty my trash but there is one folder that will not delete
I've tried gksudo nautilus and going to trash but it says cannot view files
and was wondering how do i get to the trash in terminal so I can "rm -r" the folder. or change permissions rwx for all then delete it .

---

### Post by Michael.Godawski on 2009-04-09
hi Swatfoot, 


These are the common paths to the trash folders:
     
[LIST]
[*]**/home/username/.share/local/Trash** User's Trash (hardy and later)
[*]**/home/username/.Trash** User's Trash (pre-hardy)
[*]**/root/.local/share/Trash** Root Trash (hardy and later)
[*]**/root/.local/share/Trash** Root Trash (pre-hardy):
[*]**/.local/share/.Trash-1000** NTFS/FAT32/etc: The user`s name is part of the trash name. So user 1000 which has deleted something creates the Trash-1000 folder.
[/LIST]
you can try:

```
rm -rf ~/.local/share/Trash/*
```
 If you get permission problems try to slip a sudo in front of the commands, but **be sure that the path is correct**.


 Sometimes it is necessary to change the ownership of the thrash files:
 ```
sudo chown -R yourusername /home/yourusername/.local/share/Trash
```

---

### Post by Swatfoot on 2009-04-09
Thank you this worked like a charm "rm -rf ~/.local/share/Trash/*".

---

### Post by david_ally on 2009-09-15
I couldn't even access the Thrash directory, even with sudo. The folder is there but could not be accessed, it gives the error there is no file nor directory name Thrash. 

i have tried working from the shell root and could not still access the files in the Thrash folder.

---

### Post by jerrrys on 2009-09-15
> **david_ally said:**
> I couldn't even access the Thrash directory, even with sudo. The folder is there but could not be accessed, it gives the error there is no file nor directory name Thrash. 

i have tried working from the shell root and could not still access the files in the Thrash folder.

that would be trash. not thrash

---

### Post by k33bz on 2009-09-15
> **Michael.Godawski said:**
> 
```
rm -rf ~/.local/share/Trash/*
```
 

I would be especially careful with this command, and make sure it is right, if it aint right it will have the potential of wiping out your entire partition.

---


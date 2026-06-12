---
title: "cant delete a folder"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-24
hi i cant delete a folder both in terminal and gui 
in terminal i gave this command 

sudo rm kumaresan /media/Academics/Movies
it says 
rm: cannot remove `Documentry': Is a directory
the file system type is FAT32

when i try in GUI

Error removing file: Permission denied

i dont know how to change the permission 
i have only one user in ubuntu

help thanks ina advance

---

### Post by roccivic on 2009-02-24
add -r option, it stands for recursive ;)

---

### Post by laithbsoul on 2009-02-24
try pressing alt-f2 and entering "gksu thunar" without quotes that should bring up a root file manager delete it from there
report back

---

### Post by SuperSonic4 on 2009-02-24
```
sudo rm -Rfv kumaresan /media/Academics/Movies
```

R = recursive
f = force, do not ask for confirmation
v = verbose - shows what is going on

---

### Post by kellemes on 2009-02-24
> **gkraju said:**
> 
when i try in GUI

Error removing file: Permission denied

i dont know how to change the permission 


For this part you need to start gui with root permissions from a terminal window..
```
gksudo nautilus
```

---

### Post by anaconda on 2009-02-24
just to make sure you want to delete 
kumaresan
And
/media/Academics/movies

because thta will delete both of them..
and kumaresan can be either a file or a folder with subfolders..

---

### Post by gkraju on 2009-02-24
> **SuperSonic4 said:**
> ```
sudo rm -Rfv kumaresan /media/Academics/Movies
```

R = recursive
f = force, do not ask for confirmation
v = verbose - shows what is going on

that worked for folder's only i didnt work for files
i also want to delete files

and please tell how to permission for folder

---


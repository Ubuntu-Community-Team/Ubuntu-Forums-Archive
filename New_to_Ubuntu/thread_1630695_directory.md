---
title: "directory"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by farzanemostafa on 2010-11-25
how to delete directory

---

### Post by pawhtiobo on 2010-11-25
Hi :)

$sudo rm -R /your/directory/path

or 

$gksudo nautilus (GUI)



See ya...

---

### Post by dFlyer on 2010-11-25
> **farzanemostafa said:**
> how to delete directory

If your deleting from your home folder rm -rf should work. If your going to delete from / which you shouldn't do, unless you really know what your doing you will need to use sudo rm -rf.

---

### Post by karthick87 on 2010-11-25
Sudo is not necessary,just type

```
rm -R /path/to/your/folder
```

---

### Post by skillet-thief on 2010-11-25
To delete an empty directory:
```
$ rmdir the_directory
```To delete a directory and everything it contains including all subdirectories:
```
$ rm -R the_directory
```If you are not the owner of the directory, the use sudo. But always be very very careful when doing anything with 
```
$ sudo rm -r
```Think of sudo rm -r as though you were deciding to use a tactical nuclear weapon...

---

### Post by pawhtiobo on 2010-11-25
> **karthick87 said:**
> Sudo is not necessary,just type

```
rm -R /path/to/your/folder
```
  
That depends on what is he trying to delete :P...lolll

---

### Post by pawhtiobo on 2010-11-25
> Think of sudo rm -r as though you were deciding to use a tactical nuclear weapon...LOLL...nice definition :p

---

### Post by farzanemostafa on 2010-11-25
thanks a lot but I can't delete

---

### Post by farzanemostafa on 2010-11-25
thanks it just work and I want know how to create some directory in one line

---

### Post by pawhtiobo on 2010-11-25
Nice...:D

See ya...

---

### Post by pawhtiobo on 2010-11-25
Hi :)

See this, it may help you:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

See ya...

---

### Post by dFlyer on 2010-11-25
> **farzanemostafa said:**
> thanks it just work and I want know how to create some directory in one line

to create a directory is mkdir dir1 dir2 dir3 etc.

---

### Post by farzanemostafa on 2010-11-25
I want know how to create some directory in one line

---

### Post by skillet-thief on 2010-11-25
$ mkdir the_directory

---


---
title: "how do i create a folder that can only be accessed by root?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by goustaroubunta on 2010-03-21
i mean anywhere.. on my other hard drive for example.. i know i can use an already only-root-accessed folder. but that's not a straightforward solution...

i run sudo nautilus then right click on the folder and try to change permissions but they won't change.. does it have anything to do with ntfs etc? i dunno.

---

### Post by howefield on 2010-03-21
Let's say you want a folder called example on a second hard disk, mounted at /media/Data.

Open up a terminal and type the following

```
cd /media/Data
```

Followed by

```
sudo mkdir example
```

Then check the permissions by typing

```
ls -l
```

Should show something like

```
drwxr-xr-x  2 root root     4096 2010-03-21 14:37 example
```

---

### Post by hameeda on 2010-03-21
can u pls help me out
make: *** No rule to make target `menuconfig'.  Stop.
what does this error show???

---

### Post by howefield on 2010-03-21
> **hameeda said:**
> can u pls help me out
make: *** No rule to make target `menuconfig'.  Stop.
what does this error show???

Is this supposed to have something to do with this thread ?

If not, post your question in its own thread, and give more information as to what led to the error.

---

### Post by goustaroubunta on 2010-03-21
thanks. 
the mkdir thing doesn't work =\
stef@stef-desktop:~$ cd /media/Whatup
stef@stef-desktop:/media/Whatup$ sudo mkdir
mkdir: missing operand
Try `mkdir --help' for more information.
stef@stef-desktop:/media/Whatup$

i successfully change permissions on home subfolders but not on the mounted hard drive...

---

### Post by Helkaluin on 2010-03-21
The mkdir command, literally, 'makes' a 'directory'. It reports 'missing operand' now because you need to specify the name for the directory you want to make. So if you want to make a directory named 'example' under the directory you are now:
```
mkdir example
```
As howefield suggested,
```
sudo mkdir example
```
will make a directory named 'example' under the current working directory with root privileges - therefore the directory made will have root permissions.

---

### Post by goustaroubunta on 2010-03-21
hey thanks guys. i think i got it..

---


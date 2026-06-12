---
title: "Installation problem"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by nns2006 on 2009-08-01
Instructions

    * After downloading open a shell and,  cd to the directory where you downloaded the installer.
    * At the prompt type:  sh ./setup.bin


What does these instructions mean? 
Thanks .

---

### Post by LowSky on 2009-08-01
open  terminal
Applications > Accessories > terminal

at the prompt type: cd *the place you downloaded the file*, for instance

```
cd /home/nns2006/downloads/application
```

then type

```
sh ./setup.bin
```

if that doesn't work try

```
sudo sh ./setup.bin
```

does that help?

---

### Post by SpinningAround on 2009-08-01
^
|
better

---

### Post by nns2006 on 2009-08-01
> **LowSky said:**
> open  terminal
Applications > Accessories > terminal

at the prompt type: cd *the place you downloaded the file*, for instance

```
cd /home/nns2006/downloads/application
```

then type

```
sh ./setup.bin
```

if that doesn't work try

```
sudo sh ./setup.bin
```

does that help?


this what i get


nityanand@nityanand-laptop:~$ cd /home/nityanand/Documents/setup.bin.tar.gz
bash: cd: /home/nityanand/Documents/setup.bin.tar.gz: Not a directory
nityanand@nityanand-laptop:~$ sh ./setup.bin
sh: Can't open ./setup.bin
nityanand@nityanand-laptop:~$ sudo sh ./setup.bin
[sudo] password for nityanand: 
sh: Can't open ./setup.bin
nityanand@nityanand-laptop:~$

---

### Post by LowSky on 2009-08-01
> **nns2006 said:**
> this what i get


nityanand@nityanand-laptop:~$ cd /home/nityanand/Documents/setup.bin.tar.gz
bash: cd: /home/nityanand/Documents/setup.bin.tar.gz: Not a directory
nityanand@nityanand-laptop:~$ sh ./setup.bin
sh: Can't open ./setup.bin
nityanand@nityanand-laptop:~$ sudo sh ./setup.bin
[sudo] password for nityanand: 
sh: Can't open ./setup.bin
nityanand@nityanand-laptop:~$
just to ask what application are you installing?
you got another issue, you need to untar that file first, here we go
```

cd /home/nityanand/Documents

tar -zxvf setup.bin.tar.gz

cd /home/nityanand/Documents/setup.bin

sh ./setup.bin or sudo sh ./setup.bin
```

---

### Post by nns2006 on 2009-08-01
> **LowSky said:**
> just to ask what application are you installing?
you got another issue, you need to untar that file first, here we go
```

cd /home/nityanand/Documents

tar -zxvf setup.bin.tar.gz

cd /home/nityanand/Documents/setup.bin

sh ./setup.bin or sudo sh ./setup.bin
```


I am trying to install pdf-studio. On their website they have given the above posted instruction, which i am finding hard to follow.

nityanand@nityanand-laptop:~$ cd /home/nityanand/Documents/setup.bin
bash: cd: /home/nityanand/Documents/setup.bin: Not a directory
nityanand@nityanand-laptop:~$ sh ./setup.bin
sh: Can't open ./setup.bin
nityanand@nityanand-laptop:~$ sudo sh./setup.bin
[sudo] password for nityanand: 
sudo: sh./setup.bin: command not found
nityanand@nityanand-laptop:~$ 
nityanand@nityanand-laptop:~$

---

### Post by SuaSwe on 2009-08-01
A couple of typos in there!

By "Navigate to the directory" they mean "Go into the directory where the relevant file sits".

It looks like it should be in /home/nityanand/Documents/, so do this in Terminal:

> $ cd /home/nityanand/Documents/

Once the bash prompt says:

> nityanand@nityanand-laptop:~/nityanand/Documents$

We know you're in the right place. At this point do:

> $ tar -zxvf setup.bin.tar.gz

...then finally type in:

> $ sudo sh ./setup.bin

(Note the exact locations of the spaces!)

---

### Post by SuaSwe on 2009-08-01
NB: If you want to make sure that the file is where you think, you can do an ls whilst in the relevant directory, e.g.:

> First do

$ cd /home/nityanand/Documents/ 

then

$ ls -l

This will output a list of files, hopefully one of them being setup.bin.tar.gz; if you can see the file it means you can then work on it as you are in its directory, so you can then tar it (tar -xvfz setup.bin.tar.gz) then execute (sudo sh ./setup.bin)

---

### Post by nns2006 on 2009-08-01
> **SuaSwe said:**
> A couple of typos in there!

By "Navigate to the directory" they mean "Go into the directory where the relevant file sits".

It looks like it should be in /home/nityanand/Documents/, so do this in Terminal:



Once the bash prompt says:



We know you're in the right place. At this point do:



...then finally type in:



(Note the exact locations of the spaces!)






Thanks a lot. I am able to install it.:popcorn:

---

### Post by SuaSwe on 2009-08-02
Awesome!

---


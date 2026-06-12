---
title: "how to install .bin files"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-04-11
i have a small problem (like always it seems)  i have downloaded a game called graal online that can be played with linux

the only problem is that its in a .bin file and i have no idea how to install it

the file is called  graal4setup.bin  and its on my desktop

so i went to the terminal and typed cd~/Desktop    changed it to desk top then tried  chmod graal4setup.bin 

and thats where my problem begins cuz it wont install the file

---

### Post by coolbrook on 2010-04-11
Perhaps post #3 will help

[http://ohioloco.ubuntuforums.org/showthread.php?p=5708604](http://ohioloco.ubuntuforums.org/showthread.php?p=5708604)

---

### Post by stilling on 2010-04-11
you forgot to make it executable 
sudo chmod +x file.bin
./file.bin



hope this helps

---

### Post by pyrofreak99 on 2010-04-11
ok so is it like this

sudo chmod +x graal2setup.bin  ./graal4setup.bin


cuz when i do that it says it cant detect the file at all

---

### Post by sisco311 on 2010-04-11
Type 
```
bash
```
type a space, drag the file in the terminal & press Enter.

---

### Post by theozzlives on 2010-04-11
> **pyrofreak99 said:**
> ok so is it like this

sudo chmod +x graal2setup.bin  ./graal4setup.bin


cuz when i do that it says it cant detect the file at all

try:
```
sudo chmod +x graal4setup.bin && ./graal4setup.bin
```
I noticed you have two different filenames, is that how you're typing into the terminal?

---


---
title: "Bash Script To Make Symlinks of Hidden Directories?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by N0WH3R3K1D on 2010-05-02
Hi, I'm new to bash scripting. I wanted to know is there a way to make symlinks of the hidden directories in my home folder and move these symlinks into a special folder?

What I want is this:

/home/user/.hiddenfolder

to 

/home/user/Preferences/hiddenfolder

Why I would like this? Because in Mac OS X, application settings are stored in a folder like this:

/users/user/Library

I find it rather clean and organized, although I know the consequences of damaging the files in the process of editing these files. Anyways I've been trying to do the same thing under a sandbox situation in different folders, but to no avail. Again, how would I be able to do this?

---

### Post by Primefalcon on 2010-05-02
```
ln -s .hiddenfolder /wherever/you/want/your/yourSymLink/to/be
```

---

### Post by xumuk37 on 2010-05-02
ln -s <destination> <linkname>

Oops! I didn't refresh the page xD)

---

### Post by arsenic23 on 2010-05-02
My bash scripting is pretty messy, but this will do what you want if you run if from your home directory.:


```
for a in `ls -a | grep ^[.]`; do ln -s `pwd`'/'$a Preferences/`echo $a |sed 's/^[.]//'`; done
```

edit:
______________
BTW, I'm assuming the ~/Preferences folder already exists.

---

### Post by N0WH3R3K1D on 2010-05-02
> **arsenic23 said:**
> My bash scripting is pretty messy, but this will do what you want if you run if from your home directory.:


```
for a in `ls -a | grep ^[.]`; do ln -s `pwd`'/'$a Preferences/`echo $a |sed 's/^[.]//'`; done
```

edit:
______________
BTW, I'm assuming the ~/Preferences folder already exists.
Thank you for your code; however, I would like only symlinks to the hidden directories in the home directory into the Preferences directory and not the hidden files in the home directory. Is there a way to do this?

---

### Post by arsenic23 on 2010-05-04
> **N0WH3R3K1D said:**
> Thank you for your code; however, I would like only symlinks to the hidden directories in the home directory into the Preferences directory and not the hidden files in the home directory. Is there a way to do this?

Oh sure, sorry.  Here you go:

```
#!/bin/bash

for a in `find . -maxdepth 1 -mindepth 1 -type d -name ".*"`; 
do b=`echo $a | sed 's|^[.][/]||'`; 
ln -s `pwd`'/'$b Preferences/`echo $b |sed 's/^[.]//'`;
done
```

Again, it's a little messy, but it works.  [COLOR="Silver"](I'm obviously no hand at bash.)[/COLOR]

---

### Post by Drenriza on 2010-05-04
> **N0WH3R3K1D said:**
> Hi, I'm new to bash scripting. I wanted to know is there a way to make symlinks of the hidden directories in my home folder and move these symlinks into a special folder?
 
What I want is this:
 
/home/user/.hiddenfolder
 
to 
 
/home/user/Preferences/hiddenfolder
 
```
ln -s /home/user/Preferences/hiddenfolder /home/user/.hiddenfolder 
```

---

### Post by N0WH3R3K1D on 2010-05-04
> **arsenic23 said:**
> Oh sure, sorry.  Here you go:

```
#!/bin/bash

for a in `find . -maxdepth 1 -mindepth 1 -type d -name ".*"`; 
do b=`echo $a | sed 's|^[.][/]||'`; 
ln -s `pwd`'/'$b Preferences/`echo $b |sed 's/^[.]//'`;
done
```

Again, it's a little messy, but it works.  [COLOR="Silver"](I'm obviously no hand at bash.)[/COLOR]
Thanks a lot! It works perfectly!
Gotta learn to do that myself.

---


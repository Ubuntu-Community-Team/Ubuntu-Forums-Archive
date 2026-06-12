---
title: "whats with the source code"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Aitashan on 2011-07-28
i am trying to install ardour 2 on Ubuntu 11.04 
how to compile the code??

---

### Post by cjazz on 2011-07-28
Well, you've provided no information about what steps you've taken, what difficulties you've encountered or what error messages you may have gotten, so it's hard to offer any suggestions. Have you installed the build-essential package as foillows?
```
sudo apt-get install build-essential
```

More complete instructions for compiling from source are [here.]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by Aitashan on 2011-07-28
yea i did it now what it is updated to the newest version and i m completley new to this whole compiling thing so any help would be appreciated

---

### Post by CatKiller on 2011-07-28
The latest version of ardour is in the repositories. There's no need to compile from source.

---

### Post by cjazz on 2011-07-28
Please read the link I added to the post above. Usually there are instructions included in the package (in a readme file, for example), but generally the routine involves navigating to the source folder and doing

```
./configure
make
sudo make install
```

---

### Post by Aitashan on 2011-07-28
which repository is that

---

### Post by Aitashan on 2011-07-28
> **cjazz said:**
> Please read the link I added to the post above. Usually there are instructions included in the package (in a readme file, for example), but generally the routine involves navigating to the source folder and doing

```
./configure
make
sudo make install
```


thank you for your time but compiling=**** so i just find an alternative instead

---

### Post by lisati on 2011-07-28
> **Aitashan said:**
> which repository is that

If it's in the "standard" repository, you need not worry which one. Places to check from the GUI are Synaptic Package manager and the Ubuntu Software Center. If you're doing it from the terminal, you can use a command like:
```
sudo apt-get install {proram-name}
```

---

### Post by Aitashan on 2011-07-28
> **lisati said:**
> If it's in the "standard" repository, you need not worry which one. Places to check from the GUI are Synaptic Package manager and the Ubuntu Software Center. If you're doing it from the terminal, you can use a command like:
```
sudo apt-get install {proram-name}
```

terminal says unable to locate????

---

### Post by mastablasta on 2011-07-28
the try finding the package in synaptic or software center. searchf or ardour and see what you get.

---

### Post by Aitashan on 2011-07-28
> **mastablasta said:**
> the try finding the package in synaptic or software center. searchf or ardour and see what you get.

now what is synpatic

---


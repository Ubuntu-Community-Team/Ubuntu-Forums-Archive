---
title: "I have a folder full of Wine files, how do I get Wine working?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by BobPOW on 2010-09-21
Hi everybody!  I put the Wine tar file on my Ubuntu computer and extracted it.  Now I have a folder with more Wine files in it.  How do I get Wine working on Ubuntu?

---

### Post by 3rdalbum on 2010-09-21
On Linux we don't download software from the web, instead we use a package manager.

Use Ubuntu Software Center to download and install Wine, and then you can run SOME Windows programs (around 20% of Windows programs).

---

### Post by CanadianPenguin on 2010-09-21
You downloaded source code - which is a bunch of files containing the code for the program that haven't been compiled into an executable file yet. Since you're an absolute beginner it's probably the last way you should install something.

Open the terminal and type:
```
sudo apt-get install wine
```

It will automatically download and install Wine for you.

---

### Post by CFury on 2010-09-22
> **CanadianPenguin said:**
> You downloaded source code - which is a bunch of files containing the code for the program that haven't been compiled into an executable file yet. Since you're an absolute beginner it's probably the last way you should install something.

Open the terminal and type:
```
sudo apt-get install wine
```It will automatically download and install Wine for you.

However wouldn't you agree it's something all *nix users should learn?  Simply put it's really just a few commands in the shell.

---

### Post by 3rdalbum on 2010-09-22
> **CFury said:**
> However wouldn't you agree it's something all *nix users should learn?  Simply put it's really just a few commands in the shell.

Yes, but they need to learn the package manager first. And they can learn the first time they actually need to compile something.

---


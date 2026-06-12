---
title: "fresh install and programs"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-02-14
Hi , i just wonder if there is a way to backup the programs i have installed now , and move them to a fresh install of an other distribution of ubuntu, instead of install them one by one again ... so is there ?:D

---

### Post by bruno9779 on 2010-02-14
there is.
```

dpkg --set-selections > my-pkg-list
```

this will create the file my-pkg-list

to import said file:

```
dpkg --set-selections < my-pkg-list

dselect
```

---

### Post by nick_goodfate on 2010-02-14
I suppose "--set-selections" will be the folders where i ve installed programs ...? if i replace the root folder of fresh install with a backup, its ok ? even if the backup is from 9.10 and fresh install is 10.04 ? following this : [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311) for example is fine for what i want ?

---

### Post by lovinglinux on 2010-02-14
> **nick_goodfate said:**
> I suppose "--set-selections" will be the folders where i ve installed programs ...? if i replace the root folder of fresh install with a backup, its ok ? even if the backup is from 9.10 and fresh install is 10.04 ? following this : [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311) for example is fine for what i want ?

No, that's not a backup. What the *dpkg --set-selections* does is create a list of installed and removed applications, so you can install on another machine or after a clean install using a simple command. It basically creates something like a batch installation command. The installation will be automated, but you will still need Internet connection. The advantage is that you don't need to keep track of which applications you have installed and can install them all at once, with a simple command.

If you prefer you can use my Firefox extension called [UMarks](https://addons.mozilla.org/en-US/firefox/addon/13153) to do that. It creates lists of installed packages that you can export and then import into the other machine and install the applications. It is basically a gui for dpkg --set-selections.

---

### Post by Mustard on 2010-02-14
Wow, thats a really useful command.

So what is the command to install the entire list?

---

### Post by lovinglinux on 2010-02-14
> **Mustard said:**
> Wow, thats a really useful command.

So what is the command to install the entire list?

To replicate your packages selection on another machine (or restore it if re-installing), you can type: 

```
dpkg --get-selections > ~/my-packages 
```

move the file "my-packages" to the other machine, and there type 

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

---


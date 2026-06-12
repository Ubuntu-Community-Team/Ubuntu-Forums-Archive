---
title: "Cannot Change Directories (cd not working?)"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-05
When I type DIR, I can see a list of folders (directories) and Desktop is listed.

But I cannot change the current directory TO that directory.

I tried

cd -/Desktop
cd Desktop
cd /Desktop
cd ./Desktop

none work and the response is.....

bash: cd: -/: invalid option
cd: usage: cd [-L|-P] [dir]

---

### Post by RobsterUK on 2009-02-05
It should be:

cd[space]Desktop

if that directory exists. That doesn't work?

---

### Post by ibutho on 2009-02-05
Try
```
cd ~/Desktop
```

---

### Post by blackgr on 2009-02-05
> **mistypotato said:**
> When I type DIR, I can see a list of folders (directories) and Desktop is listed.

But I cannot change the current directory TO that directory.

I tried

cd **-/**Desktop
cd Desktop
cd /Desktop
cd ./Desktop

none work and the response is.....

bash: cd: -/: invalid option
cd: usage: cd [-L|-P] [dir]

You are using the wrong symbol. you have to use **~** not **-**

---

### Post by Flimm on 2009-02-05
The correct command is
```
cd Desktop
```
Assuming of course you're currently in your home directory. (Use pwd to make sure)
```
cd -/Desktop
```
cd will think that -/Desktop is a command line option, and say so.
```
cd .Desktop
```
cd will think that the directory you want to change to is ".Desktop", which doesn't exist.
```
cd /Desktop
```
cd thinks you want to change to a directory named Desktop in the root, which of course doesn't exist. The directory you want is /home/user/Desktop
```
cd ./Desktop
```
This should work.

---


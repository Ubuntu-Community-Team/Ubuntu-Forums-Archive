---
title: "Installation Error"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Hunter Morrell on 2010-06-04
Just now, I was trying to install a program through the command line by running "sudo apt-get install". Yet, instead of going through like it normally does, it returned what seems to be some kind of error message:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```I tried to run the command that it gave me and this popped up:

```
dpkg: status database area is locked by another process
```I have tried to figure out what happened, but I'm stumped. Any help would be greatly appreciated

---

### Post by lrcaballero on 2010-06-04
Try this:

System
Administrator
Synaptic Package manager
Edit
Fix Broken Packages

Good Luck

---

### Post by wojox on 2010-06-04
> dpkg: status database area is locked by another process

Do you have any other mangers open? Software Center or Synaptic...

---

### Post by Hunter Morrell on 2010-06-04
I tried to open Synaptic and I got another error message:

```
Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. 
```

The thing is, I don't have anything else up and running except for FF and Konversation.

---

### Post by Hunter Morrell on 2010-06-04
I just restarted the computer and I'm getting the same message. Help? Please?

---

### Post by Hunter Morrell on 2010-06-05
Bump. Help? Please?

---

### Post by Hunter Morrell on 2010-06-05
Or not. I fixed it! Go me :p

---

### Post by wojox on 2010-06-05
Mark it as solved and post what you did to fix it for future people.

---


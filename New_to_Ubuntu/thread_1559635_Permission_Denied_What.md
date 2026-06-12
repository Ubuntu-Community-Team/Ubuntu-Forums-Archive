---
title: "Permission Denied? What?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by demonic_bunny on 2010-08-23
I'm trying to install some custom brushes in the GIMP and Im getting an error saying Error moving files: permission denied.

I'm the admin, shouldn't I be able to move a couple of files into a folder? What gives?

---

### Post by AlphaLexman on 2010-08-23
Where are you moving / copying the brushes to?

You should put them in 
```
~/.gimp-2.6/brushes
```

---

### Post by gordintoronto on 2010-08-24
You're not "root," so you need to take extra steps to manipulate some folders.  For example, from Accessories/Terminal: gksudo nautilus 
gives you the ability to completely mess up your installation.

---

### Post by uRock on 2010-08-24
> **gordintoronto said:**
> gksudo nautilus gives you the ability to completely mess up your installation.
Very well put.

---

### Post by 3rdalbum on 2010-08-24
> **demonic_bunny said:**
> I'm trying to install some custom brushes in the GIMP and Im getting an error saying Error moving files: permission denied.

I'm the admin, shouldn't I be able to move a couple of files into a folder? What gives?

On modern operating systems, your normal user account cannot modify files and folders outside their home directory. this is done for security reasons. You can gain access to the administrator 'root' account temporarily by running a program such as a file browser using the "gksudo" command.

So, the command "gksudo nautilus" will open a file browser without restrictions. Be careful, and remember to use your ordinary user account whenever you don't need root powers.

---

### Post by demonic_bunny on 2010-09-02
thanks guys, appreciate it. Reasoning makes sense, just used to Windows / Mac OS where you dont usually need the extra step xD

---

### Post by Ocxic on 2010-09-02
Really, you never needed a to type your password when installing applications, or changing certain settings in preferences on your MAC?

---


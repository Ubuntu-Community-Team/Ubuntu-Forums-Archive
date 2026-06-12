---
title: "saving changes made in conf files"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by spab on 2009-08-31
:confused:i just installed ubuntu and i need to fix my sound but i cant find out how to save changes made in conf files using the terminal.
thx a lot

---

### Post by drs305 on 2009-08-31
The files are probably owned by root. In this case, you must edit them while having admin rights. This means opening your editor with either "sudo" for terminal operations or "gksudo" for graphical apps such as gedit.
Example:
gksudo gedit /path/filename
sudo nano /path/filename

See this link for a reference on the subject:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by cranecreek on 2009-08-31
This is how i do it:

```
sudo -i
```Then cd to where the file is:

```
vi filename
```edit the conf, when finished:

```
:wq
```your favorite editor may differ

---


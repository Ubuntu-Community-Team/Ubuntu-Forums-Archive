---
title: "echo command attempting to mount"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by casebash on 2010-04-02
Hi, I am getting what appears to be a strange error message:

chris@comp2008:/mnt$ echo A=`echo ~chris/.gvfs/*/DCIM` | bash
mount: only root can do that
[COLOR=#888888]
Does anyone know why I am getting this?
[/COLOR]

---

### Post by jrdm on 2010-04-02
try put a "sudo" before that

---

### Post by @rizz on 2010-04-02
When do you get this error?

What are u attempting to do?

---

### Post by casebash on 2010-04-04
I had a script that wasn't working and I was trying to debug it. I am basically trying to write a script that stores a pattern into a variable. I have no idea why it is attempting to mount.

---

### Post by ibuclaw on 2010-04-05
> **casebash said:**
> Hi, I am getting what appears to be a strange error message:

chris@comp2008:/mnt$ echo A=`echo ~chris/.gvfs/*/DCIM` | bash
mount: only root can do that
[COLOR=#888888]
Does anyone know why I am getting this?
[/COLOR]

So you are trying to run:
```
echo A=`echo ~chris/.gvfs/*/DCIM` | bash
```
:-k

Not sure why you have a pipe to bash, that won't do anything useful...

---


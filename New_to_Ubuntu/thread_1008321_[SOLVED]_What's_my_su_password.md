---
title: "[SOLVED] What's my su password?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by DeathByChocolate on 2008-12-11
I know... it sounds crazy asking for a password, but I feel I missed something.  

I created a user password on installation, which works.  

I am able to install some software packages with sudo.  

I do not remember anything about a super user password.  Is there a default value on a new installation?

I want to create a new directory under /usr, and Ubuntu won't let me.

---

### Post by glennric on 2008-12-11
su is disabled by default in Ubuntu.  See [log-in-as-root]("http://ubuntuforums.org/showthread.php?t=716201").

To make a directory in /usr type 
```
sudo mkdir /usr/dirname
```

---

### Post by Elfy on 2008-12-11
Use sudo instead

```
sudo mkdir /usr/name
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by howefield on 2008-12-11
Use your user account password to gain sudo rights.

---

### Post by ajcham on 2008-12-11
There is no su password - everything is done with sudo.

To create the directory you can either use the command:
```
sudo mkdir /usr/DIRECTORY_NAME
```
or open a file manager as root, eg.:
```
gksu nautilus
```

---

### Post by Michael.Godawski on 2008-12-11
For some more info about root and sudo checkout this:


[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[/LIST]

it is for the Education Focus Team, mentioned in the sticky, not yet finished but I am doing some progress.

---

### Post by DeathByChocolate on 2008-12-11
Thanks... best answer!

---

### Post by Duck2006 on 2008-12-11
sudo su

Don't for get to exit after your done.

---


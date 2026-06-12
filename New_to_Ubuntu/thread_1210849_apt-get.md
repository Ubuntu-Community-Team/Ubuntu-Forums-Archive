---
title: "apt-get ?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by garyed on 2009-07-11
Is there a command to see or search to see if a program can be installed with apt-get? Not only would it help to know its there but also to know the correct spelling too.

---

### Post by ubudog on 2009-07-12
Yes.  apt-cache search "name of program"


Hope that helps.

---

### Post by earthpigg on 2009-07-12
apt-get and aptitude are both command line package managers for ubuntu.

some things one does better than the other.

in this case, aptitude is better:

```
sudo aptitude search firefox
```

will show you every package with 'firefox' in the name.

you can install the packages it shows you with apt-get.

---

### Post by texens on 2009-07-12
```
sudo apt-cache search *
```

where * = name of the prog,
it'll give you a list of all the packages that contain the term *. 

Alter:
you could install Synaptic - graphical package manager.

```
sudo apt-get install synaptic
```

---

### Post by garyed on 2009-07-12
Thanks to all for all the excellent help that's just what i was looking for.

---

### Post by CatKiller on 2009-07-12
> **garyed said:**
> Not only would it help to know its there but also to know the correct spelling too.

Don't forget that you can use Tab-completion with package names, the same as you would for filenames or commands.

---

### Post by GCoffee on 2009-07-12
As far as im aware synaptic is installed by default anyway?

---

### Post by northern lights on 2009-07-12
> **GCoffee said:**
> As far as im aware synaptic is installed by default anyway?Yes.

> **earthpigg said:**
> ```
sudo aptitude search firefox
```
As an aside, while not at all harmful to be run with, *aptitude search* does not require root priviliges.



Another option is checking online: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Reading:

[aptitude manpage]("http://nixdoc.net/man-pages/Linux/aptitude.1.html")

[apt-get manpage]("http://nixdoc.net/man-pages/Linux/man8/apt-get.8.html")

[apt-cache manpage]("http://nixdoc.net/man-pages/Linux/man8/apt-cache.8.html")

---

### Post by luckydeveloper on 2009-07-12
do this

sudo apt-cache search packagename


you will get a list of possible matches.. from there, you can choose and install a package.

sudo apt-get install packagename

---


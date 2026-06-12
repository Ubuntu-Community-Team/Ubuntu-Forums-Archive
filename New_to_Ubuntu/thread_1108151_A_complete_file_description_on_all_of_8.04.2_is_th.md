---
title: "A complete file description on all of 8.04.2 is there?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-03-27
Is there like a sheet for every file, process, and programs that are inside the live cd iso image 8.04.2

---

### Post by yeats on 2009-03-29
Depending on what it is you're trying to do, there are several information sources (not just one location that I know of) with descriptions, etc.  One is Synaptic (or Adept on KDE), which will have brief descriptions for each program (some more helpful than others).  There is built-in documentation for most terminal programs by doing:

```
man *program name*
```

or

```
info *program name*
```

Then there are the web sites for each individual program that would have documentation there.

What are you trying to learn?

---

### Post by louieb on 2009-03-29
Thousands of pages but its all here. [http://packages.ubuntu.com/](http://packages.ubuntu.com/):confused:

---

### Post by t0p on 2009-03-29
The nearest to a solution that I can think of is this:

Go to **Synaptic Package Manager**: System > Administration > Synaptic

On the left side of the Synaptic window is a button marked **Status**.  Click it.

Now select the option **Installed** from the list above the Status button

The resultant list will list all the packages that are installed on your Ubuntu system.  Unfortunately this does not entirely answer your question.  There are some software packages that are on the CD but which are not installed automatically.  I think **build-essential** is such a package.

---

### Post by yeats on 2009-03-29
The command line version of this would be:

```
dpkg -l > pkgs.list
```

then you can view the pkgs.list file which will show all currently installed and previously installed pkgs.  Do

```
man dpkg
```

for details.

Come to think of it, dpkg -l includes snippets of description as well.

---


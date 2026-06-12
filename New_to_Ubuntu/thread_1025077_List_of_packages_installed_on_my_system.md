---
title: "List of packages installed on my system"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by CoreyB. on 2008-12-29
Is there a way to see a list of the packages I have installed on Ubuntu 8.10?  I want to see if all of the packages I use are 64-bit compatible.

Also, I just want the list of packages I installed, AFTER the OS, not the apps included with the OS.

Thanks!

---

### Post by mkvnmtr on 2008-12-29
Yes there is a command to list everything on your computer but I have lost the command. Someone will post it up or I will find it shortly. If you have used add/remove and Synaptic to install then everything you have installed will be compatible with the system you are running.

OK here it is. It was on my desktop hiding under something else.
dpkg --get-selections | grep -v deinstall > ubuntu-files

---

### Post by howefield on 2008-12-29
```
dpkg --get-selections > installed-software
```

There are most likely a dozen ways of getting it :) That's one which will put a text file in your home folder.

---

### Post by mkvnmtr on 2008-12-29
His might be better try them both, I will.

---

### Post by CoreyB. on 2008-12-29
Thanks for the help, but this lists ALL of the packages.  Is there a way to just show the packages that don't come with the OS?

---

### Post by pdtpatrick on 2008-12-29
what exactly you want again? you want a list of the packages installed or a list of packages available to your os?

---

### Post by howefield on 2008-12-29
Hmm, unless you have cleaned the cache you'll have them in /var/cache/apt/archive/

I'm just having a look to see if that includes installed debs from sources other than synaptic.

---

### Post by TomasJancik on 2008-12-29
if you use only aptitude to install software, you could get list of installed packages by cat-it and grep-ing its logs... maybe it will be also possible to do this also with synaptics logs

---

### Post by linux_tech on 2008-12-29
```
dpkg -l
```
 also returns a list of installed packages

---

### Post by linux_tech on 2008-12-29
To see all packages which are packaged with Ubuntu by release-

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by linux_tech on 2008-12-29
> **CoreyB. said:**
> Is there a way to just show the packages that don't come with the OS?

You can run dpkg -l right after you install ubuntu and then save the output as text file. After you install some new packages, you can run dpkg -l again, save the output to a text file.  Then you can use diff to compare the 2 files and output the difference to a file.
[http://www.opengroup.org/onlinepubs/009695399/utilities/diff.html](http://www.opengroup.org/onlinepubs/009695399/utilities/diff.html)

---


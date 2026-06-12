---
title: "Tar.gz automatic compiler?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by sodra on 2009-12-11
Hi
Im tired of going to the terminal and Compiling Tar.gz files, is there a program that compiles a tar.gz file on its own?

---

### Post by abeisgreat on 2009-12-11
> **sodra said:**
> Hi
Im tired of going to the terminal and Compiling Tar.gz files, is there a program that compiles a tar.gz file on its own?

You should just be able to right-click on the item and click Create Archive, or something like that.

---

### Post by sodra on 2009-12-11
> **abeisgreat said:**
> You should just be able to right-click on the item and click Create Archive, or something like that.
I dont see one, what program do I add to see it?

---

### Post by abeisgreat on 2009-12-11
> **sodra said:**
> I dont see one, what program do I add to see it?

Hmm, I thought it was there by default. They may have changed it in Karmic, sorry.

---

### Post by sodra on 2009-12-11
Nothing? No Program? No Script? Darn
But can you post instructions on how to Install tar.gz files?
Its confusing @_@

---

### Post by MelDJ on 2009-12-11
a tar.gz is like a zip file. hence, you will have to compile it yourself. to install software from tar.gz see: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")
you might be interested in alien. it is available in the repos. it converts packages from one type to another. but not tar.gz's though

---

### Post by lykwydchykyn on 2009-12-11
> **sodra said:**
> Nothing? No Program? No Script? Darn
But can you post instructions on how to Install tar.gz files?
Its confusing @_@

.tar.gz files are just compressed file archives.  They can contain anything.  There is no one way to install them.

If it's sourcecode, then you may want to have a look at checkinstall, which will compile it to a .deb file and install using the package manger (makes uninstall or upgrading much easier).

Basically, just untar the file, go to that directory, and type "checkinstall".


If it's not sourcecode, you just have to read the README or INSTALL document included in the file to see what needs to be done.

---

### Post by 3rdalbum on 2009-12-12
Checkinstall does not compile software.

There is no software to automatically compile anytging you throw at it. I am surprised you compile much - the Ubuntu repository has lots of software, plus there are PPAs.

---

### Post by Primefalcon on 2009-12-12
> **3rdalbum said:**
> Checkinstall does not compile software.

There is no software to automatically compile anytging you throw at it. I am surprised you compile much - the Ubuntu repository has lots of software, plus there are PPAs.
I think your getting your words messed up, compiling is turning text into a program binary another words it's a part of making a program.

by what you said I think what you want to to compress files into a smaller file is that right? if so just right click and compress

---

### Post by lykwydchykyn on 2009-12-12
> **3rdalbum said:**
> Checkinstall does not compile software.


Umm... really?  Funny, cause I've compiled several dozen pieces of software using checkinstall.

---

### Post by 3rdalbum on 2009-12-12
> **lykwydchykyn said:**
> Umm... really?  Funny, cause I've compiled several dozen pieces of software using checkinstall.

> checkinstall is a program that monitors an installation procedure (such
       as  make install, install.sh ), and creates a standard package for your
       distribution (currently deb, rpm and tgz packages are  supported)  that
       you  can  install through your distribution's package management system
       (dpkg, rpm or installpkg).

       Note that for most useful actions, checkinstall must be run as root.

It runs "sudo make install" for you and puts the resulting files into a Debian package for you. Maybe it runs "make" if you haven't already run it. But it doesn't run ./configure and it doesn't resolve build dependencies, which is the real hassle involved with compiling software.

---

### Post by lykwydchykyn on 2009-12-12
> **3rdalbum said:**
> It runs "sudo make install" for you and puts the resulting files into a Debian package for you. Maybe it runs "make" if you haven't already run it. But it doesn't run ./configure and it doesn't resolve build dependencies, which is the real hassle involved with compiling software.

It does indeed run make for you, which is compiling. make==compiling.

---


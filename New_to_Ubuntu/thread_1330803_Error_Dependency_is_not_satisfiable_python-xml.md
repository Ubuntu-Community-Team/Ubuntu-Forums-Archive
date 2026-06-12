---
title: "Error: Dependency is not satisfiable: python-xml"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by tiagosgd on 2009-11-18
Hello...
I am trying to install easycam (http://blog.jbtheou.fr/?attachment_id=334) but allways appears this error: "Error: Dependency is not satisfiable: python-xml". So I tried to install python-xml... but something is wrong.
thanks

"tiago@tiago-laptop:~$ sudo apt-get install python-xml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-xml is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-xml has no installation candidate"

---

### Post by nathan726 on 2009-11-18
From [https://bugs.launchpad.net/python/+bug/343242]("https://bugs.launchpad.net/python/+bug/343242"):

> It's finally time to remove python-xml. please use the xml modules included in the python core.python-xml was broken and obsolete, so it was deleted from the repositories.
You won't be able to install easycam until the developers fix it. ](*,)

---

### Post by miguelastico on 2010-04-30
any update on this? I am trying to install python-sparqlrwapper but it asks for python-xml; I tried to compile it from the source but it failed...

---

### Post by Se[BBB]e on 2010-04-30
If the package is unstable it might be a shitty idea, but you can download and install it from here:

[http://packages.debian.org/stable/python-xml](http://packages.debian.org/stable/python-xml)

Should solve your problems.

---

### Post by stanz on 2010-10-11
Same here - 
On my Dell Inspiron 1546, integrated webcam...I'm trying Easycam with [these instructions]("http://davestechsupport.com/blog/2009/02/14/installing-webcams-in-ubuntu-the-easy-way/").
We can't install the core package without the xml.
We can't install the xml without python2.6

nathan726 = I would like to know how to do this...?
> please use the xml modules included in the python core. 

Even grabbing the xml from Debian, {using Deb Package Installer}
> Error: Dependency is not satisfiable: python (<< 2.6)
But...python2.6 IS already in 10.04, but DPI can't find it????  Why?
Thanks in advance!

  :confused:

---

### Post by nathan726 on 2010-10-15
> **stanz said:**
> 
> please use the xml modules included in the python core.
nathan726 = I would like to know how to do this...?

Someone would have to reprogram EasyCam so that it uses the python core xml modules instead of python-xml.

---

### Post by Seregwethrin on 2011-05-15
I'm trying to install this easycam.
Easycam is documented here: [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

And the problem mentioned this thread still exists. I want to run my Microsoft vx1000 webcam.

Also I tried with Hardy Universe repository and trying to install python-xml ask for removing dozens of dependencies like KDE.

If anybody has an idea, please mention it.

---


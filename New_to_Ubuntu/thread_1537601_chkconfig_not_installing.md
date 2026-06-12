---
title: "chkconfig not installing"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by sonicx059 on 2010-07-23
I am trying to install chkconfig, and i am getting the error.

error msg
-------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package chkconfig is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package chkconfig has no installation candidate
--------------------------------------------

i am pretty sure i am using the proper command
----------------------------------
sudo apt-get install chkconfig
&
sudo aptitude install chkconfig
----------------------------------------------

Has the name changed in the last two weeks I haven't used it? Also I am running 9.10

---

### Post by matrixblue on 2010-07-23
Make sure you have the universe repository enabled

---

### Post by sonicx059 on 2010-08-06
> **matrixblue said:**
> Make sure you have the universe repository enabled

I had to find out how to check that. Once I found out i forgot about this thread. Sorry, but that did the trick.

---


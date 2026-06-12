---
title: "Lethe"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by emdr on 2009-11-10
I am extremely new to Ubuntu (about 2 weeks).  I am a systems support in a library.  We are interested in using Ubuntu on our public computers as a cost saving measure.
Saying this, it will also be necessary to "lock down" the computers to protect them from any changes from our initial setup.  I've been looking at Lethe, which seems to solve our problem.  My problem is that I can't get it to install.  The last message I received was "the package lethe needs to reinstalled but I can't find an archive for it".  I've also got a message saying "cannot access archive: No such file or directory".
The version I've been installing is lethe 0.1.3.
I hope I've given the correct information to figure a solution. I apologize in advance but while I've worked on computers for about 10 years, the open source software is extremely new to me.

---

### Post by laidback on 2009-11-10
There seems to be an Ubuntu version here:-

[http://sourceforge.net/projects/lethe/files/](http://sourceforge.net/projects/lethe/files/)

v0.2

Cannot help further I'm afraid.

---

### Post by ranch hand on 2009-11-10
I think the easiest way to do that is to create another user with limited permissions in System>Administration>Users and Groups so that only folks with the right password can get to anything that would change the setup.

---

### Post by lavinog on 2009-11-10
+1 for limited permissions.

There have been a couple of users claiming that they are switching library computers to ubuntu.

Freezing the partion could be a bad idea since the system may need to update certain files.
/etc is where all of the system settings are.  You can make a backup of this folder, and occasionally check the md5s of the files if you are really paranoid about it.

I am assuming that the computers will only need to have a web browser, and not all the other applications.
You may want to try setting up a minimal install.

---

### Post by emdr on 2009-11-10
Thanks for the suggestions so far.  I will look into these.

---


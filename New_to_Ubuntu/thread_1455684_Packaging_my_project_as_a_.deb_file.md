---
title: "Packaging my project as a .deb file"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by kapmsd on 2010-04-16
Hi guys!
I have nearly completed our project.
My team developed using C,shell scripts and qt.

I would like to know how to package it as a .deb file??
Also during installation,i want it to check for the existence of few packages in the system.If they are not there,i want it to download them using apt.

How to go about doing this?

Thanks a lot for your inputs in advance.

---

### Post by Jon Monreal on 2010-04-16
Take a look at [this]("http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/") page. [This]("http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/") might also help.

---

### Post by sandyd on 2010-04-16
> **kapmsd said:**
> Hi guys!
I have nearly completed our project.
My team developed using C,shell scripts and qt.

I would like to know how to package it as a .deb file??
Also during installation,i want it to check for the existence of few packages in the system.If they are not there,i want it to download them using apt.

How to go about doing this?

Thanks a lot for your inputs in advance.

 you can use checkinstall or dh_make. you can also try using giftwrap, which does all the steps of dh_make for you graphically. if you simply want the deb, and have no use for the source debs (you need to create one to upload to launchpad ppas), just use checkinstall. However, if you wanting to make a deb, you will either need a makefile, or add the compiling instructions to debian/rules. If you want a sample first package of your app , ill gladly create the first deb for you. once the deb is set up (for the first time) it is relatively easy for you to update it.

---

### Post by kapmsd on 2010-04-16
Thanks a lot guys!

---


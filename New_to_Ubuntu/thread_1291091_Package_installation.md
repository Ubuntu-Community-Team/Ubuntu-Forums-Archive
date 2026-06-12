---
title: "Package installation"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-10-14
Hi guys..
I just wanted to know that how does a package installation take place...as in..when we install a s/w on windows..the files are extracted to the destination that we specify
What all does it do in ubuntu

---

### Post by mike1821 on 2009-10-14
Hi,

This is a good article to understand the basics of packaging system

[http://www.ibm.com/developerworks/linux/library/l-debpkg.html]("http://www.ibm.com/developerworks/linux/library/l-debpkg.html")

---

### Post by vipulkelkar on 2009-10-15
Thanks..it was a nice article !

---

### Post by mocoloco on 2009-10-15
If you open synaptic and select an installed package you can look at it's properties and see the installed files, which will show you where they are.
You'll notice files of the same type are put together, so documentation in /usr/share/doc, libraries in /usr/lib, executables together, icons together, desktop menu files together, and so on. This is contrary to the Windows way of having all (or most) of the files for one app in one location (although between shared dlls and the registry that's not so true most of the time anymore).  Both ways have pluses and minues, but for example that's why on Linux it's easy to have all the executables in the path since they're all in /bin, /sbin, or /usr/bin, while on Windows only some basic programs are in the path.

---


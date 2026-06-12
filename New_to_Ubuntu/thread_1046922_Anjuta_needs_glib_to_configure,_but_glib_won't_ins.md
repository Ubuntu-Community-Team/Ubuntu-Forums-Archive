---
title: "Anjuta needs glib to configure, but glib won't install"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-21
I am just starting to learn C++. I am "Hello world!" new. So, as well as learning the language, I am learning to use the IDE. Anjuta said it needed glib to configure. I got glib from the source Anjuta gave. I have the file glib-2.18.4.tar.gz on my Desktop. Here is my install attempt.
```
daniel@GLENDA:~/Desktop$ sudo aptitude install glib-2.18.4.tar.gz
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "glib-2.18.4.tar.gz"
Couldn't find any package whose name or description matched "glib-2.18.4.tar.gz"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```
Any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by adult swim on 2009-01-21
thats not how you would install .tar.gz files.  glib is in the repositories though so you can run this from a terminal to get it ```
sudo apt-get install libglib2.0-dev
```

---

### Post by Lostin60's on 2009-01-21
> **adult swim said:**
> thats not how you would install .tar.gz files.  glib is in the repositories though so you can run this from a terminal to get it ```
sudo apt-get install libglib2.0-dev
```

Thank you. I kind of thought it was because of the file types.  I looked in the repositories, but I was looking for glib, not libglib. Should be no problem now.
[COLOR="White"]aa[/COLOR]

---

### Post by m@n0j on 2009-08-15
Thank you ... Anjuta no longer shows glib error after i installed thru the terminal..

---

### Post by Marinozai on 2010-11-07
> **Lostin60's said:**
> Thank you. I kind of thought it was because of the file types.  I looked in the repositories, but I was looking for glib, not libglib. Should be no problem now.
[COLOR=White]aa[/COLOR]
Thank you! That worked!

---


---
title: "How to install softwares without having internet connection??"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-13
Hi everyone,I am using ubuntu 9.04 in my home with internet connection,The same version is used by friend in his home but without internet connection,He asked me is there any way install the software without internet connection?I know some packages will require additional dependencies,can i download the packages with dependencies and give it to my friend??Will it work..!If so pls say me the way..

---

### Post by mthalis on 2009-08-13
[http://ubuntuforums.org/showthread.php?t=34113](http://ubuntuforums.org/showthread.php?t=34113)

[http://www.planetoss.com/detail.php?id=13](http://www.planetoss.com/detail.php?id=13)

---

### Post by karthick87 on 2009-08-13
Ok i have read the posts,Can you say me how to install all the deb repostories that are with in a folder..

---

### Post by 3rdalbum on 2009-08-13
> **getyourkarthick said:**
> Ok i have read the posts,Can you say me how to install all the deb repostories that are with in a folder..

Double-click on them.

Start with the outermost dependencies, and finish with the main package itself.

Alternatively, open the terminal to the folder and type:

```
sudo dpkg -i *
```

---

### Post by karthick87 on 2009-08-13
Thanks a lot

---

### Post by colau on 2009-08-16
> **getyourkarthick said:**
> Hi everyone,I am using ubuntu 9.04 in my home with internet connection,The same version is used by friend in his home but without internet connection,He asked me is there any way install the software without internet connection?I know some packages will require additional dependencies,can i download the packages with dependencies and give it to my friend??Will it work..!If so pls say me the way..
Installing packages without internet connection is difficult!

---

### Post by sandyd on 2009-08-16
Perhaps, AptOnCD?
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
unless im mistaken, its included with a default install of ubuntu

---

### Post by colau on 2009-08-17
> **carlee said:**
> Perhaps, AptOnCD?
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
unless im mistaken, its included with a default install of ubuntu
I think,it's not installed by default.

---

### Post by lkraemer on 2009-08-18
Try this:
[http://keryxproject.org/](http://keryxproject.org/)

You only need an Internet connection and a USB Memory Stick to download
what you need, then take it to the computer that doesn't have an Internet
connection and install.

SIU to the Rescue!
(Southern Illinois University)

lkraemer

---

### Post by Cheesemill on 2009-08-18
+1 for Keryx

---


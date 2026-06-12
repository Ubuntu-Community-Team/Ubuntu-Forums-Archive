---
title: "autoremove programs"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by sandyd on 2009-10-10
Is there a way to clear the "The following packages were automatically installed and are no longer required:
"
in apt and aptitude?

i need those programs (i actually checked), but its kinda stupid to autoremove, then install them again.

---

### Post by NightwishFan on 2009-10-10
I thought that only cleaned up unneeded dependent packages, such as libvlc if you do not have VLC installed.

---

### Post by sandyd on 2009-10-10
it does, but aparenly a lot of programs that i needed got into there...

---

### Post by slakkie on 2009-10-10
If you have the list, you could do:

aptitude install all the packages

or.. but I have never used this:

aptitude unmarkauto all the packages 

and then all the packages should be marked as manually installed so it will not remove them.

---

### Post by ikt on 2009-10-10
> **carlee said:**
> it does, but aparenly a lot of programs that i needed got into there...

> [http://ubuntuforums.org/showthread.php?t=996053](http://ubuntuforums.org/showthread.php?t=996053)

autoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed. 

So I don't think you need those packages.

---

### Post by sandyd on 2009-10-10
thanks!
worked perfectly.

---


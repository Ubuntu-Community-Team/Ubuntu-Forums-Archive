---
title: "package name"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-01-18
the code ```
$ sudo aptitude install mplayer-nogui
```
gives : 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  libfaac0{a} liblzo2-2{a} libmp3lame0{a} libsvga1{a} libxvidcore4{a} mplayer-nogui 
0 packages upgraded, 6 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,871kB/2,997kB of archives. After unpacking 6,889kB will be used.
Do you want to continue? [Y/n/?]
perfectly normal i know ! But what {a} means, next to the name of some of the packages ? :-k

---

### Post by synapsys on 2010-01-18
> **nick_goodfate said:**
> After unpacking 6,889kB will be used.

Seems the {a} means that it's some kind of archive.....

---

### Post by EssexEagle on 2010-01-18
> **nick_goodfate said:**
> But what {a} means, next to the name of some of the packages ? :-k

I thought it meant automatically installed (as dependencies)?  i.e. Although you didn't ask for those package(s), the one(s) you did ask for require these extra packages in order to work, so Ubuntu helpfully installs them automatically for you :-)

---

### Post by synapsys on 2010-01-18
> **EssexEagle said:**
> I thought it meant automatically installed (as dependencies)?  i.e. Although you didn't ask for those package(s), the one(s) you did ask for require these extra packages in order to work, so Ubuntu helpfully installs them automatically for you :-)

I've installed lots of packages with dependencies. I've never seen an {a} following the name....

---

### Post by EssexEagle on 2010-01-18
> **synapsys said:**
> I've installed lots of packages with dependencies. I've never seen an {a} following the name....

But were you using aptitude or apt-get?

I may well be completely wrong, of course.

---

### Post by synapsys on 2010-01-18
> **EssexEagle said:**
> But were you using aptitude or apt-get?

I may well be completely wrong, of course.

You may have a point there....

---


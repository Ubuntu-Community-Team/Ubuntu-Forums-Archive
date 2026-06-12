---
title: "Where can I get the Sun Java 5 packages?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by hul on 2009-12-27
I would like to install the Sun Java 5 plugins, not version 6--I'm currently having trouble getting the Facebook uploader to work in Firefox 3.5.6 and I read a post on this forum where a user fixed the problem by installing Java 5 instead of Java 6.  However, when I run
> sudo apt-get install sun-java5-jre sun-java5-plugin
the packages aren't found.

Is there a place where I can find these?  Do I need to download the JRE v5.0 and Java plugin v1.1.3_005 that are on [this page](http://java.sun.com/products/archive/)?

---

### Post by rtyb on 2009-12-27
I believe the only thing you need to write in the terminal is
```
sudo apt-get install sun-java5-jre
```Anyways, better do
```
sudo apt-get install ubuntu-restricted-extras
```That installs everything, flash, java, (mp3, avi, mkv, mp4, etc..)

:popcorn:

PS: I'm not having problems with the photo uploader...

---

### Post by hul on 2009-12-27
Sorry, I should have mentioned that I tried that.  I get this error:

> Package sun-java5-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jre has no installation candidate

Is there a way to diagnose why I might be having trouble with the uploader?  I posted a question [here](http://ubuntuforums.org/showthread.php?t=1365242) asking about the problem but haven't found a solution to it.  If it's a network issue wouldn't it be affecting my roommates as well?

---


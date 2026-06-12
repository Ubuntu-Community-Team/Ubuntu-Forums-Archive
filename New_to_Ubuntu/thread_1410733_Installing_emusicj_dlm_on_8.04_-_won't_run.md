---
title: "Installing emusicj dlm on 8.04 - won't run"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by mynot on 2010-02-19
I've downloaded and unpacked emusicj into a subdir of my home dir. When I run it nothing happens, and from the command line I get -pages of runtime errors:
tony@TONY-PC:~/Downloads/emusicj-linux$ ./emusicj
Using emusicj at /home/tony/Downloads/emusicj-linux
Exception in thread "main" java.util.NoSuchElementException
   at java.util.AbstractList$2.next(libgcj.so.81)
   at com.google.inject.InjectorImpl.getParametersInjectors(InjectorImpl.java:512)
etc
etc.
Don't know why. Last time I installed it worked without a hitch.
Thanks
Tony

---

### Post by Brandon Williams on 2010-02-20
The error that lists libgcj suggests to me that you aren't running Sun's java. I don't know whether the version of java you're using supports emusicj. I know that Sun's jre handles it just fine. You might want to install sun-java6-jre and try with that version of java.

---

### Post by mynot on 2010-02-22
Thanks very much. Solved several other problems as well. I thouhgt Java came with Ubuntu.
Tony

---


---
title: "dpkg-shlibdeps: warning: Can't extract name and version from library nam"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by bistro on 2010-11-02
Hi

when I try to execute the command:

make-googleearth-package --force

I receive a long list of errors, starting with

mv: cannot stat `libssl.so.0.9.8': No such file or directory

then many lines of:

dpkg-shlibdeps: warning: Can't extract name and version from library name `[xxx].so'

I have seen this issue described when I searched other threads, but the solution was to install googleearth from medibuntu but, unfortunately, it doesn't appear in the medibuntu list for maverick.

I have the following file in my system:
/lib/libssl.so.0.9.8

I do not understand the problem here, many thnaks for any advice.

Regards

---

### Post by owlcroft on 2010-11-29
I have the exact same problem on a fresh, clean Maverick install.  Three weeks now--any help from anybody?

---

### Post by FrodeA on 2010-12-01
Hi!

I had the same problem. Found a solution on Webupd8, see option 2 "Manual installation" - worked like a tee...:D

Here is the link: [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html)

---


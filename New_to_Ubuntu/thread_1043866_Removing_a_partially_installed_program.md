---
title: "Removing a partially installed program"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by jacatone on 2009-01-18
This has got to be the biggest problem with Linux. You try installing some program through a terminal and it hangs and in so doing prevents you from downloading any further programs. The following is an example:

"Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]" 

And of coarse when I try using Synaptic I get: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried removing it as root. Reinstalling it. Nothing seems to work. Does anyone know how to get rid of this? Thanks.

---

### Post by PurposeOfReason on 2009-01-18
Have you run this as root?
dpkg --configure -a

---

### Post by gettinoriginal on 2009-01-18
There is nothing to remove, it never installed.  But the error message tells you that you need to go to terminal and run:
```
gksudo dpkg --configure -a
```  to correct things.
Then you should be able to go to Synaptic to install it.  :P

---


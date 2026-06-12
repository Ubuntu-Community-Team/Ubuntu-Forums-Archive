---
title: "Java docs and/or update problem"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Jonwenger on 2010-01-01
If I try to update my system (32 bit) with the update manager, after a while, it shows this error:```
 E: sun-java6-doc: subprocess installed post-installation script returned error exit status 1
```:confused:The appearing package problem also says that the package "sun-java6-doc 6-15-1" failed to install or upgrade.
Is that a problem? How can i manually update the package and if I do not what are the consequences?

---

### Post by hoppipolla on 2010-01-01
Pop into Synaptic and see if the package is broken :)

If it is it will come up in the "Broken" filter, and you can fix it by simply telling it to :)

---

### Post by Jonwenger on 2010-01-01
It does not appear in the Broken section of the Synaptics Package Manager.

---

### Post by MelDJ on 2010-01-01
try sudo dpkg --configure -a

---

### Post by Jonwenger on 2010-01-01
This is what i get: ```
Setting up sun-java6-doc (6-15-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```

---

### Post by MelDJ on 2010-01-02
try doing what it says by downloading and installing the zip file

---

### Post by Jonwenger on 2010-01-02
Now I get this error: ```
user@user-laptop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-15-1) ...
[/tmp/jdk-6u10-docs.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /tmp/jdk-6u10-docs.zip or
        /tmp/jdk-6u10-docs.zip.zip, and cannot find /tmp/jdk-6u10-docs.zip.ZIP, period.
dpkg: error processing sun-java6-doc (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 sun-java6-doc
user@user-laptop:~$ 



```

---

### Post by Jonwenger on 2010-01-02
I found the problem. I did sudo dpkg --configure -a before the package was fully downloaded. Thank you.

---


---
title: "Can't reinstall Java"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Nilafhiosagam on 2009-11-12
I had a problem with controlling flash videos from sites such as youtube and tried to uninstall Sun Java 6 browser plugin before reinstalling it again using the Ubuntu Software Centre. The uninstall worked fine but when I try to install it I get an error message saying:

 "Can not install 'sun-java6-plugin' (E:Unable to correct problems, you have held broken packages.)"

Flash videos still seem to play fine but I can't use a Firefox plugin that I need for college anymore. Does anyone know how to fix it?

I'm using Ubuntu 9.10 btw

---

### Post by Nilafhiosagam on 2009-11-12
I'm new to Ubuntu and tried to use the terminal to install it just there

I used: sudo apt-get install sun-java6-plugin

and got an error: The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

---

### Post by QIII on 2009-11-12
You can use

```
sudo apt-get install sun-java6-bin
```

first to install the file needed.

HOWEVER:  Canonical has decided to move away from Sun Java in favor of OpenJDK.  IMHO, that is a bad move.  Sun's Java is the real deal.  I develop Java applications, and I can't ensure that testing on a machine with OpenJDK really gives me a good handle on what clients running Sun Java will encounter.

The version of Sun Java available in the Karmic repos is Update 15, which is known to have significant security issues.  Sun's Java is up to Update 17.

I would recommend following the tutorial given here for installing the "real deal":


[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Nilafhiosagam on 2009-11-12
Thanks. I got it working again by reinstalling java6.bin and then the plugin. Looking at other threads, I think the version of java I had wasn't properly updated when I upgraded to 9.10.

---


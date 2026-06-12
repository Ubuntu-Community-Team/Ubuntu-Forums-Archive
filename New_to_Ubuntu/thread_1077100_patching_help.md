---
title: "patching help"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by KuroYoma on 2009-02-22
I am running a 2.6.28.6 kernel and would like to apply the 2.6.28.7 patch and compile it.  I have downloaded the patch and when I use this command:
```
 patch -p1 > patch-2.6.28.7 
```  I get a a message the says:
```
|diff --git a/Documentation/filesystems/sysfs-pci.txt b/Documentation/filesystems/sysfs-pci.txt
|index 68ef488..de99749 100644
|--- a/Documentation/filesystems/sysfs-pci.txt
|+++ b/Documentation/filesystems/sysfs-pci.txt
--------------------------
File to patch: 

```

I don't know what to type after file to patch.   I have tried everything and it says file doesnt exits then asks if I want to skip.

---

### Post by Xiong Chiamiov on 2009-02-27
It's been a while since I've used patch, but I believe you need to send the patch as input, rather than output.  You may also have to adjust the -p1 parameter, since that changes something to do with the levels of directories.

Take a read through [this](http://www.kegel.com/academy/opensource.html).

---


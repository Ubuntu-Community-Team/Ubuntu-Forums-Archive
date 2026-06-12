---
title: "compiz fusion error"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by rookalius on 2009-01-26
Hello, i trying to install compiz fusion on ubuntu and get this report: 
ubuntu@ubuntu-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

how I can install this on my ubuntu?

---

### Post by rookalius on 2009-01-26
Hello, i trying to install compiz fusion on ubuntu and get this report:
ubuntu@ubuntu-desktop:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x76 to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

how I can install this on my ubuntu?

---

### Post by Izek on 2009-01-26
What's the output of

```
lspci | grep VGA
```

---

### Post by rookalius on 2009-01-26
04:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)

---

### Post by Izek on 2009-01-26
Read this thread, maybe it will help.

[http://forum.compiz-fusion.org/showthread.php?t=8666](http://forum.compiz-fusion.org/showthread.php?t=8666)

---


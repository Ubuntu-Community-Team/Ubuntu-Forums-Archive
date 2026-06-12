---
title: "[SOLVED] Trying to build Vba-m!"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by boglio on 2008-12-03
I'm trying to build Vba-m(VisualBoyAdvance gba emulator) but I'm stuck at an error that I really don't understand. 

----
$make
Linking CXX executable gvbam
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [gvbam] Error 1
make[1]: *** [CMakeFiles/gvbam.dir/all] Error 2
make: *** [all] Error 2
----

I really don't know what this means and what "-lGL" is. 

BTW, I'm running ubuntu 8.10 x86_64

---

### Post by linux_tech on 2008-12-03
I havn't installed vba-m, I am just working off the error

"/usr/bin/ld: cannot find -lGL"  is a link error

what is output of
```
X -version
```
```
file /usr/lib/libGL.*
``` (check symbolic links)

You may want to try creating a new link 

1st rename /usr/lib/libGL.so to something else    
```
mv /usr/lib/libGL.so /usr/lib/libGL.old 
```

```
cd /usr/lib/
```
from output you may try something similar to:
```
sudo ln -s libGL.so.173.14.12 libGL.so
```
to make a symbolic link

---

### Post by linux_tech on 2008-12-03
oops duplicate

---

### Post by boglio on 2008-12-03
Yup that is spot on, thanks for the response.

---


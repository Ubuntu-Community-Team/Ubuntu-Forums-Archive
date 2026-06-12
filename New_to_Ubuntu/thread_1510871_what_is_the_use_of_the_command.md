---
title: "what is the use of the command?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by mkarthik90 on 2010-06-16
HI ,
       *Can anyone tell me what is the command sudo ldconfig refer to ? Is there any necessity in using that command after installation of packages .*

---

### Post by 3rdalbum on 2010-06-16
As far as I know, you shouldn't need it after installing a package from the repositories. However you may need it after installing a library manually (compiling it from source).

It forces the system to reindex the shared libraries on the system. If you get an error message that a particular library can't be loaded, and you know that you've got that libary, then sudo ldconfig may help.

The 'ldconfig' man page has more information:

```
man ldconfig
```

---


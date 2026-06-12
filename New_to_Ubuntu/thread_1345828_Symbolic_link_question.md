---
title: "Symbolic link question"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by maxxerific on 2009-12-04
hellooo!
   
  so - i have an afp server on a ubuntu 9.10 box. I have three drives sharing various types of media. To avoid clutter in the OSX finder, rather than share each partition individually, i've made a folder to share on the afp server called "MediaServe" and made symbolic links to each mounted partition inside. The folder "MediaServe" is in the /home/~ directory 

Everything works great except: 

when i check in a client OSX computer how much space is available, it only shows how much space is available in the root filesystem (and not the combined space shared across these extra paritions that MedisServe links to. 




Any ways to fix this?

---

### Post by blazemore on 2009-12-08
Instead of a symbolic link, you could use folder bindings in fstab
The format is like this:
```
/path/of/source     /path/of/destination    none    bind   0 0
```

---


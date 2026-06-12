---
title: "sopcast dependency?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by stevek123 on 2010-05-18
I am trying to install sopcast using the debian pkg. It gives me a missing dependency error msg ...Error: Dependency is not satisfiable: ia32-libs|lib32stdc++5  I HAVE installed the libstdc++5 library - twice - but this does not seem to satisfy the requirement. I am not sure how to get this in the /usr/lib32 ??? What do I do?

---

### Post by ankspo71 on 2010-05-19
Hi,
Here is a link that might help solve the dependency problem.
[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/)
Hope that helps

---

### Post by stevek123 on 2010-05-19
yes - thanks. I already found a similar thread and installed libstdc++5. That does not satisfy my dependency. Looking for how to get _lib32stdc++5_... Or maybe how to change the config of sopcast to use the /usr/lib instead of usr/lib32???

---

### Post by Perfect Storm on 2010-05-19
libstdc++5 32-bit on 64-bit ubuntu. The easist way is to use getlibs;

Install getlibs:
```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
```

Install libstdc++5
```

wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb
getlibs -i libstdc++5_3.3.6-17ubuntu1_i386.deb
```


More info about getlibs;
```
getlibs -h
```

---

### Post by tmx84 on 2010-05-19
Just use the repository which you will find out the below link and installation instructions.. 

[http://code.google.com/p/sopcast-player/wiki/Installation](http://code.google.com/p/sopcast-player/wiki/Installation)

Should go through just fine, only thing you might need to do is add the medibuntu repository as well, which it has instructions for that too...

---

### Post by lastbalance on 2010-09-10
> **tmx84 said:**
> Just use the repository which you will find out the below link and installation instructions.. 

[http://code.google.com/p/sopcast-player/wiki/Installation](http://code.google.com/p/sopcast-player/wiki/Installation)

Should go through just fine, only thing you might need to do is add the medibuntu repository as well, which it has instructions for that too...

thank you

---


---
title: "Error when installing gettext"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Free4Eternity on 2009-01-09
Hey guys! As you can probably see, I am new. So a greeting to everyone. Well, I am trying to install GKrellM, and apparently, it is dependent on gettext, so I am trying to install that. 

```
./conf
``` was fine, but when I tried to do ```
 make 
```, it ended after quite a while with 

```

In function 'open',
    inlined from 'msgdomain_list_print' at write-catalog.c:223:
/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [write-catalog.lo] Error 1
make[4]: Leaving directory `/home/joyce/Desktop/gettext-0.17/gettext-tools/src'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/joyce/Desktop/gettext-0.17/gettext-tools/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/joyce/Desktop/gettext-0.17/gettext-tools'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/joyce/Desktop/gettext-0.17/gettext-tools'
make: *** [all-recursive] Error 1

```

any idea how to fix that?

---

### Post by zvacet on 2009-01-10
Did you tried to install from synaptic?

---

### Post by Free4Eternity on 2009-01-11
Is that with the command with app-get?

---

### Post by zvacet on 2009-01-11
Go to the** system>admin>synaptic** and there in **search box** type **gettext**.Synaptic will find package and you will see white box on the left side of the package.Click on it and install package.Other solution is from terminal

```
sudo apt-get install gettext
```

---

### Post by snova on 2009-01-11
> **zvacet said:**
> Go to the** system>admin>synaptic** and there in **search box** type **gettext**.Synaptic will find package and you will see white box on the left side of the package.Click on it and install package.Other solution is from terminal

```
sudo apt-get install gettext
```

GKrellM can also be installed in this manner. No need to compile from source.

---

### Post by Free4Eternity on 2009-01-18
a belated thanks.

---

### Post by ziphyre on 2009-02-14
Hello,

I have the same error also but I do not want to install it from apt. In fact I don't want to install it all (with all its dependencies like apache, php etc)

I just need to compile it, and give the gettext.so to another machine.

Any help?

---

### Post by reqq on 2010-01-11
got same error, problem is im not connected to internet and hence cant use synaptic.. and i need gettext for network manager.. ohhh the irony !

---

### Post by nanobacon on 2010-02-05
Sorry to resurrect, but had same issue and changing this line in gettext-tools/src/write-catalog.c :

fd = open (filename, O_WRONLY | O_CREAT);

To this:

fd = open (filename, O_WRONLY | O_CREAT, S_IRUSR|S_IWUSR);

Solved it for me.

---

### Post by parsinimous on 2010-02-09
That sure looks like an answer I've needed. how'd you end up with it?

---


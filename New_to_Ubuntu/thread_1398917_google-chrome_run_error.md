---
title: "google-chrome run error"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by sazan on 2010-02-05
Hi

I have been currently in CentOS 5.3 and have installed google-chrome-beta_current_i386.rpm successfully. 

But I am having following error while trying to run it -

```


[root@localhost tmp]# google-chrome 
/usr/bin/google-chrome: error while loading shared libraries: libexpat.so.1: cannot open shared object file: No such file or directory


```

I checked for expat and got following list -

```

[root@localhost tmp]# rpm -qa | grep expat
compat-expat1-1.95.8-4
expat-1.95.8-8.3.el5_4.2
expat-devel-1.95.8-8.3.el5_4.2


```

Does anyone know about the solution? Did some search on it, but no use.

---

### Post by arochester on 2010-02-05
It might be more appropriate to ask CentOS Forum...

[http://www.centos.org/modules/newbb/index.php?cat=8](http://www.centos.org/modules/newbb/index.php?cat=8)

---


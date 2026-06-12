---
title: "Psiphon"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by anandamide on 2009-10-07
Hallo chaps

I'm wanting to install psiphon, just out of curiosity :-).

Unfortunately, the install instructions make no sense...

> ***** psiphon *****
$ cd ..
$ cd psiphon-src-1.3
$ bakefile -DBUILD_VERSION="\"1.3\"" -f gnu psiphon.bkl

$ make
$ cp release/psiphon .
$ cp release/libpsiphonHandler.so .
$ cd ..
$ cp appWeb-2.1.0/bin/libsslModule.so psiphon-src-1.3
$ cp appWeb-2.1.0/bin/libopenSslModule.so psiphon-src-1.3

$ cd psiphon-src-1.3

$ sudo ./psiphon

*If you receive a message "psiphon error while loading shared libraries: libwx_gtk2_adv-2.8.so.0: cannot open shared object file: No such file or directory"
add the following line:
/usr/local/lib
to the /etc/ld.so.conf  and run
$ sudo ldconfig


---

### Post by trigsenior on 2009-10-07
Have you tried running the commands ?

It probally comes in a .tar or tar.gz

So extract it.

```
tar -xvvf psiphon.tar.gz 
```

Then Change Directory 

```
 cd psiphon-src-1.3 
```


Generate the make file 

```
bakefile -DBUILD_VERSION="\"1.3\"" -f gnu psiphon.bkl
```

Make - Complie the program to get a executable

```
 make 
```

cp ( copy ) move various files around 

```
$ cp release/psiphon 
$ cp release/libpsiphonHandler.so 

```


Move up a directory 

```

cd ..

```


cp ( copy ) move various files around 
```

$ cp appWeb-2.1.0/bin/libsslModule.so psiphon-src-1.3
$ cp appWeb-2.1.0/bin/libopenSslModule.so psiphon-src-1.3

```

And finaly as root ( sudo  ) 

```
sudo ./psiphon 
```

Follow the commands , Paste any errors you get.

---

### Post by anandamide on 2009-10-08
Thanks for the reply :-)

I had tried running the commands, but the terminal just stared at me blankly (well, more blankly than terminals usually do).

I was fooled by the **psiphon** bit at the top and had missed a load of previous stuff which my cat command had splurged out. 

The instructions are not too decipherable; I'll post a more user-friendly version once I've got it up and running.

Cheers :-)

---


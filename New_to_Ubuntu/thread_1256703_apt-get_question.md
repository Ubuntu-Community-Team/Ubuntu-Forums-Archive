---
title: "apt-get question"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by memecs on 2009-09-02
Hello everyone,
I was installing  a bunch of c++ external libraries (qt, lapack, blas, etc...) and it seems like the names follow a certain pattern: lib*<libraryname>*-dev is it correct?

Most of the libraries come with a documentation lib*<libraryname>*-doc, how can i read it?

How do i find the directory where they have been installed?

thanks a lot

---

### Post by scorp123 on 2009-09-03
> **memecs said:**
>  Most of the libraries come with a documentation Documentation files should be in this directory:
**/usr/share/doc**

Let's take *zenity* as example (because I know it's installed per default; so we both should have that). The documentation would be here:
**/usr/share/doc/zenity**

As is usual with those documentation files they are compressed into *.gz files: ```
> ls -al
total 112
drwxr-xr-x    2 root root  4096 2009-08-25 17:18 .
drwxr-xr-x 1599 root root 69632 2009-09-02 21:47 ..
-rw-r--r--    1 root root    70 2008-12-11 03:24 AUTHORS
-rw-r--r--    1 root root  3427 2009-04-20 09:15 changelog.Debian.gz
-rw-r--r--    1 root root  1029 2009-04-20 09:15 copyright
-rw-r--r--    1 root root  9358 2009-03-16 23:13 NEWS.gz
-rw-r--r--    1 root root   445 2008-12-11 03:24 README
-rw-r--r--    1 root root  3054 2008-12-11 03:24 THANKS.gz
-rw-r--r--    1 root root   768 2008-12-11 03:24 TODO
```

So let's suppose you want to read the docs for that ... You could use your file manager "Nautilus" and browse into that directory above and simply read the contents of the *.gz files by clicking on them. That should open those files in "Archive Manager" so you can see what's inside. One more click and you'd have whatever is inside in front of you.

The terminal way:
Most of those *.gz files are compressed text files anyway, so it's not really necessary or useful to unpack them. You can read them right away in their compressed state with the ***zcat*** command:
```
zcat /usr/share/doc/zenity/NEWS.gz | more
```

I hope this was helpful?

---

### Post by memecs on 2009-09-03
yes it was really helpfull.

thanks a lot again for you help

---


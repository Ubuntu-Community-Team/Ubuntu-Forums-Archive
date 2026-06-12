---
title: "[SOLVED] vncviewer and libstdc++2.10-glibc2.2"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by ezramorris on 2008-05-02
&#65279;hi, I'm trying to run vncviewer, but since i upgraded to hardy, i get this error: 

vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Everywhere seems to suggest running 
```
sudo apt-get install libstdc++2.10-glibc2.2
```
but this gives the error:

Package libstdc++2.10-glibc2.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++2.10-glibc2.2 has no installation candidate

I think this is because a new version of libstdc++ is in hardy.

Any way to solve this?

Thanks.

---

### Post by hhhanxf on 2008-05-05
adding following source to your source list:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

and reload the source list

then do

sudo apt-get install libstdc++2.10-glibc2.2

After install, I recommend you remove the source from your list.

---

### Post by ezramorris on 2008-05-06
> **hhhanxf said:**
> adding following source to your source list:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

and reload the source list

then do

sudo apt-get install libstdc++2.10-glibc2.2

After install, I recommend you remove the source from your list.

Thanks, I just installed it straight from packages.ubuntu.com .

---

### Post by hhhanxf on 2008-05-06
Great, that is a better solution.

---

### Post by SaturnusDJ on 2009-02-24
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
2009-02-21
Remove feisty.


Now what?

---

### Post by ezramorris on 2009-02-24
> **SaturnusDJ said:**
> [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
2009-02-21
Remove feisty.


Now what?

Dunno, on a recent fresh install of intrepid I just installed the xtightvncviewer package and it works fine.

---

### Post by DataSpy on 2009-11-10
I was trying to get realvnc to work and had the same problem, it took me about an hour to fix :(

you can get the package @ [http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download](http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download)

hope that helps someone :)

---

### Post by charding on 2010-08-21
> **DataSpy said:**
> I was trying to get realvnc to work and had the same problem, it took me about an hour to fix :(

you can get the package @ [http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download](http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download)

hope that helps someone :)

Doing the above helped me run vncviewer! Thanks!

---


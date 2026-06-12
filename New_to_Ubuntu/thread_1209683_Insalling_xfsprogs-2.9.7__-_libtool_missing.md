---
title: "Insalling xfsprogs-2.9.7  - libtool missing"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by arajapandi on 2009-07-10
I tried to install xfsprogs-2.9.7 in my ubuntu ... 

```
test: 1: /usr/bin: unexpected operator
test: 1: /usr/bin: unexpected operator
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for gmake... no
checking for make... /usr/bin/make
checking for glibtool... no
checking for libtool... no
```So i installed libtools... when i type "whereis libtool"  i got the below result
```
libtool: /usr/local/bin/libtool
```but after installing libtool, xfsprogs-2.9.7 result is same "checking for libtool... no" 

can anybody help me to install xfsprogs-2.9.7 ?

---

### Post by unutbu on 2009-07-10
In Intrepid, it appears there is a package for xfsprogs version 2.9.8-1:
```

% apt-cache show xfsprogs
 
Package: xfsprogs
Priority: optional
Section: admin
Installed-Size: 3188
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Nathan Scott <nathans@debian.org>
Architecture: i386
Version: 2.9.8-1

```

Is there a reason for compiling the older version 2.9.7?

---

### Post by arajapandi on 2009-07-10
Hi Unutbu,

Thanks for your fast reply...

i didn't check/know the package is already available in apt. my friend gave the files and i tried to install it :( . 

Now i installed using apt-get install xfsprogs.. thank you

---


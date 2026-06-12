---
title: "synaptic package manager: where do the downloaded packages go?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by mrwicked on 2010-09-12
hi! i wanted to know, where do the packages go after getting downloaded from synaptic? is it possible to change the default directry?
thanx in advance!1;)

---

### Post by Jazzy_Jeff on 2010-09-12
This may be of some help:

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by ronnielsen1 on 2010-09-12
>  where do the packages go after getting downloaded from synaptic?

The debs are located at /var/cache/apt/archives

> is it possible to change the default directry?
I don't think so but I could be wrong

---

### Post by hhlp on 2010-09-12
Synaptic is a fontend for apt. To change the apt-get download location look here.

[http://ubuntuforums.org/showpost.php?p=3125012&postcount=3]("http://ubuntuforums.org/showpost.php?p=3125012&postcount=3")

find the package in /var/cache/apt

---

### Post by jre6 on 2010-09-12
No, you cannot change the directory. The packages are unlike Windows programs which can be installed in any location.

The packages do not get into any central location after installation. They are sent into /usr, /lib, /etc as per the instructions provided in the packages.

---

### Post by mrwicked on 2010-09-12
thanks!! found the packages....
stored a copy of them in another dirctory...

---


---
title: "rebuilding a package with a patch?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by rcallan on 2010-06-13
Hi,

I am having an issue getting ICA client to work in the Terminal Server Client (tsclient).  I found a patch which fixes the issue but i don't know how to install it.

I am on Ubuntu 10.04

The patch and explanation of the issue is here: 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=439089](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=439089)

All the way at the bottom, Bob Hauck says to dump it in debian/patches directory but i don't know where that is.  any help would be appreciated.  thanks.

---

### Post by bodhi.zazen on 2010-06-13
There is a direct link to the patch on your bug report.

Do you know how to download and patch source code ? I can not tell from your post if you just need the patch, or if you need full instructions on how to download the source, patch the source, and then build a .deb

---

### Post by rcallan on 2010-06-13
I have downloaded the patch, i just dont know how to install it.  i found a few other links saying the tsclient needs to be rebuilt and apparently the patch needs to be dumped into the debian\patches directory.

---

### Post by bodhi.zazen on 2010-06-13
I do not know about the tsclient package, take a look here :

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

That page goes through the basics of packaging ...

There is a section on how to use a patch.

Normally I patch directly, but I am not certain how to do that with the patch you have.

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by rcallan on 2010-06-14
ok thanks for your help.  I'll take a look at that page

---


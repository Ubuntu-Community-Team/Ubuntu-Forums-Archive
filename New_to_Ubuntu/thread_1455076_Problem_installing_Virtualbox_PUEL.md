---
title: "Problem installing Virtualbox PUEL"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by summersource on 2010-04-15
After a bit of Googling I soon realized that VB(OSE)did not support UBS so I followed this link to download and install (PUEL)  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads). 
First let me say that I did uninstall (OSE) before attempting to download (PUEL) I am running Ubuntu 10.9 as my host OS and
I am getting this Error: Wrong architecture 'amd64 and with i386.
 What do I need to add or do to get this installed?

---

### Post by e4uforums on 2010-04-15
This sounds like a package and OS architecture mismatch.  The package you download and the OS have be the same architecture - they both need to be 32 bit (i386) or 64 bit (amd64).

---

### Post by summersource on 2010-04-15
> **e4uforums said:**
> This sounds like a package and OS architecture mismatch.  The package you download and the OS have be the same architecture - they both need to be 32 bit (i386) or 64 bit (amd64).

I'm on 32 bit and it will not install i386

---

### Post by e4uforums on 2010-04-15
If you are on 32bit Ubuntu, then you need to download a 32bit package to install.  Or, you could install 64bit Ubuntu and use a 64 bit package.  Just be sure the package architecture and OS architecture match.

---

### Post by summersource on 2010-04-15
> **e4uforums said:**
> If you are on 32bit Ubuntu, then you need to download a 32bit package to install.  Or, you could install 64bit Ubuntu and use a 64 bit package.  Just be sure the package architecture and OS architecture match.


I am on 32bit and was unable to install i386 however it turns out that I had some remaining files from OSE that needed to be removed. Everything seems to be working fine now thanks.

---

### Post by e4uforums on 2010-04-15
Glad it's working!    :P

---


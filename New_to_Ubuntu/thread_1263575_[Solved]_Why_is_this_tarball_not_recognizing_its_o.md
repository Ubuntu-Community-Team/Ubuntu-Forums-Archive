---
title: "[Solved] Why is this tarball not recognizing its own dependancy is installed?"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Tmatherne on 2009-09-11
Hi all, me again.  
 
Due to time constraints I am stuck at work unable to connect my netbook to the internet, however, I have a few tarballs that I am trying to install from a USB.  One of these is libgcrypt 1.4.4.  It has libgpg-error as a dependancy.  I downloaded a tarball for that as well, and installed it.  If I ask terminal to locate libgpg-error, it is found, so no problems there.
 
Now move forward and try to install libgcrypt 1.4.4.  I run the commands from the page I downloaded from in terminal:
 
```
laptop:~/libgcrypt-1.4.4$ ./configure --prefix=/usr &&
>make
```
 
It runs through some basics, then returns:
 
```
configure: error: libgpg-error is needed.

```
 
Am I just missing something obvious?
 
Thanks for the help. 
 
Tommie

---

### Post by 3rdalbum on 2009-09-11
When you are compiling software, you need the development headers as well as the runtime ones. You can tell what's a development headers package, because the name ends in "-dev".

So, install the "libgpg-error-dev" package too.

---

### Post by perce on 2009-09-11
If you don't have a particular reason for wanting version 1.4.4, there is version 1.4.1 in the repository

---

### Post by Tmatherne on 2009-09-13
3rdalbum, thank you.  That fixed it.  Now...how do I edit the title of the thread to reflect the solved status?
 
Tommie

---

### Post by Michael.Godawski on 2009-09-13
> **Tmatherne said:**
> 3rdalbum, thank you.  That fixed it.  Now...how do I edit the title of the thread to reflect the solved status?
 
Tommie

Just edit the title with "Thread Tools".

---


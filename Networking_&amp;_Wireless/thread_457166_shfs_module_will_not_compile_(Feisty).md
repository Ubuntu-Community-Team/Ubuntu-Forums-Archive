---
title: "shfs module will not compile (Feisty)"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Pollywoggy on 2007-05-28
I got the shfs module to compile in Debian Etch but could not get it to compile in kubuntu Feisty.  This is what I did:

apt-get install shfs-utils shfs-source
module-assistant build shfs
module-assistant install shfs

This worked in Debian, but the "build" part failed in Feisty:


dh_clean                                                                   &#8593;
 &#9474; make -C Linux-2.6 clean                                                    &#9646;
 &#9474; make[1]: Entering directory `/usr/src/modules/shfs/Linux-2.6'              &#9618;
 &#9474; rm -rf linux-2.6.20-15-generic linux-2.6.20-15-generic.orig;               &#9618;
 &#9474; rm -f linux-2.6.20-15-generic.diff                                         &#9618;
 &#9474; rm -f *.o *.ko *.mod.c .*o.cmd                                             &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'               &#9618;
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     &#9618;
 &#9474; make[1]: Entering directory `/usr/src/modules/shfs'                        &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; make -C Linux-2.6 clean                                                    &#9618;
 &#9474; make[2]: Entering directory `/usr/src/modules/shfs/Linux-2.6'              &#9618;
 &#9474; rm -rf linux-2.6.20-15-generic linux-2.6.20-15-generic.orig;               &#9618;
 &#9474; rm -f linux-2.6.20-15-generic.diff                                         &#9618;
 &#9474; rm -f *.o *.ko *.mod.c .*o.cmd             

Any ideas what might be wrong?

---

### Post by chili555 on 2007-05-29
What do you see that makes you think something went wrong? I see no errors or warnings so I tend to believe it went perfectly well.

---

### Post by Pollywoggy on 2007-05-29
> **chili555 said:**
> What do you see that makes you think something went wrong? I see no errors or warnings so I tend to believe it went perfectly well.

The word FAILED appears even though it does not appear after I click the button to show the errors.  Also, no module package appears.
A module deb package is the normal result of this process.

---

### Post by Pollywoggy on 2007-05-29
The problem seems to be with the shfs source, but since I have done this in Debian, I will borrow source from my Debian system.

In file included from /usr/src/modules/shfs/Linux-2.6/dcache.c:26:
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:22: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:35: warning: &#8216;kmem_cache_t&#8217; is deprecated
  CC [M]  /usr/src/modules/shfs/Linux-2.6/dir.o
In file included from /usr/src/modules/shfs/Linux-2.6/dir.c:17:
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:76: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:77: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:78: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:79: warning: &#8216;kmem_cache_t&#8217; is deprecated
In file included from /usr/src/modules/shfs/Linux-2.6/dir.c:19:
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:22: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:35: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/shfs/Linux-2.6/dir.c: In function &#8216;shfs_create&#8217;:
/usr/src/modules/shfs/Linux-2.6/dir.c:305: error: &#8216;struct inode&#8217; has no member named &#8216;u&#8217;
/usr/src/modules/shfs/Linux-2.6/dir.c:306: error: &#8216;struct inode&#8217; has no member named &#8216;u&#8217;
make[5]: *** [/usr/src/modules/shfs/Linux-2.6/dir.o] Error 1
make[4]: *** [_module_/usr/src/modules/shfs/Linux-2.6] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'
make[2]: *** [binary-modules] Error 2
make[2]: Leaving directory `/usr/src/modules/shfs'
make[1]: *** [kdist_build] Error 2
make[1]: Leaving directory `/usr/src/modules/shfs'
Module /usr/src/modules/shfs failed.

---

### Post by chili555 on 2007-05-29
Did you successfully compile under Debian with kernel 2.6.20? It is evidently a bug in kernels 2.6.19 and higher. If you are running a fully updated Feisty, you will be running 2.6.20-x.

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg338245.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg338245.html)

---

### Post by Pollywoggy on 2007-05-29
> **chili555 said:**
> Did you successfully compile under Debian with kernel 2.6.20? It is evidently a bug in kernels 2.6.19 and higher. If you are running a fully updated Feisty, you will be running 2.6.20-x.

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg338245.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg338245.html)

The kernel on my Debian system is 2.6.18 and even using the sources from Debian Etch, I did not succeed.  I got the same errors as with the kernel in Feisty.

---

### Post by chili555 on 2007-05-30
Did you consider *sshfs* which is in the repos?

---

### Post by Pollywoggy on 2007-05-30
> **chili555 said:**
> Did you consider *sshfs* which is in the repos?

Yes, I have used sshfs.

---

### Post by Strelock on 2007-07-11
I have exactly the same problem building shfs. Did you find the solution? Or have you submitted bug to ubuntu?
I've found patch here:[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420770](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420770)
applied it to the downloaded source but that didn't make any difference....

---

### Post by EatMorePie on 2007-08-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/shfs/+bug/94942](https://bugs.launchpad.net/ubuntu/+source/shfs/+bug/94942) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Strelock said:**
> I've found patch here:[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420770](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420770)
applied it to the downloaded source but that didn't make any difference....

Perhaps you need to use the -O (capital letter O) option to module-assistant when you rebuild it.  By default module-assistant unpacks the compressed source archive every time, and will overwrite your patch.   If after applying the patch, you say

```
module-assistant -O build shfs 
```

It works fine.

---

### Post by Perkins on 2007-08-22
Reading the error messages, it looks like the kernel structure has changed somewhat, and the module has yet to be updated to match it.

Reading the patch, at a glance it looks like it would fix the problem.

I have never applied a multi-file patch on Linux before.  The patch command does not seem to have any options to cover doing so.  Searching the forums, most of the patches mentioned come with their own scripts to apply them...  

Before I spend the next couple hours cutting and pasting, is there an easier way to do this?  I'm assuming there is.

---

### Post by Hammer2008 on 2007-10-31
Echo this question

---

### Post by Perkins on 2007-10-31
I don't think anyone is paying any attention to this thread anymore.

I found how to apply the patch, but none of the patches I find work with any of the versions of the source I can find.

Supposedly the FUSE module has the ability to mount over SSH.  I haven't had time to try it yet, but you might look at that next as shfs no longer seems to really be supported.

---


---
title: "Writing a system call"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by giriembedded on 2010-05-08
Hi,

 I am new to this forum as well as to the ubuntu linux

 i am using ubuntu 9 with my vmware workstation.

 Now my task is to create a new system call.

 But i am unable to  fine ' /usr/src/linux/arch/i386/kernel/syscall_table.S'

 Please help me to install syscall_table.S

 Thanks and Regards
 Giri

---

### Post by j7%&lt;RmUg on 2010-05-08
Why do you want to create a new syscall in the first place?

---

### Post by giriembedded on 2010-05-08
Hi,

   I am practicing linux.

---

### Post by lisati on 2010-05-08
> **giriembedded said:**
> Hi,

 I am new to this forum as well as to the ubuntu linux

 i am using ubuntu 9 with my vmware workstation.

 Now my task is to create a new system call.

 But i am unable to  fine ' /usr/src/linux/[COLOR="Red"]arch[/COLOR]/i386/kernel/syscall_table.S'

 Please help me to install syscall_table.S

 Thanks and Regards
 Giri

Therein lies the reason you can't find the call where you were looking: this is Ubuntu, not Arch. Which tutorial were you following?

---

### Post by giriembedded on 2010-05-08
Hi,
 i am following the below tutorial


[http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/x50.html](http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/x50.html)

Regards
Giri

---

### Post by 3rdalbum on 2010-05-08
> **giriembedded said:**
> Hi,
 i am following the below tutorial


[http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/x50.html](http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/x50.html)

Regards
Giri

You're following a HOWTO from 2006 - the pace Linux develops at, it's like a person in 2010 trying to follow instructions on how to cook a dinosaur.

There's no longer a /usr/src/linux folder as far as I know. If you install the "linux-headers-generic" package you'll get some useful folders inside /usr/src that are probably applicable to what you want to do.

---

### Post by QLee on 2010-05-08
> **giriembedded said:**
> Hi,
 i am following the below tutorial


[http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/x50.html](http://tldp.org/HOWTO/Implement-Sys-Call-Linux-2.6-i386/x50.html)

Regards
Giri

If you go back a couple of pages in the guide you find "Assume that your linux source base directory is /usr/src/linux". That was supposed to indicate an example ("suppose"), it was assumed that the person following it would adapt to the system they were actually using.

You probably want something like this:/usr/src/linux-headers-2.6.31-21-generic/arch/x86/kernel/.

Edit: and so you don't become confused about the term "arch", in this case it refers to "architecture" not the name of a distro.

---

### Post by gmargo on 2010-05-08
> **giriembedded said:**
> Now my task is to create a new system call.

 But i am unable to  fine ' /usr/src/linux/arch/i386/kernel/syscall_table.S'

 
I believe the file(s) you are looking for are:
arch/x86/kernel/syscall_table_32.S
arch/x86/include/asm/unistd_32.h
arch/x86/include/asm/unistd_64.h
include/linux/syscalls.h

---

### Post by giriembedded on 2010-05-08
Hi,

      I searched for the '.S' files through out the filesystem with the following command

           $find / -name '*.S'

      but i am not getting the files   syscall_table.S or syscall_table_32.S in any of the folders

 Regards 
giri

---

### Post by gmargo on 2010-05-09
Have you downloaded the Linux source code?  It is not installed by default.  The easiest way to get the source is to create a temporary directory and use apt-get source.  There is no need to use the /usr/src/ directory.  And no need to be root.:
```

$ mkdir $HOME/kernel
$ cd $HOME/kernel
$ apt-get source --only-source linux

```The tutorial you are following is old but not obsolete.  A few files have moved around, and 32/64-bit combined, but the basics are correct.

I successfully followed this tutorial:
[http://www.cmpe.boun.edu.tr/courses/cmpe322/fall2009/Tutorials/Kernel%20Compile%20and%20SysCall%20Add%20(Ubuntu%208.04).pdf]("http://www.cmpe.boun.edu.tr/courses/cmpe322/fall2009/Tutorials/Kernel%20Compile%20and%20SysCall%20Add%20%28Ubuntu%208.04%29.pdf")

And there are other tutorials that can be easily found through google:
[http://www.google.com/search?q=Kernel+Compile+and+SysCall+Add](http://www.google.com/search?q=Kernel+Compile+and+SysCall+Add)

This one is quite detailed for Karmic:
[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

And more good info on compiling the kernel:
[http://www.google.com/search?q=ubuntu+kernel+compile](http://www.google.com/search?q=ubuntu+kernel+compile)

---


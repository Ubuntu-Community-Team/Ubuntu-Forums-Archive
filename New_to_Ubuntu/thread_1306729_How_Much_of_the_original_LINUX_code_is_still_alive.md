---
title: "How Much of the original LINUX code is still alive in UBUNTU?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by rciafardone on 2009-10-30
Hello, as just a curios tip of info. How much of the original LINUX source code is still alive in UBUNTU 9.10? 0% - 1% - 10%... 

I know I could check the source code myself but that&#8217;s a LOT of work, and knowing how some people are very passionate in the community I thought of trying my luck to see if someone knew the answer.

Thank you.

---

### Post by Tahakki on 2009-10-30
All of it, I think. Linux isn't an OS, it's a kernel. Ubuntu runs on this kernel, so it uses all of its code.

---

### Post by doas777 on 2009-10-30
of kernel 0.01? probably none of it. mabey a comment or two, but i have to assume that just about everything has changed since the bbs post.
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)
 [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by mikechant on 2009-10-30
Ubuntu and all other Linux versions/distros consist of two main parts - the kernel, which forms the core of the operating system, and the applications/utilities etc. which run using the kernel to communicate with the hardware.

Linux is actually just the kernel, and the Ubuntu kernel is 99%+ the same source code as the 'plain' Linux kernel, with a few Ubuntu specific changes.

The applications/utilities etc. which make up the rest of Ubuntu are not really Linux as such - they are just a selection from a large set of applications/utilities which can run on Linux and are commonly distributed with it. The issue is confused by the common practise of using the term 'Linux' to refer to the kernel plus some basic selection of utilities and applications. However, logically it is quite clear that the basic utilities (eg. the bash shell, and basic commands like ls, cp, mv etc.) are not really part of Linux because they can and do run with non-Linux kernels.

---

### Post by blur xc on 2009-10-30
All of those utilities and tools are known as the GNU utilities.  GNU (pronounced Guh-New) stands for GNU's Not Unix.  What we refer to as Linux is really GNU/Linux.  GNU runs on other kernels as well (bsd, I think?)...

BM

---

### Post by markbuntu on 2009-10-30
There is still probably not much of original code left since it was low level stuff for the 386 chips and the entire structure of kernel programming has changed drastically since then.

It would be an good question to ask Linus since he is probably the only one who really knows.

---


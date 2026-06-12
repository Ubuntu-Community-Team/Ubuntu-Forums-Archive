---
title: "[SOLVED] What kernel should I use?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-12-25
I have recently glanced at this thread: [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

I'm wondering what kernel I should switch too. My computer is an Inspiron E1505 with a Centrino Duo. If I switch kernels would this erase my files?

---

### Post by billgoldberg on 2008-12-25
> **Bigbob22 said:**
> I have recently glanced at this thread: [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

I'm wondering what kernel I should switch too. My computer is an Inspiron E1505 with a Centrino Duo. If I switch kernels would this erase my files?

You should use the one you are using now.

Ubuntu will provide security updates for the current kernel.

I wouldn't advise you to compile your own kernel, especially if you have to ask if it will delete your files (which it won't).

---

### Post by logos34 on 2008-12-25
> **billgoldberg said:**
> You should use the one you are using now.

Ubuntu will provide security updates for the current kernel.

I wouldn't advise you to compile your own kernel, especially if you have to ask if it will delete your files (which it won't).

+1

About the only thing that might give you noticeable performance jump would be switching to the real-time/low-latency kernel (-rt), but last time I looked it was buggy in Intrepid and even UbuntuStudio 8.10 is not using it

---

### Post by Toshibawarrior on 2008-12-25
True...stay away from compiling kernels...The -rt was very cool back in Hardy but I've read that in intrepid it's kinda problematic.

Stay with the defualt/generic kernel. And keep in mind that the thread you read was from 2005...Lots and lots of things have changed in Linux over the years.

Simply remember "If it ain't broke...don't fix it." A simple statement that i've had learned the hard way.

:popcorn:

---


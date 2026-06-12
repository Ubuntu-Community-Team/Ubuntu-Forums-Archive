---
title: "Possible to dual boot 64 bit Ubuntu &amp; 32 bit Windows?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by den160593 on 2010-04-29
Hi,

I was wondering if it was possible to dual boot 64 bit Ubuntu and 32 bit Windows? 

Thanks

---

### Post by lisati on 2010-04-29
> **den160593 said:**
> Hi,

I was wondering if it was possible to dual boot 64 bit Ubuntu and 32 bit Windows? 

Thanks

Short answer: yes.
Generally speaking, you will only have one OS running at a time, so it shouldn't matter which each is.

---

### Post by carl4926 on 2010-04-29
> **den160593 said:**
> Hi,

I was wondering if it was possible to dual boot 64 bit Ubuntu and 32 bit Windows? 

Thanks
A prerequisite of course is 64 bit hardware. But you already knew that.:lolflag:

---

### Post by anewguy on 2010-04-29
I've always been a little curious about another take on this - I think I know the answer, but what the heck:

Is it possible to run 64-bit Linux in a VM on a 32-bit Windows host if the hardware is 64-bit?

My suspicion is no, but then again, what do I know.

Dave ;)

---

### Post by carl4926 on 2010-04-29
I'm sure it is No.

---

### Post by Paqman on 2010-04-29
> **anewguy said:**
> 
Is it possible to run 64-bit Linux in a VM on a 32-bit Windows host if the hardware is 64-bit?


Nope, your host OS needs to be 64-bit to run 64-bit VMs.

---

### Post by 3rdalbum on 2010-04-29
I think VMware Workstation can run 64-bit guests within a 32-bit host OS, as long as the processor supports 64-bit. Not sure about any of the free-as-in-beer virtualisation solutions though.

---

### Post by computerguts on 2010-04-29
you could partition you hard drive and as long as your computer supports 64 bit operating systems you should be good to go. Or if you have the know how you could install a second hard drive in your machine and not have to worry about the partiton on the drive failing. 

Another advantage of this is you could back up your files both ways so that you always have an operating system on your computer and all your files from both operating sytems without having to restart multiple times to retrive files.

---

### Post by Calash on 2010-04-29
> **3rdalbum said:**
> I think VMware Workstation can run 64-bit guests within a 32-bit host OS, as long as the processor supports 64-bit. Not sure about any of the free-as-in-beer virtualisation solutions though.

You are correct.

If your processor supports virtualization (Most vPro enables processors do) you can run a 64bit guest in a 32bit host.

When we tried it we found the stability was not the best, but this was a bit over a year ago so it is likely they have improved the function.

I also thing the latest Virtualbox may have the ability, but I can not say for sure...I run 64bit on all my hosts so I have nothing to test with.

---


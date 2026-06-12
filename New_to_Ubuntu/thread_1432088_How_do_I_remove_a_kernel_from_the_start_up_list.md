---
title: "How do I remove a kernel from the start up list?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by myolbug on 2010-03-17
I installed a kernel at the request of a bug fix email, but it is really the wrong deal for my computer.  If I try and boot into it, which it does automatically unless I hit escape, my computer goes haywire, almost like there is no drive.

I am going to send this data to Cononical, but how do I get this off of my list?

---

### Post by Alabamaschalk on 2010-03-17
Hi!
You can use startupmanager to choose the kernel that boots at startup.
I think if you just remove the Kernel (which can be done by Synaptic I think, but havem't tried yet) I suppose you have to do a grub update.
But may be someone knows better

---

### Post by 2hot6ft2 on 2010-03-17
To remove the kernel go to synaptic
System > Administration > Synaptic Package Manager
and search for the kernel by its number and remove both the linux-image and linux-headers for that kernel.

For each kernel there are 3 files that are needed. like below (these are examples).
These are needed for kernel 2.6.31-20:
> linux-headers-2.6.31-20
linux-headers-2.6.31-20-generic
linux-image-2.6.31-20-generic
and for kernel 2.6.31-19 these are needed:
> linux-headers-2.6.31-19
linux-headers-2.6.31-19-generic
linux-image-2.6.31-19-generic
Be careful when removing kernels not to remove all of them or removing any of the 3 needed files as shown above for kernels you wish to keep.
Otherwise you will most likely not be able to boot into Ubuntu.
Once you have the ones marked that you wish to remove click on Apply.

---

### Post by readycarpenter on 2010-03-17
what version of ubuntu are you using? as of ubuntu 9.10 grub has been upgraded to grub2 or grub-pc. grub2 is not as configurable as past versions.

you can open package manager and remove the kernels you no longer need.


"Open Source is not just a method, but a belief system"
[My Blog]("http://theaustingeek.com/blog")
[Computer Repair Web Design Austin Bastrop Elgin]("http://theaustingeek.com")

---

### Post by Penguin Guy on 2010-03-17
> **readycarpenter said:**
> what version of ubuntu are you using? as of ubuntu 9.10 grub has been upgraded to grub2 or grub-pc. grub2 is not as configurable as past versions.
I actually find it more configurable, just takes longer to learn how.

As for removing the kernel, just open synaptic and search for [FONT="Courier New"]linux[/FONT], then remove any unneeded kernels.

---

### Post by Paqman on 2010-03-17
> **readycarpenter said:**
> grub2 is not as configurable as past versions.


Eh?

---

### Post by stoogiebuncho on 2010-03-17
> **2hot6ft2 said:**
> To remove the kernel go to synaptic
System > Administration > Synaptic Package Manager
and search for the kernel by its number and remove both the linux-image and linux-headers for that kernel.

For each kernel there are 3 files that are needed. like below (these are examples).
These are needed for kernel 2.6.31-20:

and for kernel 2.6.31-19 these are needed:

Be careful when removing kernels not to remove all of them or removing any of the 3 needed files as shown above for kernels you wish to keep.
Otherwise you will most likely not be able to boot into Ubuntu.
Once you have the ones marked that you wish to remove click on Apply.

+1  

It sounds like you don't want to ever use this kernel again, so this is the easiest and best way to get rid of it.  Write down the kernel version number of the kernel you want to get rid of, open up synaptic, and remove the three packages as outlined above.  It will remove it from your boot menu automatically.

---

### Post by myolbug on 2010-03-17
Thank you everyone.  I for now have just erased the one that was causing problems.  I appreciate it!

---


---
title: "Grub Loader is showing duplicate entries for the same linux installation"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by aka.bhagvanji on 2009-04-06
I am new to linux.. just installed ubuntu ultimate 2.0
Everything was fine until yesterday when the grub loader started showing duplicate entries for the same linux installaion. I have attached a picture describing the same.

Moreover when I typed the following command in the terminal:
dpkg -l | grep -i linux-image

this is what i got:
ii  linux-image-2.6.27-11-generic              2.6.27-11.27                                Linux kernel image for version 2.6.27 on x86/x86_64
ii  linux-image-2.6.27-7-generic               2.6.27-7.16                                 Linux kernel image for version 2.6.27 on x86/x86_64
ii  linux-image-generic                        2.6.27.11.14                                Generic Linux kernel image


In the image (that i have attached) how do i get rid of the 1st linux-generic boot option. The second option is the original installation with all my default settings and updated packages. HELP!

---

### Post by tad1073 on 2009-04-06
2.6.27-11 is the updated kernel.

When you install a new kernel version the old one is not over-written or deleted for the purpose of having a back-up kernel in case something goes wrong with the new one.

---

### Post by Eisenwinter on 2009-04-06
The older kernel is not deleted when you installed a new one in Ubuntu. It is still bootable.

I suggest you leave it there, but if it bothers you, you can simply edit /boot/grub/menu.lst to remove the older kernel from the menu list, then it'll still be installed, but you won't see it when you get to the grub menu.

---

### Post by aka.bhagvanji on 2009-04-06
Ah, actually the thing is I haven't installed any new version. It has come by itself. The v '7' has all the settings i had configured..whereas the '11' doesn't. Can i get rid of v '11'?

---

### Post by nandemonai on 2009-04-06
> **aka.bhagvanji said:**
> Ah, actually the thing is I haven't installed any new version. It has come by itself. The v '7' has all the settings i had configured..whereas the '11' doesn't. Can i get rid of v '11'?

It's only a new kernel.. What do you mean by 'doesn't have the settings you've configured'?

---

### Post by aka.bhagvanji on 2009-04-06
Some settings like.. compiz desktop settings... Firefox addons.. nothing great actually.. the appearance of the new kernel (image) in the boot loader was misleading.. i thought it was some kind of bug , or another copy of linux got self installed..

How and why do new kernels get installed?? coz i am sure that i didnt install them!. What if one more kernel comes there in the options in the future!>>?

---

### Post by nandemonai on 2009-04-06
> **aka.bhagvanji said:**
> Some settings like.. compiz desktop settings... Firefox addons.. nothing great actually.. the appearance of the new kernel (image) in the boot loader was misleading.. i thought it was some kind of bug , or another copy of linux got self installed..

How and why do new kernels get installed?? coz i am sure that i didnt install them!. What if one more kernel comes there in the options in the future!>>?

A kernel update (which is automatic when you upgrade through update manager) shouldn't affect any of your desktop settings at all.

It's generally a good idea to update your kernel as it (usually *cough*) adds better hardware support, security updates, that kind of thing.

I've never seen a kernel update affect anything on the desktop side of things except perhaps things you've manually compiled or that depends on a previous kernel (VMware comes to mind here) though you can usually recompile that kind of thing.

I find it odd you've lost setting with a new kernel.. seems to me like something else would be to blame here..

---

### Post by aka.bhagvanji on 2009-04-06
ThanQ nandemonai, it was relieving to understand that it was just a kernel update.. WHat do u suggest-should i keep the old version also? will  newer kernel updates effect effect the ascii mapping in the Booting hash table?

---

### Post by lisati on 2009-04-06
My $0.02: the "recovery mode" shown in the screen shot (you'll notice that it has the same version number) is the equivalent of "safe mode" in Windows.

You don't normally need to worry too much about new kernels and deleting old ones unless disk spaces is at a premium.

---

### Post by aka.bhagvanji on 2009-04-06
Woah.. it takes disk space???.. HOW much?
I have just set aside 9 GB HD space for linux and 1 Gb for the swap.. the rest 150 GB is for windows.

---

### Post by nandemonai on 2009-04-06
> **aka.bhagvanji said:**
> ThanQ nandemonai, it was relieving to understand that it was just a kernel update.. WHat do u suggest-should i keep the old version also? will  newer kernel updates effect effect the ascii mapping in the Booting hash table?

I usually keep 2-3 previous kernels 'just in case' something breaks so I can revert to an older one. Cleaning out old kernels can be tricky in that it can be easy to make a mistake and remove the current one. If you're not strapped for disk space I say leave em and just remove the entries in /boot/grub/menu.list though any subsequent kernel updates will rebuild the list making it a bit of a pain as you have to go back and remove the entries again.

As far as the ascii mapping I have no idea because I'm not too sure what you mean, that said, something like ascii maps are a standard and not likely to change anytime soon ;)

My suggestion would be use the new kernel, redo your lost settings (still not too sure what caused that..) and yeah if everything hardware wise is still working you're golden.

---

### Post by nandemonai on 2009-04-06
> **aka.bhagvanji said:**
> Woah.. it takes disk space???.. HOW much?
I have just set aside 9 GB HD space for linux and 1 Gb for the swap.. the rest 150 GB is for windows.

~45MB per kernel and ~2-4MB for the kernel modules.

---

### Post by aka.bhagvanji on 2009-04-06
Cool.. I'll keep them all .. ty..

---

### Post by jdavid4it on 2010-05-24
:) Hi everybody!  Just wanted to add that I also was looking for an answer regarding this issue about the duplicated kernels in the GRUB boot screen.  I've read, I've studied, I've learned, "I thank you all"  :-)

---


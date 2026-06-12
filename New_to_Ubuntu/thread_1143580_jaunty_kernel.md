---
title: "jaunty kernel"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-04-30
can i use another kernel with jaunty?  or impex?


i tried to install jaunty, but had lots of freezes so i reinstalled ipex, but after i updated the kernel got the freezes again.

is there a security risk not to use the lastest kernel with ubuntu?

---

### Post by blazemore on 2009-04-30
You can use whatever kernel you want with any system. Most are available as .debs for easy installation.

---

### Post by skymera on 2009-04-30
Here is the Ubuntu kernel list:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Good luck :)

---

### Post by Eneerge on 2009-04-30
If you would like, you could compile your own kernel for use.  Here's a very easy guide to follow that can help you do this: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) .

Compiling your own kernel can help you learn more about your system.  You can look at all of the options you have control of that goes into your kernel.  You can research all of these items and tune the kernel to your needs.  It could take some time to fine-tune everything, and the hard benefits (EG: performance increase) is not going to be very extravagant.  However, you well have a better understanding of everything that is working behind the scenes and if you play around enough to break it (yes, break it), you can figure out what options you need to for certain configurations which can help you to tweak other systems in the future much quicker.

EG: In order to build the ATI fglrx proprietary driver, you cannot disable ACPI settings in your kernel build, because the kernel module will fail to build without the acpi kernel module(s).

Knowledge learned from breaking things and then fixing them is some of the best you can obtain.  However, if you don't really care about learning about all the different modules and settings of the kernel, you can install some different kernels through Synaptic or you might find some .deb packages as mentioned by the user above.

---

### Post by northwestuntu on 2009-04-30
thanks for the good advice everyone.

couple more things.

you have to install both the header and images debs to install? 

how do you make your system default to that kernel?

should i use the newest one possible?

why does ubuntu not use the latest kernel all the time?

---

### Post by skymera on 2009-04-30
> **northwestuntu said:**
> thanks for the good advice everyone.

couple more things.

you have to install both the header and images debs to install? 

how do you make your system default to that kernel?

should i use the newest one possible?

why does ubuntu not use the latest kernel all the time?

1) Yes

2) The kernel will appear at GRUB menu

3) Try the latest stable

4) Could be compatibility issues

---

### Post by northwestuntu on 2009-04-30
awesome!! :popcorn:

thanks for the help skymera :P

---

### Post by northwestuntu on 2009-05-01
ok i keep getting this message when trying to install one of the debs.

```
Error: Dependency is not satisfiable: linux-headers-2.6.28-02062809
```

but that's the file i am installing?

is there a easier way to upgrade or downgrade my kernel? im convinced the kernel is causing my crashes in jaunty just need to try something else.

also how does this affect my nvidia video driver?  do all kernels work with all video drivers? i have 180.44 enabled hardware driver.

thanks

---


---
title: "how to add system call to the kernal"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by rejuvenate on 2010-03-04
I want to add simple system call
> /* adding helloworld system call */
#include <linux/linkage.h>

asmlinkage int sys_helloworld() {
   printk(KERN_EMERG "Hello World!\n");
   return 0;
}

i want to add this to the kernel how can i do it..because the link i am following is tell to make
> Define a new system call number for NR helloworld in
/usr/src/linux-2.x/include/asm-i386/unistd.h.
and then
> Add an entry .long sys helloworld to the sys call table defined
in /usr/src/linux-2.x/arch/i386/kernel/entry.S file.
but in my system there is no i386 folder instead it have ia64 and in that also it don't have the /kernel/entry.s ..
i am working on ubuntu9.10 and kernel linux 2.6.31
the link i am using is at [http://www.ivanescobar.com/oper1_material/projectch2.pdf](http://www.ivanescobar.com/oper1_material/projectch2.pdf)

---

### Post by Kulgan on 2010-03-05
In the Absolute Beginner Forum? 

I think you might have more success answering this question if you try over in Programming Talk ([http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)). Since your problem appears to be x64-related, make sure to tag it with the "64 bit" prefix when making the post. 


- K

---


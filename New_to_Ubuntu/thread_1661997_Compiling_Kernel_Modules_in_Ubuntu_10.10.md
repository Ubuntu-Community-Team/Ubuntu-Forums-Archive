---
title: "Compiling Kernel Modules in Ubuntu 10.10"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by lionaneesh on 2011-01-07
After Being Fully Enthusiastic and ready to make my own Kernel Modules I started the work to be done to get started into kernel programming...
I have managed to successfully compile my own kernel...But while compiling my modules 
After trying continuously for  about 4-5 hrs....... I am totally frustrated and Asking for your help!!!

System Information :-

Linux Version	 	: Ubuntu 10.10 i386
Kernel Version 	: 2.6.32.26

The Problem :-

The main problem is the make part...
I have a hello-1.c code from [http://www.faqs.org/docs/kernel/x204.html](http://www.faqs.org/docs/kernel/x204.html)
```

/*  hello-1.c - The simplest kernel module.

 */

#include <linux/module.h>  /* Needed by all modules */

#include <linux/kernel.h>  /* Needed for KERN_ALERT */

int init_module(void)

{

   printk("<1>Hello world 1.\n");

	

   // A non 0 return means init_module failed; module can't be loaded.

   return 0;

}

void cleanup_module(void)

{

  printk(KERN_ALERT "Goodbye world 1.\n");

}

```
and a Makefile is from different source as the above source provides makefile for kernel 2.4
```

ifneq ($(KERNELRELEASE),)

# We were called by kbuild



obj-m += target.o



else  # We were called from command line



KDIR := /lib/modules/$(shell uname -r)/build

#KDIR := /home/cynove/src/kernel/linux-source-2.6.31

PWD  := $(shell pwd)



default:

	@echo '    Building target module 2.6 kernel.'

	@echo '    PLEASE IGNORE THE "Overriding SUBDIRS" WARNING'

	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules



install:

	./do_install.sh *.ko



endif  # End kbuild check

######################### Version independent targets ##########################



clean:

	rm -f -r *.o *.ko .*cmd .tmp* core *.i

```
I am constantly getting the same errors :-
```

    Building target module 2.6 kernel.

    PLEASE IGNORE THE "Overriding SUBDIRS" WARNING

make -C /lib/modules/2.6.32.26+drm33.12-explict-hax0r/build SUBDIRS=/home/aneesh/semtex modules

make[1]: Entering directory `/home/aneesh/source/linux-source-2.6.32'

make[2]: *** No rule to make target `/home/aneesh/semtex/target.c', needed by `/home/aneesh/semtex/target.o'.  Stop.

make[1]: *** [_module_/home/aneesh/semtex] Error 2

make[1]: Leaving directory `/home/aneesh/source/linux-source-2.6.32'

make: *** [default] Error 2


```

I am totally discouraged and frustrated by not getting results after trying so hard...
I checked the Makefile and seems it all is right ….
Really I am unable to get a clue what's wrong...
I thing maybe something is missing... But what?Where?Why?:confused::confused::confused:

Thanks in Advance

Your's faithfully
`uname -r`

---

### Post by janpol on 2011-01-07
Take a look at the name of your module (**hello-1**) and the name used in the makefile (**target**)

```
obj-m += target.o
```

Should be:

```
obj-m += hello-1.o
```

I suggest you to take a look at the Kernel Newbie Corner series from Linux.com, you can find 'em here:

[http://www.linux.com/search/kernel+newbie+corner/%252F?ordering=oldest&searchphrase=exact&limit=20]("http://www.linux.com/search/kernel+newbie+corner/%252F?ordering=oldest&searchphrase=exact&limit=20")

Good Luck!

---


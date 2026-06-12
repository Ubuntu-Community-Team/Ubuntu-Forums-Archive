---
title: "make: *** No rule to make target `make', needed by `hello'.  Stop."
date: 2009-06-24
forum: New to Ubuntu
---

### Post by girish24 on 2009-06-24
hi 
i am an absolute beginner so please guide me through thus one
i actually wanted to compile a example program helloworld using make files but the result i get is 
"make: *** No rule to make target `make', needed by `hello'.  Stop."
whenever i compile the make file
my makefile is this -- 

obj-m := hello.o
KDIR    := /usr/src/linux-headers-2.6.24-16/include/linux/$(shell uname -r)/build
PWD := $(shell pwd)
CC := gcc
WARN := -W -Wall -Wstrict-prototypes -Wmissing-prototypes
hello:    ${MAKE} $(WARN)    -C $(KDIR) M=$(PWD)/src modules
clean:        rm -rf $(PWD)/src/*.*o; rm -rf $(PWD)/src/*.mod*;
        rm -rf $(PWD)/src/*odule*;
insmod:        insmod ./src/hello.ko;
rmmod:        rmmod hello;

my program is ----
#include <linux/module.h> 
#include <linux/init.h>  


int __init mod_first(void)
{
   printk("Hello world. \n");
    
   // A non 0 return means init_module failed; module can't be loaded.
   return 0;
}


void __exit mod_last(void)
{
  printk("Goodbye world. \n");
}  
module_init(mod_first);
module_exit(mod_last);
MODULE_LICENSE("GPL");

please can anyone help me out on this

---

### Post by cmnorton on 2009-06-24
Is the name of your make file makefile?

What language is your source? It looks like C, but I've never heard of printk.

Also, are := part of standard makefile syntax? (I don't know, but I've never seen that syntax.)

---

### Post by girish24 on 2009-06-24
yes the make file i named it as makefile
and also the source is 'c'
but this is an example program from one book i have been reading for kernel moduling
i haven't able to figure out even it is correct or wrong if it is possible can u give a code for it ??
just how to write a program and execute it using a make file plz :(

---

### Post by cmnorton on 2009-06-25
With make files, start small, and move up, literally.  I have attached hello.txt and makefile.txt so they would upload to this post. You would need to rename them to hello.c and makefile respectively.

I think one your problems is you do not have a default target list, and I cannot find an individual list of targets. I put my stuff I want built under all:, and if I want one thing built I use the individual target on the command line. 

The other thing is it appears make thinks one of your targets is make. 

That's why I say start with something simple, and then add complexity to your makefile.

Edit

---

### Post by girish24 on 2009-06-25
thank u i will try this and let u know how far i have come thanks for the help :D

---


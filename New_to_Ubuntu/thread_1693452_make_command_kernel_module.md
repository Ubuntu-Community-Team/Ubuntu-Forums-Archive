---
title: "make command kernel module"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by chew725 on 2011-02-22
Hi,

I'm trying to create a simple kernel module, and I am having a lot more trouble than I feel is necessary. Here is my code 
#include <linux/module.h>
#include <linux/kernel.h>
int init_module(void)
{
        printk(KERN_INFO "Hello World!\n");
        return 0;
}
void cleanup_module(void)
{
        printk(KERN_INFO "Bye-bye World!.\n");
}
and my Makefile is

obj-m += hello.o
all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
I am trying to use the make command to compile the program, but I keep getting these errors: 

seed@seed-desktop:~/Documents/lab2/hello$ make hello
cc     hello.c   -o hello
hello.c:1:26: error: linux/module.h: No such file or directory
hello.c: In function ‘init_module’:
hello.c:5: error: ‘KERN_INFO’ undeclared (first use in this function)
hello.c:5: error: (Each undeclared identifier is reported only once
hello.c:5: error: for each function it appears in.)
hello.c:5: error: expected ‘)’ before string constant
hello.c: In function ‘cleanup_module’:
hello.c:10: error: ‘KERN_INFO’ undeclared (first use in this function)
hello.c:10: error: expected ‘)’ before string constant
make: *** [hello] Error 1
seed@seed-desktop:~/Documents/lab2/hello$ 


I am just using sample code from online, so I'm not sure why this isn't working...

Please help!

---


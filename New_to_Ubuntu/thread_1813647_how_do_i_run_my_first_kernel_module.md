---
title: "how do i run my first kernel module"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by pradhan.mcis on 2011-07-28
i wanted to try my hand at executing a very small module which is the  first example in Linux device Drivers by rubini. the contents of my  test. c are as follows:

[B]#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");
static int hello_init(void)
{
    printk(KERN_ALERT "Hello, world\n");
    return 0;
}
static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye, cruel world\n");
}
module_init(hello_init);
module_exit(hello_exit);
[/B]
and i have created a Makefile with the following contents :

**obj -m := test.o**

when i try to give the command Make it says **"make: Nothing to be done for `test.c'.**


what might be the error???

---


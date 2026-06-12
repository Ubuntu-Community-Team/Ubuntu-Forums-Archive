---
title: "kernel programming help in Ubuntu 8.04LTS"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-08-05
Hi all,

    I'm very new to kernel programming, Please anyone help me how to compile the program given in below. I'm using Ubuntu 8.04 LTS and  kernel  is 2.6.24-24-generic. Do I need to install any software to compile this program. Please give me step by step explanation for this. Please tell me any good IDE for kernel programming which will good as eclipse.


#include <linux/module.h>
#include <linux/init.h>

static int  mymodule_init(void)
{
 printk ("My module worked!\n");
        return 0;
}

static void  mymodule_exit(void)
{
 printk ("Unloading my module.\n");
        return;
}

module_init(mymodule_init);
module_exit(mymodule_exit);

MODULE_LICENSE("GPL");

---


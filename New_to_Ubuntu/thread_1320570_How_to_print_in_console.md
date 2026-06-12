---
title: "How to print in console"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by girish24 on 2009-11-09
I am compiling a hello world kernel module. When using printk(), setting up any priority, i am not able to print the statement on my terminal. I am able to see it in my log file though. 

This is the program i am working on - its just a hello world program

#include <linux/module.h>   
#include <linux/kernel.h>   

int init_module(void)
{
    printk(KERN_INFO "Hello world 1.\n");

    return 0;
}

void cleanup_module(void)
{
    printk(KERN_INFO "Goodbye world 1.\n");
}

After loading this into the kernel and executing, i am not getting the result on my terminal, rather it is being printed in the log file.
I have used all the priorities of printk() but none of them are printing on my console.

---

### Post by Penguin Guy on 2009-11-09
[S]I don't know an awful lot about kernel modules but couldn't you just use [COLOR="Green"]print "Hello World!"[/COLOR]?[/S]

Edit: Sorry, looks like you're using C, not Python.

---

### Post by girish24 on 2009-11-09
I have tried even that but print command is not recognised for the above header. An error is displayed -
error: implicit declaration of function &#8216;print&#8217;

Which header should i use?

---

### Post by mikechant on 2009-11-10
I would say you probably want
```
#include <stdio.h>
```
at the top of the code
and to use 'printf' to print to the terminal, i.e.
```
printf("Hello world 1.\n");
```

---

### Post by Penguin Guy on 2009-11-10
I assume you're using C, if so then your program should look like this:
```

#include <stdio.h>

int main()
{
    printf("Hello World!\n");
    return 0;
}

```
As I said before, I don't know a lot about kernel modules so there is a possibility that this won't work for what you're trying to do.

---

### Post by wojox on 2009-11-10
```

#include <linux/module.h>     /* needed by all modules */
#include <linux/init.h>     /* needed for macros */
#include <linux/kernel.h>     /* needed for printk */

int my_entry_fn_name()
{
    printk(KERN_INFO "Hello World \n");
    return 0;         /* return zero on successful loading*/
}

void my_exit_fn_name()
{
    printk(KERN_INFO "Good Bye World \n");
}

module_init(my_entry_fn_name);
modue_exit(my_exit_fn_name);


```

---


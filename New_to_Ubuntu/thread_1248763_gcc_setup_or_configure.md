---
title: "gcc setup or configure"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by newport_j on 2009-08-24
I recently set up Ubuntu 8.04 on my laptop computer. I wanted to take it home with me.

However, I recently noticed that it will not compile anything.


When I try to compile the easiest program out there, hello world, it crashes with a lot or errors.. I guess one must configure  gcc after Ubuntu 8.05 is installed. My error output when I compile hello.c is attached..


How do I configure gcc?

I guess you cannot just install it. It must be configured.


newport_j

---

### Post by Hospadar on 2009-08-24
looks like something wrong in your code, could you link that as well?

---

### Post by lisati on 2009-08-24
> **newport_j said:**
> I recently set up Ubuntu 8.04 on my laptop computer. I wanted to take it home with me.

However, I recently noticed that it will not compile anything.


When I try to compile the easiest program out there, hello world, it crashes with a lot or errors.. I guess one must configure  gcc after Ubuntu 8.05 is installed. My error output when I compile hello.c is attached..


How do I configure gcc?

I guess you cannot just install it. It must be configured.


newport_j
> james@james-laptop:~/Desktop$ gcc hello.c 
hello.c:1:19: error: stdio.h: No such file or directory 
hello.c: In function ‘main’: 
hello.c:5: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
hello.c:5: error: ‘stderr’ undeclared (first use in this function) 
hello.c:5: error: (Each undeclared identifier is reported only once 
hello.c:5: error: for each function it appears in.) 
james@james-laptop:~/Desktop$ 

Try this:
```
sudo apt-get install build-essential
```

---

### Post by Thelasko on 2009-08-24
If you use the [apt package manager]("http://www.psychocats.net/ubuntu/installingsoftware") it will download, install, and configure the software you choose to install.  GCC is part of the build-essential package.  Installing that as lisati mentioned, should solve your problem.

---


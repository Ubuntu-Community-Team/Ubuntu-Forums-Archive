---
title: "Advice about kernel &amp; compiling module/driver"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-27
I have a new motherboard and cpu. The CPU is a K10 family of AMD cpu-s. Karmic does not have a lm-sensors module in-built into the kernel. I have tried following:

mechdave

at 

[http://ubuntuforums.org/showthread.php?t=1253858](http://ubuntuforums.org/showthread.php?t=1253858)

but when I run 

make 

all I get is:

mark@Lexington-19-Karmic:/usr/src/k10temp_module$ make
make: Nothing to be done for `all'.

I copied his two files: "make" and "install.sh" and put them in the /usr/src/k10temp_module directory.

I sent a PM to the mechdave a week ago. He may not be coming back to the forum any longer...

---

### Post by inclusivedisjunction on 2010-02-27
I'm thinking you misread his instructions. The first block of code he listed, 

```
obj-m += k10temp.o
all :
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

should have been named 'Makefile', not 'make'.

---

### Post by Mark_in_Hollywood on 2010-02-27
It is. See attached screenshot.

---

### Post by inclusivedisjunction on 2010-02-27
That's funny; that error message usually results from a missing Makefile (or perhaps a Makefile that has nothing to do), and the same Makefile and code compiles fine on my computer (I didn't bother trying to install it). I've attached a tarball of my copy for your comparison.

---

### Post by Mark_in_Hollywood on 2010-03-01
As I'm truly lost about this, I'm marking the thread as solved as I got some help. I'm just not competent enough to know how to proceed. Thanks.

---


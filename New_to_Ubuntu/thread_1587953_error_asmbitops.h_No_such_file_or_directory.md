---
title: "error: asm/bitops.h: No such file or directory"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by kutub on 2010-10-04
Hi,
I am trying to compile a file named process_30sec.c(thats a C program) through the Ubuntu terminal and it is showing the following error in command terminal:
**process_30sec.c:15:23: error: asm/bitops.h: No such file or directory**

I have just started using Ubuntu&Linux so I am not familiar with lots of commands and things going around.
I am using the following command to compile the process_30sec.c file:
[B]kutub@ubuntu:~/Desktop$ gcc process_30sec.c

[/B]The above mentioned program file contains a header file <asm/bitops.h>, that I need to use in the program.
It seems that this header file is not recognized by the system, and it needs to be included somewhere in the system so that the terminal would allow me to compile this program.

Please suggests what to do??
Thanks!!

---

### Post by andrewthomas on 2010-10-04
Did you install the kernel headers for your kernel as was suggested on the other thread that you posted on linuxquestions.org? 

[http://www.linuxquestions.org/questions/linux-newbie-8/error-asm-bitops-h-no-such-file-or-directory-836073/](http://www.linuxquestions.org/questions/linux-newbie-8/error-asm-bitops-h-no-such-file-or-directory-836073/)


You really shouldn't post the same questions on multiple forums.

---


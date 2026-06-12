---
title: "Orange Icon 225 PHARscape - did work but now does not!!"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by TpyKv on 2008-11-25
Hello good people.

I am frustrated! Last week, this was working!

[http://www.pharscape.org/content/view/66/53/](http://www.pharscape.org/content/view/66/53/)

but now, after a clean install, it will not! 

I'm on Intrepid,  and this is the error message :

kevin@vaio:~$ cd ~/Desktop

kevin@vaio:~/Desktop$ tar zxf hso-1.2.tar.gz

kevin@vaio:~/Desktop$ cd hso

kevin@vaio:~/Desktop/hso$ make

mkdir -p /home/kevin/Desktop/hso/tmp/.tmp_versions

make -C /lib/modules/2.6.27-7-generic/build M=/home/kevin/Desktop/hso MODVERDIR=/home/kevin/Desktop/hso/tmp/.tmp_versions modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'

  CC [M]  /home/kevin/Desktop/hso/hso.o

In file included from /home/kevin/Desktop/hso/hso.c:38:

/home/kevin/Desktop/hso/hso.h:129:1: warning: "WARN" redefined

In file included from include/asm/bug.h:38,

                 from include/linux/kernel.h:20,

                 from include/linux/sched.h:52,

                 from /home/kevin/Desktop/hso/hso.h:12,

                 from /home/kevin/Desktop/hso/hso.c:38:

include/asm-generic/bug.h:57:1: warning: this is the location of the previous definition

/home/kevin/Desktop/hso/hso.c:176: warning: initialization from incompatible pointer type

/home/kevin/Desktop/hso/hso.c: In function ‘_hso_serial_set_termios’:

/home/kevin/Desktop/hso/hso.c:1662: error: ‘struct tty_ldisc’ has no member named ‘set_termios’

{standard input}: Assembler messages:

{standard input}:9: Warning: can't open .lst: Permission denied

GAS LISTING  			page 1





   1              	.file "hso.c"

   9              	.Ltext0:



GAS LISTING  			page 2





DEFINED SYMBOLS

                            *ABS*:0000000000000000 hso.c



NO UNDEFINED SYMBOLS

make[2]: *** [/home/kevin/Desktop/hso/hso.o] Error 1

make[1]: *** [_module_/home/kevin/Desktop/hso] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

make: *** [modules] Error 2

kevin@vaio:~/Desktop/hso$ sudo make

mkdir -p /home/kevin/Desktop/hso/tmp/.tmp_versions

make -C /lib/modules/2.6.27-7-generic/build M=/home/kevin/Desktop/hso MODVERDIR=/home/kevin/Desktop/hso/tmp/.tmp_versions modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'

  CC [M]  /home/kevin/Desktop/hso/hso.o

In file included from /home/kevin/Desktop/hso/hso.c:38:

/home/kevin/Desktop/hso/hso.h:129:1: warning: "WARN" redefined

In file included from include/asm/bug.h:38,

                 from include/linux/kernel.h:20,

                 from include/linux/sched.h:52,

                 from /home/kevin/Desktop/hso/hso.h:12,

                 from /home/kevin/Desktop/hso/hso.c:38:

include/asm-generic/bug.h:57:1: warning: this is the location of the previous definition

/home/kevin/Desktop/hso/hso.c:176: warning: initialization from incompatible pointer type

/home/kevin/Desktop/hso/hso.c: In function ‘_hso_serial_set_termios’:

/home/kevin/Desktop/hso/hso.c:1662: error: ‘struct tty_ldisc’ has no member named ‘set_termios’

make[2]: *** [/home/kevin/Desktop/hso/hso.o] Error 1

make[1]: *** [_module_/home/kevin/Desktop/hso] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

make: *** [modules] Error 2

kevin@vaio:~/Desktop/hso$ 



 - - Does anyone have any idea what is going wrong here? I have build-essential....

Thank you,

Kevin

---

### Post by TpyKv on 2008-11-26
Bump!

Laptop is useless without the internet... if you can help...? ](*,)

---

### Post by TpyKv on 2008-11-26
I've posted this to the Pharscape forums in the hope that they can help.....

---

### Post by TpyKv on 2008-11-29
OK so the pharscape forums cannot help. and after a reinstall I still can't get it working.

Does anyone have any suggestions, at all? please?

---

### Post by Neill_R on 2009-09-20
I have similar to you but have another problem name connection drops all the time see my other post.
I will let you know if i solve my problem just exactly what i did.

---


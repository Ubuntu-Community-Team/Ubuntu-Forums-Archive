---
title: "Inclusion of Header file"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by jero2rome on 2011-08-28
I'm writing a linux kernel module in c/c++ and using make file to compile

I'm very weak in terminology. sorry if i'm confusing you. But my question is staright forward.

My program is to create loadable kernel modules which would extend outgoing IP packets.

my header files are in /usr/src/include/linux-headers-2.6.38-11-generic/linux/

Now i need to include few other header files which are in

/usr/include/netinet/in.h
/usr/include/net/if.h
/usr/include/netdb.h
/usr/include/sys/socket.h
/usr/include/arpa/inet.h

i dont know how to include this in my source code.
**when I used #include <netinet/in.h> and compile I'm getting error**

root@jero-VirtualBox:/home/jero/Documents/workspace/updated# make
make -C /lib/modules/2.6.38-11-generic/build M=/home/jero/Documents/workspace/updated modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/jero/Documents/workspace/updated/hook.o
[B]In file included from /home/jero/Documents/workspace/updated/hook.c:19:0:
/usr/include/netinet/in.h:23:22: [COLOR=Red]fatal error:[/COLOR] features.h: No such file or directory
compilation terminated.[/B]
make[2]: *** [/home/jero/Documents/workspace/updated/hook.o] Error 1
make[1]: *** [_module_/home/jero/Documents/workspace/updated] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [all] Error 2

**how do i include these header files now.**

---

### Post by overdrank on 2011-08-28
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by snip3r8 on 2011-08-28
The way you have included files is correct so that shouldnt be the problem.

The problem is probably that you need to specify /usr/include/ in the make file
 another thing you could try and do is just copy your headers from /usr/include to your other header location
The final alternative would be to copy the files to your project directory and use

#include "file.h"

instead of

#include <file.h>

---


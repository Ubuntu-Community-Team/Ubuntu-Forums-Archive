---
title: "AT&amp;T Option Wireless GT Ultra Support"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Bill.Scott on 2008-10-31
Does anyone know if the above card will be supported with 8.10?
We have acquired multiple cards and have not been able to use them as 8.04 does not support the card. and I have not been able to find anyone that knows how to get it to.

---

### Post by helios17 on 2008-11-01
I have been in a running gunbattle with this card for a month.  Now there is a website that offers help of sorts.  The guy who is running the site is just doing it out of the kindness of his heart but trying to find comprehensive how-to's and data is like trying to find pieces of a shredded 100 dollar bill in a hurricane.  

It's not the guy's fault.  Option, the maker of this card has given him some but not near enough support.  They refuse to "officially" support Linux so Paul has taken it upon himself to do it.  Trouble is, each distro is dealing with different python issues and gcc builds...the famous libc6 hassles enter into it from time to time.  There are threads in this huge community that deal with it and I've followed the instructions perfectly and there just isn't any way I can get this card to work...even though the instructions here say it's "foolproof"
iusing linux are assuming it's plug and play.

That's funny...I've lost hair trying to get this card to work.  I am currently in contact with a guy I met at Portland named Kevin.  Donky-hotee I think he goes by on this forum.  Hopefully he can help us get this straightened out.  He's a brilliant python scripter so between the two of us, we ought to be able to write the missing gui's and system calls to make this work.  The link to the scattered information is:

[http://www.pharscape.org/content/view/66/53/](http://www.pharscape.org/content/view/66/53/)

---

### Post by Bill.Scott on 2008-11-17
Well, tried to follow his doc but needless to say first compile gives errors:
========================================================================
root@scubuntu001:~/Downloads/hso# make
mkdir -p /home/bscott/Downloads/hso/tmp/.tmp_versions
make -C /lib/modules/2.6.27-7-generic/build M=/home/bscott/Downloads/hso MODVERDIR=/home/bscott/Downloads/hso/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/bscott/Downloads/hso/hso.o
In file included from /home/bscott/Downloads/hso/hso.c:38:
/home/bscott/Downloads/hso/hso.h:129:1: warning: "WARN" redefined
In file included from include/asm/bug.h:38,
                 from include/linux/kernel.h:20,
                 from include/linux/sched.h:52,
                 from /home/bscott/Downloads/hso/hso.h:12,
                 from /home/bscott/Downloads/hso/hso.c:38:
include/asm-generic/bug.h:57:1: warning: this is the location of the previous definition
/home/bscott/Downloads/hso/hso.c:176: warning: initialization from incompatible pointer type
/home/bscott/Downloads/hso/hso.c: In function ‘_hso_serial_set_termios’:
/home/bscott/Downloads/hso/hso.c:1662: error: ‘struct tty_ldisc’ has no member named ‘set_termios’
make[2]: *** [/home/bscott/Downloads/hso/hso.o] Error 1
make[1]: *** [_module_/home/bscott/Downloads/hso] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2
root@scubuntu001:~/Downloads/hso# 
=========================================================================

Any Idea as to why? Do I need to install some libraries?

---


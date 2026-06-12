---
title: "alfa awus036nh"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by krikett on 2010-10-09
[COLOR=#000000]how do I install the alpha awus036nh on my ubuntu distro. [/COLOR]step by step. I do not really understand what I need to configure.

---

### Post by jtarin on 2010-10-09
You'll need the package aircrack-ng to begin with.

---

### Post by krikett on 2010-10-09
why? when i try to install aircrack this is what i get 


:
[FONT=monospace]krikettmannen@flesken:~/aircrack-ng-1.1$ make
make -C src all
make[1]: Entering directory `/home/krikettmannen/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/krikettmannen/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/krikettmannen/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/krikettmannen/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/krikettmannen/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12: fatal error: openssl/hmac.h: No such file or directory
compilation terminated.
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/krikettmannen/aircrack-ng-1.1/src'
make: *** [all] Error 2
[/FONT]

---

### Post by jtarin on 2010-10-10
Why are you compiling? Your just making things more difficult for yourself. It's available for download from Ubuntu software sources.

---

### Post by krikett on 2010-10-10
ok. I have now installed aircrack-ng with Ubuntu software sources. What is next to do?

---

### Post by jtarin on 2010-10-10
Sorry I was responding to the wrong post. As far as I know aircrack-ng is not required. Uninstall. if you want however it is still a useful program.Repost your topic under the heading of "**Wireless connection problem**" then tell about alfa awus036nh in your post.

---


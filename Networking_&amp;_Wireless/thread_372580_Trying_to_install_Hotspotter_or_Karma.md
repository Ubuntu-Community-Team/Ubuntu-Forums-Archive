---
title: "Trying to install Hotspotter or Karma"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by mact on 2007-02-28
I am an extreme rookie....

That said, I am trying to install Hotspotter.

On the install file it says: 
How to compile:
	- cd to the "src" directory and type "make"
	  (You should have now a binary named hotspotter)

This is what I get. .... any help. Thanks.

cc -g3 -ggdb -pipe -Wall   -c -o utils.o utils.c
utils.c:19:20: error: stdlib.h: No such file or directory
utils.c:21:19: error: stdio.h: No such file or directory
utils.c:22:20: error: string.h: No such file or directory
utils.c:23:19: error: crypt.h: No such file or directory
utils.c:24:20: error: unistd.h: No such file or directory
utils.c:25:19: error: ctype.h: No such file or directory
utils.c:26:42: error: netinet/in.h: No such file or directory
utils.c: In function ‘lamont_hdump’:
utils.c:44: warning: implicit declaration of function ‘printf’
utils.c:44: warning: incompatible implicit declaration of built-in function ‘printf’
utils.c:54: warning: implicit declaration of function ‘ntohs’
utils.c: In function ‘printmac’:
utils.c:96: warning: incompatible implicit declaration of built-in function ‘printf’
utils.c: In function ‘mac_to_string’:
utils.c:101: warning: implicit declaration of function ‘snprintf’
utils.c:101: warning: incompatible implicit declaration of built-in function ‘snprintf’
make: *** [utils.o] Error 1
rick@Security-tm-LT:~/Tools/wifi/hotspotter-0.4/src$

---

### Post by nutz on 2007-11-02
+1

Is there a way to install this so it will work with any wireless nic?

---


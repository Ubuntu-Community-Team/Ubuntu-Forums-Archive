---
title: "Bahamut server compile error"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Foxkit on 2011-04-20
well um... hi... Well, I wanted to actually dive into some of the deeper parts of ubuntu, and also being a regular Blender user I wanted to try and keep up with the latest versions. So just to get some practice I picked a random source and happen to get Bahamut, an IRC server. the ./config works fine, the problem lies with the make command, I end up getting this error.

```
Building src
make[1]: Entering directory `/usr/local/src/bahamut-1.8.9/src'
gcc -g -O2 -Wall -fno-strict-aliasing -I../include -c blalloc.c
In file included from blalloc.c:9:0:
../include/struct.h:52:51: fatal error: openssl/rsa.h: No such file or directory
compilation terminated.
make[1]: *** [blalloc.o] Error 1
make[1]: Leaving directory `/usr/local/src/bahamut-1.8.9/src'
Building doc
make[1]: Entering directory `/usr/local/src/bahamut-1.8.9/doc'
make[1]: Nothing to be done for `build'.
make[1]: Leaving directory `/usr/local/src/bahamut-1.8.9/doc'
Building tools
make[1]: Entering directory `/usr/local/src/bahamut-1.8.9/tools'
gcc  -I../include -c convert_conf.c
In file included from convert_conf.c:20:0:
../include/struct.h:52:51: fatal error: openssl/rsa.h: No such file or directory
compilation terminated.
make[1]: *** [convert_conf.o] Error 1
make[1]: Leaving directory `/usr/local/src/bahamut-1.8.9/tools'
******************************************************************************
* For help with bahamut, please refer to http://bahamut.dal.net/             *
* If you encouter serious security related bugs, please mail coders@dal.net  *
* For other bug reports and inquiries, please mail dalnet-src@dal.net        *
* Thank you for choosing Bahamut!  - The DALnet coding team                  *
******************************************************************************
```

Normally I would go to the the listed site for help but I also tried to compile Visual Boy Advance for the heck of it and the same error popped up. 
Infomation that might be of use.
I got a little ahead of myself and upgraded to 11.04 Natty Narwhal beta.
I'll provide more information if I can.
Could anyone give me some help with this?

---


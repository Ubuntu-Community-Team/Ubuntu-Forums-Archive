---
title: "make blows up on libv4l-0.5.0"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-10-28
What went wrong? Do I need to use sudo and if I do, will it make the operations of this video lib useable only by root? And, is that O.K.?

mark@Lexington-19:/usr/lib/libv4l-0.5.0$ make
make -C libv4lconvert V4L2_LIB_VERSION=0.5.0 all
make[1]: Entering directory `/usr/lib/libv4l-0.5.0/libv4lconvert'
cc -c -MMD -I../include -I../../../../linux/include -fvisibility=hidden -fPIC -g -O1 -Wall -Wno-unused -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4lconvert.o libv4lconvert.c
libv4lconvert.c:737: fatal error: opening dependency file libv4lconvert.d: Permission denied
compilation terminated.
make[1]: *** [libv4lconvert.o] Error 1
make[1]: Leaving directory `/usr/lib/libv4l-0.5.0/libv4lconvert'
make: *** [all] Error 2

---

### Post by aroach31291 on 2009-10-28
Nope that isn't the problem.

Make sure that you extracted the tarball with the same user you plan on running make.

EDIT: I just noticed you are extracting the source in /usr/lib, why? Do all of this in your home directory or in /usr/src if you root. For example:

cd ~
tar xvf package
cd package
./configure
make
sudo make install

Then there is probably no reason to keep the source so you could just remove it.

---

### Post by Mark_in_Hollywood on 2009-10-28
That seemed to do the trick. Thanks.

---


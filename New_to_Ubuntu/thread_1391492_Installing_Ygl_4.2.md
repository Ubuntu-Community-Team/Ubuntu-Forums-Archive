---
title: "Installing Ygl 4.2"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by thebigeis on 2010-01-26
For this open source software to work ([http://www.siebel-research.de/people_tracking/reading_people_tracker/](http://www.siebel-research.de/people_tracking/reading_people_tracker/)), it says I must have all of the necessary packages first. Ygl 4.2 is one of these, yet when I try to make it, it comes up with an error. 

 make
rm -f ygl.o unshared/ygl.o
gcc -m32 -c   -I.     -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L 				-D_POSIX_SOURCE -D_XOPEN_SOURCE 				-D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 				  				  -DFUNCPROTO=15 -DNARROWPROTO   -DOGL -DX11 -DGSvs -DDOUBLEBUF -DMULTIBUF    	-g -O2 -fno-strict-aliasing -g  ygl.c -o unshared/ygl.o
In file included from ygl.c:17:
header.h:31:21: error: GL/glu.h: No such file or directory
make: *** [ygl.o] Error 1

Obviously, the error has to do with no glu header file existing, but I do not know how to go about fixing this. Im not good with Linux and would very much appreciate any guidance! Let me know if you need more information.

---

### Post by cariboo on 2010-01-28
I'm not sure, but does installing libygl4-dev from the repositories help?

---


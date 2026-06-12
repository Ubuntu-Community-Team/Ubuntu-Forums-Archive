---
title: "Xmovie error"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by mkapitur on 2010-10-14
Hi everyone!
I have following error while compiling xmovie. Could you please help me to fix it? Thanks!

[I]student@student-desktop:~/Desktop/lammps/lammps-2Oct10/tools/xmovie$ make
gcc -c -O2 -finline-functions -g -DMISSINGDEFS -D_POSIX_SOURCE -DUSEPRIVATE -DINCL_FLOAT -Wimplicit -Wunused -Wmissing-prototypes  xmovie.c
xmovie.c:15:26: error: X11/Xaw/Form.h: No such file or directory
xmovie.c:16:31: error: X11/Xaw/Cardinals.h: No such file or directory
xmovie.c: In function ‘main’:
xmovie.c:153: error: ‘ZERO’ undeclared (first use in this function)
xmovie.c:153: error: (Each undeclared identifier is reported only once
xmovie.c:153: error: for each function it appears in.)
make: *** [xmovie.o] Error 1[/I]

---


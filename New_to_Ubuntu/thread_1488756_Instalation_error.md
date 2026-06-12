---
title: "Instalation error"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Xavierdri on 2010-05-20
Can some one please help I want to install pcb-20050315 at first there was a file missing Xaw athena widget any how got that so now when I do ./configure it comes up with this at the end is this correct? 


   Athena Widgets Based GUI: yes
   GTK+ Based GUI:           no
   GTK+ library version:     
   GLIB library version:     
   dmalloc debugging:        no
   ElectricFence debugging:  no
   CPPFLAGS:                  -DPCBLIBDIR=\"${prefix}/share/pcb\" -DPCBTREEDIR=\"${prefix}/share/pcb/newlib\"
   CFLAGS:                   -g -O2 -Wall  
   LIBS:                     -lXaw -lXpm -lXmu -lXt -lXext -lSM -lICE -lX11 -lm     

Now when I do make I get this

make[4]: *** [djopt.o] Error 1
make[4]: Leaving directory `/home/xavier/Downloads/pcb-20050315/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/xavier/Downloads/pcb-20050315/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/xavier/Downloads/pcb-20050315/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/xavier/Downloads/pcb-20050315'
make: *** [all] Error 2
xavier@xavier-desktop:~/Downloads/pcb-20050315$ 

So now what am I doing wrong? Sorry for being a nuisance but i have read 170 pages found a hell of a lot of interesting info but nothing on this problem.

Regards Xavier PS how will I know when I have a new post? Man I do sound stupid don't I :)

---

### Post by cariboo on 2010-05-22
Is there a reason why you're trying to install such an old version? The version in The repositories is 20091103-2.

---


---
title: "Toshiba A15-S1292"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by idom on 2009-10-25
I was using ubuntu 8 before and my toshiba satellite A15-S1292 was working properly. My HDD crashed and I bought a new hdd and have installed ubuntu 9.04 now. 

Previously I was able to change my screen's brightness with Fn+F6/F7 keys with ubuntu 8. However, now that does not seem to be working properly. 

what am I suppose to do ?

-Cheers
Idom

---

### Post by lisati on 2009-10-28
Which Ubuntu 8 are you using? 8.04 or 8.10?

---

### Post by anewguy on 2009-10-28
It's possible a video driver changed or something along those lines.  Post back the output of  lspci | grep VGA (that's a piping symbol - it's above the "\" on my keyboard).

Dave :)

---

### Post by idom on 2009-10-30
Output as follows
idom:~>  lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
idom:~>





> **anewguy said:**
> It's possible a video driver changed or something along those lines.  Post back the output of  lspci | grep VGA (that's a piping symbol - it's above the "\" on my keyboard).

Dave :)

---


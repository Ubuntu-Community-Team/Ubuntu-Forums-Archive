---
title: "Dell Xps M1330 Ubuntu 8.10 wit kernel 2.6.28 intel drm"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by trinox6 on 2009-05-22
ok....................i am absolutely a nube.........i finally got the intel drm source kernel 2.6.28 working on my dell xps m1330 ............well that ws a relife and then i check again and i just found out even after all that i stil dnt have a shred of graphics worth working with..compiz refuses to start................desktop effects refuses to wrok..............i
Xorg -configure
on a root shell terminal.................
i added other important options as needed so now...am desperate......i cnt download The latest jaunty ubuntu version..................cuz mynet is well abit slow paced on that side...
to am stock wit this....even after installing the latest drm version and xfree86 driver from intel nothing seems to work..any1 pls help

---

### Post by trinox6 on 2009-05-22
and now i want to also apply the [http://intellinuxgraphics.org/download/2008Q4-rc4/2008q4-kernel-against-2.6.28.patch](http://intellinuxgraphics.org/download/2008Q4-rc4/2008q4-kernel-against-2.6.28.patch) patch but i don't know how............wud really love some directions on how to do this.................pls :)

---

### Post by trinox6 on 2009-05-22
i modprobe agpgart but it keepps telling me the module does not exits...............do i need to copy agpgart.o file into any other directly.............like /usr/lib/xorg/modules............................
pls help

---

### Post by trinox6 on 2009-05-23
hello wts dis.............................can;t anyone help me out........................am begging here.........wts wrng?
is this a community or what?

---

### Post by NESFreak on 2009-05-23
Its a bit complicated to explain all that at once.

First of all, didn't ubuntu just ran out of the box? Dell even ships m1330 laptops with ubuntu in some countries. Never had a serious problem with mine.

If like you said you really are a n00b it might as well be smart to keep away from trying to compile a complete kernel yourself.

Btw i [found this interesting website, hope it helps]("http://www.google.nl/search?q=ubuntu+compile+kernel+howto")

PPS ow please write your vowels. please come on man dude. plx jst wrt thm.

---

### Post by trinox6 on 2009-05-23
lol............sorry mybad.................mybd habit i guess.
ya am a noob in a sense......to say but i actually successfully build the kernel myself but stil the agpgart wasn't working but i guess it was a kernel,maybe that was one of the things the patch solves.........but thanks for the link thoguh

---

### Post by trinox6 on 2009-05-23
funny enough..without knowing i download the ubuntu jaunty iso file.....but from what i have read it seems thats another heep of extra-large issues for us using the intel gma .....so
i doubt i will be upgrading to it soon

---


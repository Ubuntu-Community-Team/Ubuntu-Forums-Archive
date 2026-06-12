---
title: "What to do about disabled NX capabilities."
date: 2010-12-26
forum: New to Ubuntu
---

### Post by OldBoy44 on 2010-12-26
I entered the virtual console for the first time today where ubuntu reported that my CPU was from family 15, model 4 with NX capabilities and had been configured to disable the capability. Please enable this in your Bios.
My CPU is an Intel Pentium 4 (Presscott) 3.00 GHz with 1 core and 2 threads.

I read a little about it here - [http://en.wikipedia.org/wiki/NX_bit](http://en.wikipedia.org/wiki/NX_bit)

The problem is, I haven't a clue as to how to rectify this - What should I do?
Is this important? My old refurbished computer has been operating reasonably in the last 15 months.

Any comments would be gratefully received.

Cheers,  :)

---

### Post by davidmohammed on 2010-12-26
in terms of ubuntu - [this]("https://wiki.ubuntu.com/Security/Features#nx") is what the NX bit means.

You could enable it if you wish by enabling it in your bios - but unless you are using PAE or ubuntu server - ubuntu will not use it to "boost" security.

---

### Post by admiralspark on 2010-12-26
The NX bit isn't very useful in a home environment on a linux machine anyway, and it's not supported except on the server kernel or a PAE kernel, neither of which are default on Ubuntu.

---

### Post by OldBoy44 on 2010-12-26
Thanks David and admiralspark,

I can assume then that I could just leave things as they are! I have followed quite a few other threads on this issue and there did not appear to be an easy solution.
Also I couldn't see in my Bios where this was switchable.

Thanks again,  :)

---


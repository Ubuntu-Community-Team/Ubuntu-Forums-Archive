---
title: "(initially) no luck with gutsy 7.10, linksys WUSB11 2.6, and Belkin F5D7050"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by semenzato on 2008-03-14
Howdy,

I've had no luck with either the Linksys WUSB11 v2.6, or the Belkin F5D7050 (B, which
I believe is model 3000).  I don't expect anybody to be able to fix my problem
unless they can fix the drivers, as I think the problem is there.  (Of course I will
be glad to be proven wrong).  I am reporting these bugs here in case anybody
can use this information.  Contact me for more info.

I've tried the WUSB11 first on ubuntu 7.10 gutsy server installed on a 5-year
old PC with AMD CPU.  It worked charmingly.

Unfortunately the power supply in the box gave up and I figured it was
a signal that I should buy a new box.  I got a $320 pc from Alphapcstore
with a Athlon 64 3800+ and Asus M2N-MX SE mobo with 1g RAM.
I am afraid to say that the exact same installation resulted in a non-working
wireless adaptor.  When I plug in the adaptor, I get these messages:

at76c503.c: 2522: assertion dev->istate == INIT failed
at76c503.c: 2492: assertion dev->istate == SCANNING failed

WHAT!!!!

Well I'll be darned.  I still get these messages, but now the WUSB11
is working.

Grrr.  I spent hours on this.  Never mind.  No wonder Linux on the
desktop is not catching up that quickly.

The F5D7050 was giving me similar problems---suspicious
kernel messages, and the output of iwconfig looked fine, except
there was no connection.  The router was found, but signal strength
was zero and no data was transmitted.

In retrospect, I think it's the router's fault (a pre-N Belkin).  This
morning my imac couldn't connect either until I power-cycled the
router.  I bet the F5D7050 would work now as well.  But I am not
going to check. :-)  It was hard to realize it was a router issue
because existing connections kept working fine.

The router has misbehaved before and I think that the lesson
here is to get rid of faulty equipment ASAP and not just live
with it.

Thanks for reading my rants!

---

### Post by pytheas22 on 2008-03-15
As a workaround, you could try ndiswrapper.  I don't know that status of your devices with it, but I'm sure a quick search would reveal it.  You might also try searching more extensively to see if anyone else has had similar problems with the same hardware.   Also, turning off encryption on your router could help.

---

### Post by semenzato on 2008-03-16
Thanks, but if you read the entire post, you'll see that the problem was
in the router.  The WUSB11 works fine now.

---


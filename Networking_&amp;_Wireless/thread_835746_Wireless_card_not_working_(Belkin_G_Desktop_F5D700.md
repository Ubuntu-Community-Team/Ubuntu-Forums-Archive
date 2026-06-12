---
title: "Wireless card not working (Belkin G Desktop F5D7000   Ver.4000)"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by leogx on 2008-06-20
My    Belkin G Desktop Card F5D7000 Ver.4000 Wireless Card Will not work in ubuntu any suggestions on how to get this to work??

---

### Post by lisati on 2008-06-20
There are a couple of things we can check. The first is to see if your card is being recognized and anything is happening. One way of doing this from the terminal is:
```
iwconfig
```

---

### Post by leogx on 2008-06-20
i tryed a different card and it worked thank u

---

### Post by SeePU on 2008-07-03
Bump

For anyone trying this same usb dongle (with ver. 4000), try removing any other usb connections (for e.g., a printer that's connected via usb).  I did before boot up and I could scan for networks.  This is even using Debian Testing which uses a similar version of kernel.  (2.6.24).

I was really surprised, to tell you the truth.  I know this is not the best solution and doesn't explain much but it's FYI.  I hope this helps someone.

P.S.  There is another post here somewhere that reports the same 'solution.'  Something about a usb hub.  I wonder if there is some sort of usb conflict that is preventing the (zydas/zd1211-based) adapter starting up.

---

### Post by tbobker on 2008-07-31
Hi,

Im having the same problem....everything seems to work fine except my wireless network card?

What replacement card did you use so that i can get one?

Thanks

---


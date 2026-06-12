---
title: "Weird question about modems"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by TheKingofZZT on 2008-06-09
Hi, I have two computers:

The first is an Ubuntu 7.10 machine, with some variety of data modem. (presumably 56k?)
The second is an old Windows 3.1 laptop, also with a modem. (28.8k) -and no ethernet.

I've been trying to figure out: Is it possible to connect them using the modems and a telephone cord? I'd like to use the laptop as a little thin-client.

Any help appreciated!

---

### Post by Mgiacchetti on 2008-06-09
Well, basically if you want to do this without using your home phone line system, you have to emulate the dialtone.

[http://www.jagshouse.com/modem.html](http://www.jagshouse.com/modem.html) 

That page should get you started, if you are savvy with wiring diagrams, you should have no problems with this.

---

### Post by TheKingofZZT on 2008-06-09
Thanks! The laptop seems to get a dialtone (it will try to dial numbers, though it also semms to try even if there is no dial tone.)

I'm a bit confused about how to allow the Linux box to accept connections/logins on the modem though, does anyone know how to set it up to do that?

Thanks again.

---

### Post by TheKingofZZT on 2008-06-09
If I type
```
ATX3&C0
ATDT555
```
into the Windows terminal it seems to dial even if there is no dial tone.

I installed minicom via Synaptic, but I can't seem to figure out how to make it talk to my modem, or have the modem auto accept connection (like the connection was tty2 or something)

The modem is "Communication controller: Agere Systems LT WinModem" if that helps.

---


---
title: "Modem driver restart"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by RxRated on 2007-10-26
I have a Toshiba laptop running xp and feisty.  I use a dialup account at work.  My modem is a smartlink winmodem and I am using the sl-modem daemon drivers.  The only ppp dialer I can get to work is kppp.  The modem is detected, but I get the "no carrier" error when I try to dial.
If I restart the modem drivers by running "sudo /etc/init.d/sl-modem-daemon restart" then re-open kppp the modem will connect fine.  I need to do this every time I boot up feisty.

Is there a way to have that script automatically run each time I boot-up?

I tried a fresh install of Gutsy, but had WAY too many problems to stick with it for now.(Wireless locked up the kernel on connect, ati display wouldnt work right etc).

Thanks

---

### Post by RxRated on 2007-10-27
*Bump*  Anyone?

---


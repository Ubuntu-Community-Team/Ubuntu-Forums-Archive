---
title: "Can see the available networks, unable to connect"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by dcapurro on 2007-04-22
I just installed Feisty. My USB adapter D-Link DWL G-122 ver C1 seems to be working because I can detect the available networks. The thing is that I can't connect to anyone even if they are unsecured ones.

Does anyone know how to fix this?

thanks

---

### Post by ziadoz on 2007-04-22
I had the same issue with my wireless card on my laptop. I compiled a new kernel (2.6.20) and it seems to work now. I'm assuming that it is kernel related, as I couldn't access my wireless from any network apps (nm-applet, wicd, wifi-radar etc), now I can.

---

### Post by dcapurro on 2007-04-22
> **ziadoz said:**
> I had the same issue with my wireless card on my laptop. I compiled a new kernel (2.6.20) and it seems to work now. I'm assuming that it is kernel related, as I couldn't access my wireless from any network apps (nm-applet, wicd, wifi-radar etc), now I can.

Sorry, I'm new to linux. How do I compile a new Kernel?, How do I know which one do I have now?
Thanks

---

### Post by ziadoz on 2007-04-22
I followed this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

You should use 2.6.20.7 which is stable though I guess.

---

### Post by dcapurro on 2007-04-22
Thanks. Does this work on 7.04 too? the instructions are for 6.06.

---


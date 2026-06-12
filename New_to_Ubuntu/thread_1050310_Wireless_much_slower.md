---
title: "Wireless much slower"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by jlott on 2009-01-25
i have just put ubuntu 8.10 on my acer aspire 1 netbook, and after hours of terminal i finaly managet to get the wireless working, only problem is that it is a lot slower than my previos operating system. i can no longer get wireless in my bedroom and i could before.

Please help

Many thanks

Joseph

---

### Post by pi.boy.travis on 2009-01-25
Check out System>Administration>Hardware Drivers  If you have not already done so.  If there is one there, try the proprietary driver.  They often provide better functionality as far as WLAN is concerned.

It's sad. . . but true. . .

---

### Post by jlott on 2009-01-25
i have got two (none activated)

support for 5xxx series of atheros 802.11 wireless LAN cards

and

support for atheros 802.11 wireless LAN cards

which one do i activate?

---

### Post by pi.boy.travis on 2009-01-25
> **jlott said:**
> i have got two (none activated)

support for 5xxx series of atheros 802.11 wireless LAN cards

and

support for atheros 802.11 wireless LAN cards

which one do i activate?

I would use trial and error to see which one provides better performance.  You can deactivate the driver later if you wish.

---

### Post by jlott on 2009-01-25
the first one (5xxx series...) connects but does not make a differnce

the second one says "this driver was just disabled, but still in use" when a activate it

---

### Post by pi.boy.travis on 2009-01-25
> **jlott said:**
> the first one (5xxx series...) connects but does not make a differnce

the second one says "this driver was just disabled, but still in use" when a activate it


In that case you will have to restart to disable the driver.

---

### Post by jlott on 2009-01-25
i have done that, it just asks me for my password, then says again "this driver was just disabled, but still in use"

---

### Post by pi.boy.travis on 2009-01-25
Hmm. . . if the Linux driver isn't working for you, you may get better results from using the windows driver if you have the means.  Check out:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hope this helps!

---


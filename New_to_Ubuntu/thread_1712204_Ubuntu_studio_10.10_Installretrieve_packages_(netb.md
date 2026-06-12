---
title: "Ubuntu studio 10.10 Install/retrieve packages (netbook-usb)"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by juancho2374 on 2011-03-22
Hi

I´m needing right now ubuntu studio on my netbook, and I don´t have an internal nor external dvd unit, so I just can´t install it normally with the burnt ISO. Anyway I found out how to do it with the Unetbootin app, and the "cannot find cd fix" (cdrom-detect/try-usb=true) because it can´t be done otherwise... maybe you should check that yourselves and do it for us newbies... :) it would be really helpful
The thing here is that I can´t access an ethernet cable in order to retrieve the packages from the web... this installer doesn´t recognize my wifi card, Is ther any way of doing it?

Thanks:popcorn:

---

### Post by cariboo on 2011-03-22
It would help if you told us what wireless chipset your system has. If you don't know, open an Applications->Accessories-Terminal and type:

```
lspci > hardware.txr
```

the above command will create a text file called hardware.txt that you can transfer to a system with a working network connection.

---

### Post by pgmer6809 on 2011-03-22
> **juancho2374 said:**
> Hi

I´m needing right now ubuntu studio on my netbook, and I don´t have an internal nor external dvd unit, so I just can´t install it normally with the burnt ISO. Anyway I found out how to do it with the Unetbootin app, and the "cannot find cd fix" (cdrom-detect/try-usb=true) because it can´t be done otherwise... maybe you should check that yourselves and do it for us newbies... :) it would be really helpful
The thing here is that I can´t access an ethernet cable in order to retrieve the packages from the web... this installer doesn´t recognize my wifi card, Is ther any way of doing it?

Thanks:popcorn:

Is your system new enough to boot from a USB stick?
If so there are instructions for creating a linux system on a USB stick (or you can buy one cheap) and then you can boot and go from there.
pgmer6809

---


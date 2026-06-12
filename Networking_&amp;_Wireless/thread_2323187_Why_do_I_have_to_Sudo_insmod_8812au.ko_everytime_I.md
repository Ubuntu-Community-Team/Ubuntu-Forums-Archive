---
title: "Why do I have to Sudo insmod 8812au.ko everytime I start my computer"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by nvthao147 on 2016-05-03
I have a problem, every time when  I start ubuntu I have to run Sudo insmod 8812au.ko to use wifi USB. I really want my usb wifi autorun. I am using Wicd network manager and ndiswrapper. Please help me.
Sorry about my english.

Thank you so much

---

### Post by chili555 on 2016-05-03
The only way you'd need to insmod a .ko is if you compiled from source. Did you?

Also, 8812au is not a ndiswrapper driver. Why are you using ndiswrapper?

Finally, did you remove the default Network Manager, that works rather well, to replace it with Wicd, which is no better and perhaps not as good? If you didn't remove NM, are BOTH running and competing?

:confused: :confused:

---


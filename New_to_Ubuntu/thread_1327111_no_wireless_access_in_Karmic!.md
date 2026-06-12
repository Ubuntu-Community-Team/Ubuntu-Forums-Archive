---
title: "no wireless access in Karmic!"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by kapi on 2009-11-15
Help please, yesterday I upgraded to Karmic and found that there is no wirless access.

It worked fine in jaunty but not in Karmic.

Any help would be very much appreciated

Thanks

---

### Post by mathfreak123 on 2009-11-15
It might be that you don't have a driver for your card. If your ethernet connection works, I suggest using it and then checking System > Administration > Hardware Drivers. You might have a driver for your card.

I also had the same problem, too, with my Compaq laptop. Turned out my laptop had a Broadcom wireless card, so I had to use ndiswrapper to get around it. Here's a link to the guide on ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

In any case, can you open up a terminal (in Applications > Accessories > Terminal), type in lshw, and post what you get here?

---

### Post by kapi on 2009-11-15
thank you so very much. As stated the drivers were there and so i installed them.

Thanks again for your help

---


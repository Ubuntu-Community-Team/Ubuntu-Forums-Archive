---
title: "D-Link WNA-1330 problem"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by pumpkinpapa on 2008-05-03
I have a Dell Inspiron 1100 with a D-Link WNA 1330 pcmcia wireless g adaptor. It worked fine in 7.10 but has issues in 8.04. I've done the upgrade from 7.10 to 8.04 rather than the clean install this time.

In 2.6.24-16-generic it is not detected and the device manager is broken. However in 2.6.22-14-generic and 2.6.22-14-386 the device manager works and the card is detected. I can connect to my network and internet, just not in 2.6.24-16-generic.

I've tried iwconfig and the card is there but I need to get hardware drivers to see it and have the hardware info work  first (I think)

---

### Post by pumpkinpapa on 2008-05-08
Never mind, I fixed it, I'm not sure how but it is working now for the most part.

Though from time to time the driver for the Atheros chipset defaults to "not in use" and so Wicd can't see the card. Disabling and enabling the driver fixes it.

Now to get the driver to default to "in use".

---


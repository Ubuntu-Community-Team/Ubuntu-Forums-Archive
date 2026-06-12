---
title: "wifi connection and rt2400 driver"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by spaceman on 2005-03-30
Hi everyone,

I have a problem  setting up my wifi connection.
I have a PC54G2 wifi card from MSI and I have tried to install the rt2400 driver.

The first steps seem OK (no errors on make and make install).
I can find a rt2400.ko file in ..../drivers/net/wireless.

Then I make *alias ra0 rt2400*
then *modprobe -c|grep rt2400* -> Ok I have something at the screen

Finally *ifconfig ra0* and it goes wrong !!
I have an error message : *Peripheral not found* !

Has anybody an idea ?

---

### Post by roblubbers on 2005-07-10
did you get the latest driver raball from sourceforge?

---


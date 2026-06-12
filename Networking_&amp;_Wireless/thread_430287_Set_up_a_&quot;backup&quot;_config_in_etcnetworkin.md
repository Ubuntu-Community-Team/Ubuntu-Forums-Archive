---
title: "Set up a &quot;backup&quot; config in /etc/network/interfaces ?"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by jbm222 on 2007-05-02
I have an RT2500 chipset in my wireless card, so I'm using the linux native drivers.  When I'm at home, I'm using WPA, so /etc/network/interfaces has that interface setup to connect to my home network (with a static IP).  

This works great, however, it's a pain to reconfigure everything manually when I'm away from home.  Is there a way I can say:  try this configuration, and if that network isn't there, revert to default auto settings?

---

### Post by wirawan0 on 2007-10-04
(I know this thread is so old, but maybe this writing is useful for anybody else.)

I wonder if you know about network-admin tool. This is available in Ubuntu 7.04 (I don't knot about the earlier versions). From command line, you can type "gksu network-admin". If the network manager applet (nm-applet) is enabled, then you can use "manual configuration" to invoke the network-admin program.

Additionally, Ubuntu now has wireless roaming mode. I don't quite like it yet, but it seemed to be able to pick up SSID automatically as it goes. But I don't know if this would also provide a way to set the WPA/WEP key for certain SSIDs.

---

### Post by kevdog on 2007-10-04
Check out the manual pages for interfaces.

man interfaces

I think I remember seeing something like this in the manual.  Im not in front of a linux box right now so sorry I cant help you.

Correction
Take a look at this link --
[http://linux.die.net/man/5/wpa_supplicant.conf](http://linux.die.net/man/5/wpa_supplicant.conf)

---


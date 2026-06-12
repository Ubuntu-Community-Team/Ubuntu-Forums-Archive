---
title: "Wireless won't start when laptop starts???"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by distortedecho on 2007-12-20
Hi again

Everytime I boot up my laptop, I have to "Maually configure" my wireless network.
This involves clicking on the network icon in the system tray and selecting manual configuration. Then selecting my profile and then going through the terminal to restart with this command:

/etc/init.d/networking restart

How can I set up ubuntu to start up with my wireless network all ready working?????

Please help.

Thanks

---

### Post by spd106 on 2007-12-20
I would recommend eschewing network-admin on Ubuntu 7.10 and instead configure the network settings directly in the /etc/network/interfaces file.

If you need help, especially with WPA, then have a look at the Howto Wireless Security sticky.

---

### Post by now-new on 2007-12-20
what make is your wireless card?
you can check and you could modify the interfaces file /etc/network/interfaces so you'll have it automatically or check what you can do if its bcm43xx its supported now with ubuntu gutsy

---

### Post by distortedecho on 2008-01-01
Hi,

I've all ready setup my wireless in the interfaces as per the tutorial.
Why won't it start automatically?

---


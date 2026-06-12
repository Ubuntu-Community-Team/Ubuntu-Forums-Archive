---
title: "Mobile phone (Nokia 6280 etc..) and UMTS / 3G"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by knubbe on 2006-12-12
Hi,

Anyone who've managed to connect to UMTS (3G) using a phone in ubuntu? If so, anyone who can point me to a tutorial/howto?

I have a Nokia 6280 + edgy.

Cheers

---

### Post by knubbe on 2006-12-12
> **knubbe said:**
> I have a Nokia 6280 + kubuntu breezy badger.
My bad. Im using edgy, not breezy.

---

### Post by alanfranz on 2006-12-12
The provided USB cable seems to crash the Linux kernel, either at connect (2.6.18 kernels) or at disconnect (2.6.17).

I do use the very same phone via Bluetooth to connect to the internet (provider is Tre, Italy). I could point you to a very good tutorial but it's in italian :-(

there's a pretty good tutorial on the ubuntu wiki BTW

[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

and on

[http://www.saunalahti.fi/nonn/linux_gprs.html](http://www.saunalahti.fi/nonn/linux_gprs.html)

(it says it's for gprs, but UMTS usually works the very same way, it's the phone who will pick the fastest available network).



but you'll have to experiment yourself; also, you'll need to know the APN from your provider and/or if you need to enter any username or password; you may even need to create a data profile with your settings on the phone and set it as the default profile.

After paring the device and getting the rfcomm0 working ok, you might even take a look at gnome-ppp or similar utilities; they may work very well and they're easy to configure.

---

### Post by knubbe on 2006-12-12
> **alanfranz said:**
> The provided USB cable seems to crash the Linux kernel, either at connect (2.6.18 kernels) or at disconnect (2.6.17).

I do use the very same phone via Bluetooth to connect to the internet (provider is Tre, Italy). I could point you to a very good tutorial but it's in italian :-(
My provider is also Tre (Sweden though). It would be great to have a look at that italian tutorial, and i'll babelfish it.

Thanks for your reply. I'll also have a look at the other links you sent.

---

### Post by alanfranz on 2006-12-13
[http://3v1n0.tuxfamily.org/blog/informatica/linux/connessione-gprsedgeumts-su-ubuntu-con-nokia-6630-via-bluetooth/](http://3v1n0.tuxfamily.org/blog/informatica/linux/connessione-gprsedgeumts-su-ubuntu-con-nokia-6630-via-bluetooth/)

---

### Post by magicfab on 2007-01-26
Unfortunately lots of manual intervention is required to configure these cards. Your best bet is to formally complain about official support for Linux directly to your provider and to Nokia. If enough people do that, they will probably provide official .deb packages for Ubuntu and other packages for other distributions or better yet, have them commercially packaged and offered by Canonical or else.

---

### Post by alanfranz on 2007-02-02
I don't think there's so much manual intervention required. Configuring them on Windows, WITHOUT installing all those filthy packages which pollute your system, require quite a lot of manual configuration as well. And most commands are not Nokia-specific: I've been able to use the same connect/disconnect scripts with other mobile phones (SE k608i) as they're mostly gsm/gprs specific, not Nokia specific.

---


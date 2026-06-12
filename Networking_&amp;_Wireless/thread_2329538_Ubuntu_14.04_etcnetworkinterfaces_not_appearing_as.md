---
title: "Ubuntu 14.04 /etc/network/interfaces not appearing as expected."
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by Aphexlog on 2016-07-02
i am using Ubuntu 14.04 and trying to configure a static IP via terminal... however this is what the interfaces directory presents to me:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
-----------------------

it shows me that instead of showing the current configuration.

any suggestions as to why would be very helpful

Thanks

---

### Post by steeldriver on 2016-07-02
If you are running a desktop version of Ubuntu, then your network configuration will be done by NetworkManager - you can set a static interface there using the GUI (IPv4 Settings -> Manual)

---

### Post by Aphexlog on 2016-07-02
oh, so it disables the directory configurations on the desktop version?

---

### Post by steeldriver on 2016-07-02
It doesn't "disable" it as such - they are different services, with different focuses (NetworkManager makes it relatively easy to support roaming for example - handy for laptops / mobile devices)

You are still free to configure interfaces via /etc/network/interfaces if you wish - by default, NetworkManager will then ignore them (consider them to be "unmanaged")

Or if you want to go "old school" you can disable - or even uninstall - NetworkManager

---


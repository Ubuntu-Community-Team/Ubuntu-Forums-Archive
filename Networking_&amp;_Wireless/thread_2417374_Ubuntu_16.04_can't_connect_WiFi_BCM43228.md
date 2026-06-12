---
title: "Ubuntu 16.04 can't connect WiFi BCM43228"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by modomobo on 2019-04-22
Trying to connect to WiFi on an Acer Laptop with a BCM43228 802.11a/b/g/n [14e4:4359].

I can see WiFi networks and connect to one, but trying at a friend's house it doesn't allow me to connect to another.

The **Authentication Required by Wi-Fi network** prompt keeps coming up, even if I enter the correct password.

I've tried the following with sudo:

```

apt-get purge bcmwl-kernel-source
apt update
update-pciids
apt install firmware-b43-installer
apt autoremove
reboot
apt install bcmwl-kernel-source
reboot
```

No joy.

Any suggestions to get this working?

Thanx

---


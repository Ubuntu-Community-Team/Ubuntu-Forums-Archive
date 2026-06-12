---
title: "I can't connect to the web!"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by gem1849 on 2006-10-02
I have a HP NX9600 with internal 802.6b wireless card. I installed Unbuntu today and I can't connect to the web. I tried to load the drivers from the HP disk but it won't let me. How do I connect & how do I install any programs?

---

### Post by keithjr on 2006-10-03
Your HP disk will not work because the executables there will not run outside of windows.  

A quick search of the interweb found this:
[http://ccsd.msoe.edu/faq/linux/Ubuntu.jsp?IDFaq=223](http://ccsd.msoe.edu/faq/linux/Ubuntu.jsp?IDFaq=223)

However it is not very complete.  Do your own searching for setting up a wireless network with ubuntu.

---

### Post by az on 2006-10-03
> **gem1849 said:**
> I have a HP NX9600 with internal 802.6b wireless card. I installed Unbuntu today and I can't connect to the web. I tried to load the drivers from the HP disk but it won't let me. How do I connect & how do I install any programs?

It has a broadcom chipset.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-d0946e95811e2999580f6073e165fa66c3709f01](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-d0946e95811e2999580f6073e165fa66c3709f01)

To simplify, just read the section called 1.2.2.2. "Firmware Packages"

download and install the bcm43xx-firmware_1.3-1ubuntu1_all.deb package and then reboot.  Your wireless should then work.
The firmware is not licenced for distribution by the people who make the chipset, which is why you have to get it yourself.

```
wget -c http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb
```

```
sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb
```

---


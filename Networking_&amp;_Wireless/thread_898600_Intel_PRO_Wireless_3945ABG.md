---
title: "Intel PRO Wireless 3945ABG"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by lgp171188 on 2008-08-23
I have a HP dv9704tx laptop. I ordered Ubuntu 8.04 cd from Canonical as soon as it was released. I installed it on my laptop and it detected my Intel PRO Wireless 3945 ABG and installed restricted drivers for it. So I was able to use wireless. Then, when Ubuntu 8.04 dvd was out, I installed many software packages from it.

After some time, I reinstalled Ubuntu 8.04 from the DVD but it no longer detects and installs drivers for the same wireless adaptor how much ever times I install it again and again. :confused:

What could be the problem and how to rectify it? Or is it a bug?

P.S. Ubuntu 7.10 detects and installs drivers for the same and it works perfectly:)

---

### Post by lgp171188 on 2008-08-23
I think it could be due to the kernel update in Ubuntu 8.04.1 (from which I installed now). I installed from 8.04 LiveCD and it worked. I think the kernel update has broken the driver support:)

---

### Post by pfdevil on 2008-08-23
How sure are you that the drivers for the card is not installed?

---

### Post by lgp171188 on 2008-08-23
ifconfig -a does not show any wireless devices. network-admin too doesn't. Ubuntu showed and installed restricted drivers only for my Nvidia GeForce 8600 M GS, nothing more :(

---

### Post by pfdevil on 2008-08-23
Hey try following this to get it up again.

[http://kryptoz.wordpress.com/2008/05/02/install-ipw3945-intel-prowireless-3945abg-on-debian/]("http://kryptoz.wordpress.com/2008/05/02/install-ipw3945-intel-prowireless-3945abg-on-debian/")

---

### Post by lgp171188 on 2008-08-23
Does the 2.6.24 version of the kernel not support ipw3945?

---

### Post by pfdevil on 2008-08-23
Hey sorry forgot that the ipw3945 is deprecated. 

Rather follow this link and read installation details.

[http://intellinuxwireless.org/?n=Info]("http://intellinuxwireless.org/?n=Info")

---


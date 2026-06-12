---
title: "Toshiba Satellite A215-S7437"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by supertails on 2008-01-07
I have Ubuntu 7.10 Gutsy Gibbon and I have a Toshiba Satellite A215-S7437. How to I get wireless to work on the computer? Do I need to give more info on my computer?

---

### Post by amo-ej1 on 2008-01-07
Could you open a a console an paste the output of the following commands: lspci and iwconfig (the first one lists the pci devices in your system, the second one lists the configuration of the wireless devices, if detected).

---

### Post by supertails on 2008-01-07
I'll test it out. Thanks.

---

### Post by edgeseraph on 2008-01-16
This thread has my interest as well.
The wireless adapter is internal, but uses USB. It is a REALTEK RTL8187B
I've tried using the windows-to-linux driver wrapper: ndiswrapper
ndiswrapper doesn't automatically detect the wireless device when i try to load the .inf file
when i try to do it manually, ubuntu doesn't seem to pick up on the existence of the device.

---

### Post by ponychaser on 2008-01-17
try this link:

[http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/](http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/)

---


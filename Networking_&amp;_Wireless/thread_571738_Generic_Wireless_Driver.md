---
title: "Generic Wireless Driver"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by kcihtred2 on 2007-10-09
I need a generic wireless driver for my TEW-443PI wireless card, and TEW-452BRP wireless router, also possibly a driver for the ATI Radeon 9250

---

### Post by reckless2k2 on 2007-10-09
if you go to the restricted drivers applet in the administration menu you should have the option at the very least for the ati card. i'm not sure. i think they have one for ati. if not, you have to install ati from the binary. 

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

make sure to pick the right version and always backup xorg.conf before changing it. i think the install does it automatic. 

as far as wireless...is it recognized at all?

what do you get if you do this at the terminal:

```
lspci -v
```

---


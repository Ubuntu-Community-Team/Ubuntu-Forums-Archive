---
title: "wireless on gateway lt 2030 netbook"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by voteforcondit on 2010-12-27
can someone help me out with getting wifi to work on my gateway lt2030

do i need to do it with ndiswrapper? 

the only thing i can find about the wireless card is that it is 802.11B and wifi certified.

thanks

---

### Post by TeoBigusGeekus on 2010-12-27
```
lspci | grep net
```
to find out the model of the wireless card. Post it to us please.

---

### Post by wep940 on 2010-12-27
Also, post the output of lsusb - some laptops have the internal wireless actually connected to the internal USB bus and not the PCI bus - asking for a listing of both PCI and USB *should* show any device.

---


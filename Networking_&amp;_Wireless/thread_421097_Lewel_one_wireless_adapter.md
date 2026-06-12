---
title: "Lewel one wireless adapter"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by RobKan on 2007-04-24
I am a new user of UBUNTU. After installing OS i don't  know  how  to  install the adapter's driver(Lewel one). What should I do?

---

### Post by spd106 on 2007-04-25
I'm not familiar with this brand of wifi card. Could you please open a terminal and post the output of these commands?


```
sudo lshw -class netowork
```
```
iwconfig
```

For pcmcia or cardbus
```
lspci
```
For usb
```
lsusb
```

---


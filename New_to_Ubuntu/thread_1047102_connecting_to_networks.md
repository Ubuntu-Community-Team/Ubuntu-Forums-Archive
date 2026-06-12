---
title: "connecting to networks"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by floatingpoint on 2009-01-22
Does anyone know how to connect to networks wirelessly (with usb adapters) or wired, without Network Manager?

---

### Post by zika on 2009-01-22
**_for wired:_**
make file **/etc/network/interfaces **look like:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```and just type (in terminal):```
 sudo /etc/init.d/networking restart
```

---

### Post by floatingpoint on 2009-01-22
Thanks zika, now I can get online here. One problem down ;)

---


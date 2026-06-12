---
title: "Can't configure route"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by letex on 2008-02-16
Hello and thanks for answering

  I'm trying to connect to my wireless (WEP) lan for acces internet.

 Configuration
 
  adress 192.168.0.138
  netmask 255.255.255.0
  gateway 192.168.0.1

  I'm coneccting with wicd and with Network-manager from gnome and in command line, but always i appear as connected but i can't acces my lan and not internet....but yes in windows!!!

  After connecting with one of manager on top, I do:

 route
 adress                    gateway             netmask                 dev
192.168.0.0                 *               255.255.255.0           wlan0

I've tried to change this gateway with the route command, but I can't!!

 Please, help me to discover the problem. I've probed with network-manager of Gusty, wicd 1.3 and 1.4
 
   Thank you for answering!! in advance!!

---

### Post by jan quark on 2008-02-17
please run these terminal commands and post the output
thank you

```
iwconfig
```
```

sudo iwlist scan
```

```
lspci
```
```

sudo lshw -C network
```

---


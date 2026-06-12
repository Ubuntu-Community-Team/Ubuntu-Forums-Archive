---
title: "how to check wireless network adapter?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by tdietz87 on 2009-05-25
Any way to check what wireless network adapter I am using?
 
any help?
 
I am on a gateway ml 6732 with ubuntu 9.04 and vista 32

---

### Post by Boondoklife on 2009-05-25
try
```
lspci
``` if it is an internal one
or
```
lsusb
``` if it is a usb one

---

### Post by anewguy on 2009-05-25
Actually, do both the lspci and the lsusb, as some laptops internal wireless adapters actually are USB (I just learned this myself a few months ago).

Dave :)

---

### Post by little dave on 2009-05-25
> **tdietz87 said:**
> Any way to check what wireless network adapter I am using?
 
any help?
 
I am on a gateway ml 6732 with ubuntu 9.04 and vista 32


```
iwconfig
```

or 
```
lshw -C net
```

---

### Post by raymondh on 2009-05-25
Here's a guide with possible commands .... good for reference

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw)

Regards,

---

### Post by rob2uk on 2009-05-25
Unless the card has been changed since the laptop was built, it'll be the original LiteOn WN6301L which uses the Realtek 8187B chipset

[http://support.gateway.com/s/Mobile/2008/OasisSR/1015480R/1015480Rcl4.shtml]("http://support.gateway.com/s/Mobile/2008/OasisSR/1015480R/1015480Rcl4.shtml")

---


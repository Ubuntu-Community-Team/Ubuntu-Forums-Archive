---
title: "How do I get wireless to work?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by andrewwg94 on 2009-02-17
I have a Broadcom card on my Compaq Presario V5206OM. I've googled around, but all i found was from old versions of ubuntu. I'm on 8.10. any help appreciated.

---

### Post by andrewwg94 on 2009-02-17
any1?

---

### Post by kspncr on 2009-02-17
Did you get all the updates yet from a wired internet connection?

Please post the output of
```
lspci | grep Broadcom
```

---

### Post by sandyd on 2009-02-17
fyi, its a 

broadcom 54g™ 802.11b/g WLAN with 125HSM / SpeedBooster support

---

### Post by sandyd on 2009-02-17
this might be what your searching for
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=s]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=s") how

assumeing that this shows up in lspci

```

Broadcom Corporation Unknown device 4311

```
most likely it is this tutorial / guide that will work for you

---


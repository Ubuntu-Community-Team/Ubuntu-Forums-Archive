---
title: "Run Drivers Through Wine?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Dmosk on 2009-02-03
Ok fairly new at everything especially wine. I want to install wireless driver on 8.10 from netgear, I want to know if it can be done through wine wine or if i have t have them re-written. ](*,)

---

### Post by Sprut1 on 2009-02-03
> **Dmosk said:**
> Ok fairly new at everything especially wine. I want to install wireless driver on 8.10 from netgear, I want to know if it can be done through wine wine or if i have t have them re-written. ](*,)

This is not possible I'm afraid.

---

### Post by jerome1232 on 2009-02-03
Although ndiswrapper can be used with windows drivers.

What is the chipset of the wifi card? That's the important question.

If it's usb
```
lsusb
```

if it's internal
```
lspci
```

and this might show some info as well

```
sudo lshw -C network
```

---

### Post by Temposs on 2009-02-03
For most hardware, there is usually a way to get it working without using a windows driver. If you're pretty sure you can't get it working without the windows driver, there is ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I hope that is an adequate solution :-)

---

### Post by Dmosk on 2009-02-03
I found a few guides to set it up, however theres no Internet connection  at all at the moment on the computer I'm trying to install it on. Is theres any way to install Ndiswrapper and compile it without a connection?

---


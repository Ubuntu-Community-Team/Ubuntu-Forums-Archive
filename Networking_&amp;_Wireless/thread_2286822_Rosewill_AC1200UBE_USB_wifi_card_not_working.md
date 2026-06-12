---
title: "Rosewill AC1200UBE USB wifi card not working"
date: 2015-07-14
forum: Networking &amp; Wireless
---

### Post by musser-brett on 2015-07-14
I have a Rosewill AC1200UBE USB 3.0 wifi card. It works fine when I use it on Windows, but I just can't get it to work on Ubuntu. I've been searching all over the Internet for a solution. I found one or two that might seem like they would work, but I couldn't get them to work when I tried them. However, I did discover some useful information. I have found out that it uses a Realtek RTL8812AU chipset. I also found a driver here:  [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)  but I couldn't get that driver to work. In the directions it says, "Installing the driver is simply a matter of copying the built module into the correct location and updating module dependencies using depmod" but I don't know which file is the module, or where the correct location is. I'm a bit new to Linux.
Currently I am using a Netgear Wifi USB adapter to post this now. It does work, but it is very slow and I would like to use my much faster Rosewill adapter. I am using Ubuntu Gnome 15.04.

---

### Post by praseodym on 2015-07-15
Please show the terminal output of

```
lsusb
```

---


---
title: "Trendnet TEW-423PI and ndisgtk"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by jamieh on 2007-12-08
How can I get the Trendnet TEW-423PI to work with 7.04? I am new to linux so please give me easy step-by-step instructions.

Thanks!

---

### Post by coolbrook on 2007-12-08
I'm assuming that you have ndisgtk installed.  Copy the Windows 98 driver (the .inf file and .sys file) to a folder on your system and install it using System...Administration..Windows Wireless Drivers.  I'm sure ndisgtk works fine but it may be worth it to install the driver using terminal commands instead:

In terminal check to see that your system is acknowledging the card's presence

```
lspci
```

You should see that your card is present.

```
sudo ndiswrapper -i ~/pathtoyourdriver/drivername.inf
ndiswrapper -l
```

You should see that the driver is installed and present

```
sudo depmod -a
sudo modprobe ndiswrappper
```

Check the installation with one or both
```
ifconfig
iwconfig
```

You should be able to detect wireless networks in your area.  It's then a matter of choosing your network and connecting.

---


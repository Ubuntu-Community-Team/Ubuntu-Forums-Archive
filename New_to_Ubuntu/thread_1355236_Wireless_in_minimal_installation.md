---
title: "Wireless in minimal installation"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Fidelio on 2009-12-14
Hi All,
I've been trying a few distros to see if I can get a usable system on my old laptop, a P3 1Ghz system with 256mb RAM.
Crunchbang works fine, but I'd be happier with a more traditional desktop, so I thought I would try a minimal Ubuntu, and add LXDE. Both are running side by side at present. While Crunchbang worked out of the box, with wireless, I can't get the wireless to work on the Ubuntu partition.
My wireless come up on lsusb as '148f:3070' which I think means it's a Railink 2870 device.

Shows up in Ubuntu as wlan0, but in crunchbang as ra0.

iwlist scan in ubuntu shows 'no scan results'

As the installs are so similar, both being based on minimal ubuntu, I thought it would be quite straightforward to configure the LXDE one.

What am I doing wrong here?
Tx

---

### Post by Bachstelze on 2009-12-14
Try bringing the interface up first:

```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 scan
```

---

### Post by Fidelio on 2009-12-14
Hi. Do you mean..

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

Yes I've tried that. Still says
```
 No scan results 
```

---


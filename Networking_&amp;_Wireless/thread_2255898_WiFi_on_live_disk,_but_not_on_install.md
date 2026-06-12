---
title: "WiFi on live disk, but not on install"
date: 2014-12-08
forum: Networking &amp; Wireless
---

### Post by jshx87 on 2014-12-08
I am installing xubuntu on a dell latitude e6400

I booted off a live usb and got the additional drivers to use the wifi card.  I loaded xubuntu onto the drive then booted onto the new partition only to find i cant enable the driver to have my wifi work.  it shows the driver but when i try to apply the machine to use it. it never changes over.

ideas?

thanks

---

### Post by Hadaka on 2014-12-08
Hi, please remove the usb  and open a termnal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

---

### Post by jshx87 on 2014-12-08
Im told to insert cd-rom of the distro

---

### Post by Hadaka on 2014-12-08
so wifi works on usb "try ubuntu" but does not on "Install Ubuntu"
is this correct? And of course you are trying to do the entire load
wirelessly..correct? It is really better to insert the load while hard
wired. Post the error message on the INSTALL when it fails.
thanks.

---


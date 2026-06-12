---
title: "no wifi adapter found"
date: 2018-11-02
forum: Networking &amp; Wireless
---

### Post by gw67058 on 2018-11-02
Hello im running ubuntu  18.04 through virtualbox on a win10 enterprise host, problem is "No Wifi Adapters found, make sure you have a wifi-adapter plugged and turned on "

laptop type is lenovo T470p,  network card is Intel(R) Dual Band Wireless-AC 8265 and Sierra Wireless Em7455 Qualcomm Snapdragon X7 LTE-A
network diganostics information is at :  [http://paste.ubuntu.com/p/GWt8jjtmrs](http://paste.ubuntu.com/p/GWt8jjtmrs)

tries 2 solutions  

[https://ubuntuforums.org/showthread.php?t=2395655&p=13781215#post13781215](https://ubuntuforums.org/showthread.php?t=2395655&p=13781215#post13781215)
[http://ubuntuhandbook.org/index.php/2018/08/no-wifi-adapter-found-hp-laptops-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/08/no-wifi-adapter-found-hp-laptops-ubuntu-18-04/)

but didnt work out 

any suggestion would be helpful thanks

---

### Post by jeremy31 on 2018-11-02
In most virtual installs only a USB wifi device can be used directly by the guest OS and with a PCIe wifi you can usually access internet through a virtual ethernet adapter created by the VM

---


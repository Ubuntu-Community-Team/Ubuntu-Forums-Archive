---
title: "Linksys WUSB54GC not working"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by CheetahDC on 2009-04-12
I'm a total noob.  I picked up this WUSB54GC, because according to this page: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) , it should work "out of the box", which, from my understanding, means there should be a driver already included with Ubuntu.  I'm using Intrepid Ibex.  So...how do I get this thing to work?

Also, I installed some drivers and other programs, not even sure if they're the write ones, using Terminal.  How do I find these programs and uninstall them?

---

### Post by waspbr on 2009-04-12
is your WUSB54GC black or grey?

---

### Post by cjv8888 on 2009-04-12
I also have a WUSB54GC.  It did work out of the box in Hardy and in Mint6 which is based on Ibex.  Do you get a network icon on the top right of the panel and what happens if you right click on it?

---

### Post by waspbr on 2009-04-12
... 
that's why I asked what color it was, I googled around and apparently the WUSB54GC v1 (silver/grey) works of the box while the WUSB54GC v3 (black) doesn't..

---

### Post by kerry_s on 2009-04-12
you got to check what chip it's running.
in terminal> lspci -vn | grep net
you have to check the 14e4xxxx code to see if it's supported.

not all linksys are the same internally.
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by CheetahDC on 2009-04-19
Thanks all. I just got tired of it and decided to run an ethernet connection, hah.  Thanks for the tips though!

---


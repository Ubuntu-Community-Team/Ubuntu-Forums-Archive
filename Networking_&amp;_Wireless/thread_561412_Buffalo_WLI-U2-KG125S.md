---
title: "Buffalo WLI-U2-KG125S"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by PhaderSYD on 2007-09-27
Can anyone guide me into setting up the Buffalo WLI-U2-KG125S to work with Ubuntu 7.04.

Downloaded These Packages And Installed
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)  [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9) 
[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) 

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
(NOT SURE ABOUT ABOVE STEP)

lsusb
0144:00BC  Melco. inc

sudo ndiswrapper -i netg125s.inf
sudo cp usb8023.sys /etc/ndiswrapper/netg125s/
sudo cp rndismp.sys /etc/ndiswrapper/netg125s/
ndiswrapper -l

netg125s : driver installed
       device (0144:00BC}) present

sudo depmod -a
sudo modprobe ndiswrapper

sudo ndiswrapper -d 0144:00BC netg125s
(Sometimes comes with 0144:00BC.F.Conf File exists
netg125 is not installed (properly))
This should be it but i still have no wlan0

is there something im missing??

---

### Post by PhaderSYD on 2008-01-18
Got it to work with Gutsy and original driver cd

sudo ndiswrapper -i netg125s.inf
sudo cp usb8023.sys rndismp.sys /etc/ndiswrapper/netg125s/
ndiswrapper -l (adapter present)
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
iwconfig (showing wlan0)

thats it.
thanks for the massive amount of help i got off everyone.

---


---
title: "Buffalo WLI-U2-KG125S problems"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by Jakob Lundberg on 2007-10-11
I have problems with my Buffalo WLI-U2-KG125S usb wlan client. I have tried to use ndiswrapper, but it does not seem to work.

> 
$ndiswrapper -l
netg125s : driver installed
        device (0411:00BC) present
$ sudo depmod -a
$ sudo modprobe ndiswrapper
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by cabe45 on 2008-05-12
Sorry to revive an older thread but I have the same problem and I've searched around and none of the solutions work for me iwconfig does not show wlan0, I am running hardy with ndiswrapper 1.50.  If anyone has any suggestions they would be greatly appreciated.

---

### Post by Jakob Lundberg on 2008-05-12
I did get the thing working, but as I'm not using it anymore I have forgotten the exact solution. But basically you need to copy some of the driver files to some ndiswrapper directory. Ndiswrapper only copies one file automatically when it installs the driver.

---


---
title: "MSI Wind wireless not working"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by therabidbadger on 2009-03-23
Hi all,

You all have been very helpful in my change to Ubuntu. I am trying to get the wireless working. I have tried to install several versions I have found from this forum and the wind forum. 

Can any help me?

I need super basic instructions. I have been using Ubuntu for all of about 5 hrs.

Thanks

---

### Post by Xiong Chiamiov on 2009-03-23
Can you please post the output of
```

lspci | grep Network

```
If that doesn't show anything, then just
```

lspci

```
Any other information about your hardware would be helpful, and what you've tried to do and what the results were.

---

### Post by iaculallad on 2009-03-23
I've used the link below to solve my MSI Wind's wireless problem:

[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Wireless:](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Wireless:)

Try replacing your network-manager with [wicd]("wicd.sourceforge.net").

---

### Post by therabidbadger on 2009-03-23
iaculallad: tried it all but replacing the card which i will probably not do

---

### Post by therabidbadger on 2009-03-23
Xiong:

The first command didn't work. This is the output from the second command.

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22)


Hope that helps

---

### Post by therabidbadger on 2009-03-24
bump

---


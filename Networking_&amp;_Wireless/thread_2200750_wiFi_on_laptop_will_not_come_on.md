---
title: "wiFi on laptop will not come on"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by john140 on 2014-01-20
I have installed Unbuntu on an older laptop.  It is an Averatec 3200.  It has a WiFi switch next to the power switch and that is supposed to turn the WiFi on and off to save battery power.  When I installed Ubuntu on the laptop the switch is very intermitant.  Most of the time I can not turn the wifi on.  I haave updated the software by connecting to my wired net.  Does any one have ahny idea how to be sure that I have consitant WiFi.

John

---

### Post by marx404 on 2014-02-23
John, I have had major driver incompatibility issues with Lubuntu and my old Averatec 3220H1 laptop. I have read where others have had issues with the wifi on this laptop as well. My plan, IF , I ever am able to get Lubuntu 13.10 installed on this laptop is to switch to a compatible usb dongle for my wifi. 

That said, how did you get Ubuntu to install on your Averatec? I chose Lubuntu as it does not have Ubuntu's Unity interface, which I felt would conserve resources.

---

### Post by praseodym on 2014-02-23
Please show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
pccardctl info
lsusb
lsmod
iwconfig
rfkill list
```

---


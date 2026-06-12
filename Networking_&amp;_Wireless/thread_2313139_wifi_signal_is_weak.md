---
title: "wifi signal is weak"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by naveen_george on 2016-02-10
Product name:RTL8101E/RTL8102E PCI EXPRESS FAST ETHERNET  CONTROLLER,
vendor:Realtek semiconductor co ltd,
driver:r8169.Wireless interface 
product:RTL8723BE PCIe Wireless Adapter,
vendor:Realtek semiconductor Co Ltd,
driver:rtl8723be 
driver version.I am using ubuntu 14.04.

The signal strength is too weak.Sometimes it gets disconnected.How can i rectify the problem.pls help.

---

### Post by Hadaka on 2016-02-10
Hi, Try this..
[http://ubuntuforums.org/showthread.php?t=2304607](http://ubuntuforums.org/showthread.php?t=2304607)

#Page 6...  #Post 52

Please post..
#or whatever your wlan is..
```
iwconfig wlan0 | grep -i signal
grep '' /sys/module/rtl8723be*/parameters/*
```

thanks.

---

### Post by naveen_george on 2016-02-12
signal level is 72 dbm.i tried post 52.but when i try to connect to antenna 2 permission is denied.pls help.

---

### Post by Hadaka on 2016-02-12
Hi please follow this guide..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
thanks

---


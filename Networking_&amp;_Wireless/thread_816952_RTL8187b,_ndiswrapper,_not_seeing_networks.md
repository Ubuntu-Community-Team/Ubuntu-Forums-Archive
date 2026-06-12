---
title: "RTL8187b, ndiswrapper, not seeing networks?"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by mattpark on 2008-06-03
Hi All, 

I wonder if you might be able to assist me in spotting what i'm doing wrong here. 

Just installed lastet ubuntu verstion on my Toshiba Equium A200, model PSAF5E. The internal wireless is realtech "rtl8187b"... for some reason its not pci, but attached to the internal USB port. Highly odd. 

Anyway, I have the driver installed fine using ndiswrapper. It was all working great and spotting wireless networks no problem. 

Rebooted, and although the device us still there, it just not picking up wireless networks at all!?

Any ideas?

lshw -C network:
```
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:7a:13:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g

```

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

lsusb:
```
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Cheers, 

Matt

---

### Post by chili555 on 2008-06-03
This is from *man iwlist*> Triggering scanning is a privileged operation (root only) and normal users can only read left-over scan results.If you have just set up the interface, there are no left-over scan results. Please try:```
**sudo** iwlist wlan0 scan
```

---

### Post by mattpark on 2008-06-03
Hi,

Thanks for the response. 

Unfortunatly we don't see anything cropping up with that comman either:

```
 sudo iwlist wlan0 scan
[sudo] password for mattpark: 
wlan0     No scan results

```

:(

---

### Post by chili555 on 2008-06-03
This is from ndiswrapper's site: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)> First, find out if you can see your access point (AP) with iwlist wlan0 scan Note: You may have to set the network name before the scan can find your Access Point. If the scan does not find your AP, try issuing the command iwconfig wlan0 essid ESSID before using the command iwlist wlan0 scan. If this lists your AP, you can continue. Otherwise, you may have one of two problems: Your AP doesn’t broadcast SSID. See the FAQ for more information, or if the radio of the card is off again, see the FAQ for details. So, I guess you have to know your ESSID in order to find out your ESSID! Wacky!

---


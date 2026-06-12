---
title: "How do I uninstall rt73 driver"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Floppyjoe on 2007-02-09
I have installed a rt73 driver on one of my computers to test if I could get a DLink DWL G122 ver C1 to work. I believe I installed it incorrectly and it does not work properly. I have blacklisted the driver but I would like to try to install a different version of the same driver. Does anyone know how to uninstall this driver so I can try to reinstall the other driver?

Edit: I have found that my Dlink DWL-G122 Ver C1 works out of the box with the native driver rt73usb but there is an odd wmaster0 interface listed in iwconfig along with wlan0 which are tied together somehow. Both interfaces are using the same mac address but only the wlan0 works.

---

### Post by tonab on 2007-02-09
type into the terminal   



ndiswrapper -e rt73

---

### Post by Floppyjoe on 2007-02-09
> **tonab said:**
> type into the terminal   



ndiswrapper -e rt73


It is not however a ndiswrapper driver.

---

### Post by tonab on 2007-02-09
I guess that might be the case after I posted

---

### Post by Floppyjoe on 2007-02-09
I read another post that suggested that one does not need to uninstall previous drivers, just compile and install new ones. When I tried this and ran dmesg it still seemed to be referring to the first driver that I installed.

---

### Post by yigal.weinstein on 2007-03-17
Floppyjoe why not just 

```
modinfo rt73
```

then you will know what driver is being used.

---

### Post by Floppyjoe on 2007-03-17
> **yigal.weinstein said:**
> Floppyjoe why not just 

```
modinfo rt73
```

then you will know what driver is being used.

Thanks for that info. It's been a while since I've been playing with that device.
I found that my D-Link DWL-G122 H/W Ver C1 F/W Ver 3.00 works with the native rt73usb serial monkey driver out of the box in Ubuntu Edgy.

---

### Post by krol on 2007-03-18
Can  you explain how did you make it work with edgy default rt73 driver?

---

### Post by Floppyjoe on 2007-03-18
It's actually kind of funny. I thought I was using a different devices drivers and that that was making it work. I also have the same device, a DWL-G122 H/W ver A1 F/W ver 3.2.0 for which i was using ndiswrapper to get to work and I thought that my version C1 was using the same ndiswrapper drivers because it worked when i pulled one out and plugged the other one in. All i did was set up my network interfaces file with the information about my router such as Essid,Channel and Mode-managed as well as my WPA config. I also had my WPA config file properly set up to work with WPA supplicant.
I also have the following lines in /etc/modprobe.d/blacklist.
> blacklist islsm_usb
blacklist islsm_device
blacklist islsm

---


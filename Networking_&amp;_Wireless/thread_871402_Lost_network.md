---
title: "Lost network"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by bmachia on 2008-07-26
I turned the Laptop on tonight to find my PCI network card wasn’t found or loaded during boot.  For some strange reason the previous wlan0 is no longer and the laptop is now looking for eth1, which isn’t currently defined.

Can anyone direct me to the right file to edit to change wlan0 to eth1 so I can get this laptop back online?  

I’m using my XP machine to post this and its killing me!

Bill

---

### Post by bmachia on 2008-07-26
Update
It looks like something clobbered my /etc/network/interfaces file.  This file only contains 

auto lo
iface lo inet loopback


Does anyone have an example I can use or means to recreate this file?

---

### Post by superprash2003 on 2008-07-26
please post an output of lspci

---

### Post by bmachia on 2008-07-26
This is kinda difficult to do, since I have no network connection with the laptop and the lspci command responds with a page worth of lines.  

Is there anything I can look for and respond to?

The strange thing is, since the latest update/upgrade, I have no RJ45 network and the PCI wn511b (wireless) has no lights.  Prior to tonight, the wn511b used to flash, meaning ndiswrapper was loaded the driver and the device was found.  Now nothing for both wire and wireless

I removed wn511b.inf from ndiswrapper
uninstalled ndiswrapper
and then reinstalled ndiswrapper as well as the driver.  
Still nothing.

Bill

---

### Post by bmachia on 2008-07-27
OK, I'm back on line. (I'm responding to this thread from my notebook)  Here's how I solved my problem.

I went into grub and selected the previous boot image.  And; wha-la, all Network devices were found and came on-line.

I'd love to know what happened in that last update/upgrade, that took away both my wired and wireless networks.  

Is there anyway to find that out?  By comparing the working and non-working grub images?

Thx
Bill

---

### Post by bingobingo on 2009-02-02
Try this driver...
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---


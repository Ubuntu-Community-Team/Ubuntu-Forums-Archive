---
title: "Wlan not working on HP Laptop with Broadcom BCM43142,Ubuntu 16.04"
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by summse on 2016-12-07
I followed the "Broadcom guide".
lspci -nn -d 14e4:
==> 03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)


The corresponding broadcom table told me to install driver "bcmwl-kernel-source".

I installed Ubuntu 16.04 on my laptop form CD. I also checked the checkbox for third party software. 
Through the installation process the driver package "bcmwl-kernel-source" was installed.
Unfortunately WLAN is not working. I can see the menu entry for activating WLAN ("Funknetzwerk aktivieren"),but I am not able to activate WLAN. I can click the menu entry, but nothing happens.
I attached the wireless-info.txt file for more information.
Did I just miss something? 
Thank you in advance for your help!

---

### Post by jeremy31 on 2016-12-07
Welcome to the forums.  Please open terminal and enter
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and see if wireless works

---

### Post by summse on 2016-12-08
Dear jeremy31, 
thank you very much for your help!
I followed your suggestion and Wlan works fine now.
Best Regards!

---


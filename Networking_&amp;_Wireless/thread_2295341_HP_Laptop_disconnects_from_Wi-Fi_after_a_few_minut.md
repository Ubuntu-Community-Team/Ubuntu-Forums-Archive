---
title: "HP Laptop disconnects from Wi-Fi after a few minutes"
date: 2015-09-17
forum: Networking &amp; Wireless
---

### Post by King_Fluffy on 2015-09-17
Hi, new to Linux. When my Laptop first boots it connects to WiFi no problem but after a couple of minutes I won't be able to connect to anything (but the symbol in the upper right claims I am still connected). Disabling Networks and leaving that off for a while before re-enabling seems to allow me to connect again for a few more minutes. Would appreciate some help.

I've run the wireless info script (attached), installed the linux-firmware-nonfree package, made sure my system is fully updated etc. 

Hope I have provided enough information, many thanks.

---

### Post by jeremy31 on 2015-09-18
See if ```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
``` followed by a reboot helps

---

### Post by King_Fluffy on 2015-09-19
Perfect, thank you.

---


---
title: "blacklisting rtl8187"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-07-17
After much struggle with my rtl8187 chipset, I decided to buy a linksys usb wireless card that works like a charm OOB. The only problem is that network manager still looks for the native chipset by default. Here's what I have:

matt@Ogodei:~$ lsusb
Bus 003 Device 007: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 003 Device 006: ID 13b1:0020 Linksys 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I tried to blacklist the realtek chipset by adding "blacklist rtl8187" to my /etc/modprobe.d/blacklist file, but that doesn't do the trick. How do I shut this thing up?

Thanks

---

### Post by P3P on 2008-07-29
If you have a realtek chipset included in your motherboard, you can disable it in the BIOS configuration (see motherboard user guide for information about how to do it).

---


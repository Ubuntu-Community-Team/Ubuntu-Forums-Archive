---
title: "two wireless usb cards crashes Ubuntu"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by octaedro7 on 2007-07-24
I have three USB wifi cards, all of them working fine with ndiswrapper, but individually.  I was trying to share the internet connection with another ubuntu laptop.  What I wanted to do was:

internet>>>>Desktop PC (Ubuntu Studio) wlan0 (DHCP)
                                 ||
                                 ||                                                      Ad-Hok
                    Desktop PC (Ubuntu Studio) wlan1(fixed IP)>>>>Laptop Ubuntu wlan0 (DHCP)

Regardless what my plans were (since I could not even reach the configuration fase), as soon as I plugged a second USBwifi dongle, the system freezes having to reboot.  If I boot with both cards plugged , Ubuntu doesn't boot at all. 

My question is, beyond this particular issue, ¿Can Ubuntu handle multiple wireless connections?
¿Is an Ndiswrapper thing?

Thanks in advance

---

### Post by geraldm on 2007-07-24
There are issues with ndiswrapper: 
What kernel version?
Using special kernel stack option CONFIG_4KSTACKS (only available up to 2.6.21.1) ?

Gerald

---

### Post by octaedro7 on 2007-07-25
happens with 2.6.20-16-realtime and 2.6.20-16-lowlatency
can you explain more?

---


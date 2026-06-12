---
title: "Wireless troubles"
date: 2004-11-28
forum: Networking &amp; Wireless
---

### Post by drew on 2004-11-28
Hello, 
I am new to linux, and i am having trouble installing my wireless card (SMC 2635W) i downloaded drivers and used the ndiswrapper to install but when i list drivers installed it says "no hardware present" but when i go to network configuration i can see wlan0 and i also have this in my /etc/network/interface file.  When i run a ifup wlan0 i get no such device?. did i miss somthing or has anyone else seen this problem
Thanks,
Drew

*edit I would like to add when i do a lspci it list my network controller as linksys [AMDtek] sp906b_v2 wireless LAN adapter

---

### Post by ToddMaynard on 2004-11-29
Couple of thoughts...

Did you (using sudo):

"ndiswrapper -i /path/to/your/windows_driver.inf" ?

then "modprobe ndiswrapper"

what does: "iwconfig wlan0" show?

---


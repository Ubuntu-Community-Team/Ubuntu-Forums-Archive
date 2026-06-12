---
title: "rtl 8723be pcie"
date: 2015-07-05
forum: Networking &amp; Wireless
---

### Post by rbrtc7511 on 2015-07-05
I have just got a hp probook 445 have installed 14.4 from 12.10 .but my wifi does not work. laptop came with ubuntu 12.4 installed wifi adapter worked fine untill i upgraded 
to 14 .4 . my card is listed in system profiler but cant find a driver. rtl 8723be pcie

---

### Post by jeremy31 on 2015-07-05
It might be a different issue, show the results from terminal of this command```
lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by janmes2 on 2016-02-23
Dont know about other wifi like intel/broadcom etc but I also have the realtek rtl8723be wifi card and tried installing loads of drivers and multiple options but no jy. Also had a funny cursor. After about a month, i added this simple line to grub and low and behold all is working well.

here it is....

press Ctrl+Alt+T to open up a terminal 


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer

---


---
title: "Another wusb54g issue and stability"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by griznik on 2007-11-14
Hi.

I am trying to use the wusb54g V4 model with gutsy. I can get the device recognized by my system and can manage it from WICD. I have noticed though there are 2 main issues. 

Issue #1: It seems as though the wusb54g unit has it's own web server and configuration tools. It also seems to provide dhcp addresses which may explain how come I can get an address of 192.168.1.100 while my wrt54g is set to provide dhcp with a scope of 192.168.168.x. I hooked a laptop with XP on it and surfed into the web console which let me and showed the usual stuff... wireless security and so on. Unfortunately I screwed that up and get back in! 

Oh well. 

I am wondering am I am crazy and too many hours spent trying to get this working is playing with my mind?

Issue #2: USB seems to cause stability issues. When I plug in the wusb54g my keyboard will work for a while and then freeze. Is that something anyone else is experiencing.

Thanks for any and all responses.

---

### Post by rustybronco on 2007-11-14
i believe gutsy loads the wrong driver (rt2500pci) when it needs the rt2570 driver, try [http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54gv4](http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54gv4)

---

### Post by griznik on 2007-11-14
I'll double check that when I get home... I am sure I did have the rt25xx driver though... rausb0 according to iwconfig

Any thought about the instability with respect to USB?

---


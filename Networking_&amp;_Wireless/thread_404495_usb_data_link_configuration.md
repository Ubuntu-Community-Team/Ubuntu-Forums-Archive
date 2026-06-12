---
title: "usb data link configuration"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by xhevi on 2007-04-08
Hi everyone,

I have this situation:

Host A - desktop, Windows XP, connected to internet (via dialup CDMA)
Client B - laptop, Kubuntu 2.6.17-11 x86_64 etchy, 
Cable usb data link, vendor: Ali corp.

I am trying to access the internet from B, by connecting it to A via cable. I have used this until now in Windows, now I want to do the same in Ubuntu.

I tried to config USB Network in Windows via DHCP. 
Adapter gets address 192.168.0.1 netmask 255.255.255.0

Then on laptop
ifconfig usb0 192.168.0.2 netmask 255.255.255.0 up
route add default gw 192.168.0.1

I cannot even ping 192.168.0.1 from laptop. 
I have tried different configurations analogue to the one described above, but I'm stuck. 

Did anyone have try to solve this situation before? Can anyone suggest all steps I need to do?

Thanks,
Jay.

---


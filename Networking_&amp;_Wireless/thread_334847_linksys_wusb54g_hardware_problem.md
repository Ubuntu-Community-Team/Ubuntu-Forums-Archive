---
title: "linksys wusb54g hardware problem"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by henrik_h on 2007-01-09
I have tried installing Linux WUSB54g v.4 on KUbuntu.

I have read some other threads here but I seem to get stuck ](*,) 

The wireless adapter is working, but when i put wusb54g in the usb, everything goes slooowly, like there is som kind of conflict.

When my wireless adapter is connectet the computer get stuck for a while when "LOADING HARDWARE DRIVERS...."

Here is what I have done:

1) Have installed ndiswrapper from ubuntu's package-system.
2) Downloaded Linksys driver v.4 from linksys.com
3) installed ndsiwrapper in the same katalog as .inf-file
    ndiswrapper -i ...inf

sudo ndiswrapper -l
Installed ndis drivers:
rt2500usb    driver present, Hardware present

// looks fine

5) ifconfig
rausb0 
    the right mac-adress

It goes very slow. Can someone help me:confused: 
/henrik

---

### Post by wieman01 on 2007-01-09
You mean the internet is slow? If so, disabling IPV6 would help... You'll find references/howtos in the forum.

---

### Post by henrik_h on 2007-01-09
hey wieman01
No not only the Internet. EVERYTHING is slow :-(

---

### Post by henrik_h on 2007-01-10
Hey
Has solved the problem. I have put in some extra USB2-Card. When I removed the usb2-card the built-in (two :cry: ) usb1.1 port was working fine with the wireless linksys-adapter.
/henrik

---


---
title: "Wireless won't connect after distro upgrade (WG111v2)"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by coolbrook on 2008-04-30
My wireless stopped working after the distro upgrade from Gutsy to Hardy.  The RTL8187 driver seems to work but then it flakes out.  I blacklist RTL8187 and I try ndiswrapper with the Netgear [Win 98] driver and I have no luck. My WG111v2 won't play nice.  My router won't serve an IP address to Ubuntu.

:-({|=

---

### Post by coolbrook on 2008-05-01
bump

---

### Post by liviubero on 2008-05-10
Hy, I have the same problem (sort of...)
I have a Toshiba Satellite L40 laptop with a rtl8187 wireless card.
Just upgraded to Hardy.
I used for my rtl8187 wireless card ndiswrapper but I disabled it before the upgrade (just removed it from /etc/modules and restart) because I wanted to try out the new rtl8187 driver which should be now included in the kernel.
But when I lsmod | grep rtl I don't see the new driver at working. In fact, ifconfig doesn't show me any wireless card.
How can I start the driver? I think that it should be included in the kernel...

I tried modprobe rtl8187 and lsmod | grep rtl shows

rtl8187                36096  0 
mac80211              165652  1 rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               146028  4 rtl8187,ehci_hcd,uhci_hcd

But ifconfig and iwconfig doesn't want to show me my wireless...
Help???

---

### Post by Sevy on 2008-06-01
I have the same problem.Im using ndiswrapper and the WIN98 driver in Gutsy and everything is fine but the same settings on my Hardy box is a no go

---


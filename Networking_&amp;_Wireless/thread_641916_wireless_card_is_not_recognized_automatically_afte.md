---
title: "wireless card is not recognized automatically after reboot my xubuntu"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by mozkaynak on 2007-12-16
Hi,
I have an old laptop with AMD processor. It has Xubuntu 7.10 on it and I use usb wireless card to get connected to my home network.
My usb wireless card's brand is trendnet and it's model is TEW-$24UB
I have xubuntu recognize my usb wireless card by using  ndiswrapper.

My problem is my wireless card is not recognized by xubuntu when I reboot it unless I run 
> sudo modprobe ndiswrapper 
and restart DHCP.

I am very frustrated with running modprobe and restart DHCP everytime I reboot my computer.

Any suggestion about how to solve this problem?
Thanks....

---

### Post by jan quark on 2007-12-20
try 
 sudo ndiswrapper -m.

it writes the driver into the aliases file

---


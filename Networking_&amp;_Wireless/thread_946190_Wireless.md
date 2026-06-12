---
title: "Wireless"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by labusel on 2008-10-13
Hi,

I am quite new with this. I have installed Ubuntu newest version Herald Hero on an Amilo Fujitsu Siemens Laptop. It works perfectly with the LAN INternet. It seems that the Wireless card is detected and all other things seem to work as well, there is only one problem, I cannot turn the wireless lan on on the computer. The button does not work. It did up to yesterday with Windows XP, so there should be not problem. Is there a command to type in to definetly turn it on, so I can be sure it is turned on? How can I check? I would be very grateful to receive help.

Thanks

labusel

---

### Post by Kiefer Rodriguez on 2008-10-13
Do you just want to 'activate' the wireless device?
```
sudo ifconfig <wireless interface name> up
```
Try that if thats the case.

---

### Post by superprash2003 on 2008-10-13
firstly has your wifi device being recognized by ubuntu?? please provide output of 
1)iwconfig
2)lshw -C network

---


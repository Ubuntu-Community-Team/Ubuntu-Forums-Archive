---
title: "Port Forwarding with wireless router"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by carlosjoan91 on 2007-08-08
I used to have only a speedstream 5200 ADSL modem, and plugged directly to my home computer, so even hough it was on DHCP, i just forwarded ports that i needed, to the IP adress my ciomputer always got, now i added a Belkin 54g Wireless router to my configuration, so my simple configuration doesnt work anymore, the roputer is used for a wireless laptop, a (wireless) Nintendo DS, a (wireless) Nintendo Wii, and a wired main computer, that is from where im writing this, i want to know how do i have to forward the ports both on the modem, and the router, to get them forwarded to my main wired computer, i don't care if i cant foreward to the wireless things, just the wired computer, and it would be great if i could do this without deactivating DHCP on the wireless network, because many people bring their computers, and devices to my house, and it wouyuld be a hassle configuring IP's every time, 
thanks in advancee

---

### Post by Austin_KW on 2007-08-08
You can still use static IP addresses for devices when you router dhcp server is active. DHCP will only assign address to devices that request a dhcp address. For other devices just assign an address outside the dhcp pool (but within the 2-254 range).

Most routers will allow you to always assign the same dhcp address to the same device. If your router dhcp config do not have this option it should have a dhcp lease time. Setting a long dhcp lease will have the same effect.

---

### Post by carlosjoan91 on 2007-08-08
=O so that part is answered, b ut stil, how do i get the ports forwarded to the computer, forwartd them from the ADSL modem to the IP of the router, and then from the router to the IP adress of the wired computer? tnx again

---

### Post by Austin_KW on 2007-08-08
If the modem is a NAT device, then put the router in the DMZ on the modem. The modem will then forward everything to the router.
Then just port-forward the required ports on the router.

---


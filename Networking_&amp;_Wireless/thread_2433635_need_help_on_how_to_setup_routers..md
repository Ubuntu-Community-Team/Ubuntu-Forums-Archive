---
title: "need help on how to setup routers."
date: 2019-12-22
forum: Networking &amp; Wireless
---

### Post by unclesam-xu on 2019-12-22
Here is my scenario. I have a ADSL/fiber modem that connect to my ISP.  and I connected a tp-link router to the ADSL modem using Ethernet cable , and my computers connected to that tp-link modem. 

This is what I want to achieve. I want to turn off DHCP on the tp-link modem, all the computers and printers using DHCP to get ip address from ADSL modem so other device who connect to ADSL modem can use the shared info on my computers. What is the right process to do this. I went in the manage page of my tp-link , and turn off the DHCP feature, then reboot the tp-link to make that in effect. then I don't have internet on any of my computer anymore. Do I need to change the setting on my WAN and LAN of the tp-link modem as well.

Please help.

---

### Post by TheFu on 2019-12-22
This will only work if you can place the TP-link into bridge mode, not router mode.  The subnet that the fiber router provides has to be providing the DHCP leases to all the computers/devices on your LAN.  I know the telecom fibre provider here doesn't something funny with their gateway routers so some specific instructions on networking are necessary to do this, but I don't have that ISP, so I don't know the exact details. 

If you will say the specific provider and the city, someone might be able to help.  At a minimum, the routing on each side of the TP-link will need to be known.

---


---
title: "Cant ping my wireless laptop!"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by tuxy on 2006-11-05
I have a Belkin54g wireless 4 port router which is connected to Netcomm NB5ADSL router via a 4 port switch. My desktop is connected  to the 4 port switch as well and the laptop is wirelessly connected to the wireless router. 

The desktop IP address is 192.168.1.120 
ADSL modem address is 192.168.1.1
Wireless router address when seen from the Modem login page is shown as 192.168.1.100. I login to wireless router through laptop by typing 192.168.2.1. 

The laptop IP address is 192.168.2.2. I cant ping the laptop from the desktop because the IP address of the laptop is private within the wireless router network and the desktop can only see and ping 192.168.1.100. Basically the wireless router WAN address is 192.168.1.100 and the internal IP within the wirless network is shown as 192.168.2.1

I tried to change the IP address of the wirless router so that it comes under the 192.168.1.* range but it doesnt work because it clashing with the ADSL modem addressing.

I have checked the wirless router settings so that I can tunnel into the laptop(192.168.2.2) from the desktop(192.168.1.120) but I cant! As I said before I can ping the desktop from the laptop.

What is the best way I can make the desktop talk to the laptop.

---

### Post by x64Jimbo on 2006-11-05
Put your wifi router in switch mode - turn off its DHCP server. Network Address Translation (NAT) is the enemy of intranets. It's great to protect yourself from the nasties in the wild, but you don't need it on your own network. The 192.168 address space is quite enough for a home network.

---


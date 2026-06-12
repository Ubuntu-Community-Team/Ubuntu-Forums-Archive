---
title: "please help me set up internet connection"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by koma86 on 2007-09-01
Hi! I'm a new Ubuntu user and I don't know much about networking. 
My problem is that I'have just changed internet service provider and I cannot configure the internet with the new one. With my previous ISP I got to type "sudo pppoeconf" in a terminal, answer the questions and then "pon dsl-provider" and it worked, but with the new ISP it is a bit different because it does NOT use any username/password to connect. 
I write down how I set up my connection under Windows XP: 
They gave me a new ADSL modem (D-Link DSL 380T), after resetting it I changed Local Area Network's TCP/IP settings to IP: "192.168.1.2", Getaway: "192.168.1.1". Then opened a browser and typing "192.168.1.1" I could enter the modem's configuration panel. I changed connection type to: "bridge mode", VCI: "35",  VPI: "8", and DHCP server to: "no DHCP". Saved the modem settings and reboot. Changed back windows LAN settings to "obtain an IP address automatically" and then the whole thing worked.
I only have 1 PC at home, no routers. 
Under Ubuntu I tried to do something similar without succes. I couldn't reach 192.168.1.1 and also tried "Administration/Network" and set "Wired Network" to "Automatic configuration (DHCP)" but nothing. 
Thanks for all your help! You may also answer to my email: koma [at] fazekas [dot] hu

---

### Post by koma86 on 2007-09-04
Hello! On another forum I got a solution to my problem: 
release the IP that I got from the ISP under windows (with the command: "ipconfig /release", and then reboot to Linux.

---


---
title: "wep not wpa"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by jeremytaylor on 2006-09-04
Hi, 
the wireless network at my lab uses WEP security. When i try to connect to it using network-manager it brings up a dialoge about WPA with more options than i know what to do with. 
Any ideas about what I'm doing wrong?
thanks
Jeremy

---

### Post by SteveHoffmanUK on 2006-09-04
Newbie here, but I do have my wireless WEP working.

Not sure what network-manager you're referring to, but setting up my wireless WEP network connection in Ubuntu was sooo straightforward, I will tell you what I did, if it helps.

System | Administration | Networking | Wireless Connection | Activate

Check Enable this connection

Enter Network name (ESSID), the name of the lab's network

Key type: hexadecimal

Enter the lab network's 26-character WEP key

Under Connection settings, Configuration, click on DHCP (other options go dim)

Click OK

The activation bar will whizz back adn forth and then stop when it's activated. 

You should then be connected.

---

### Post by jeremytaylor on 2006-09-05
Thanks for the suggestion. I'd like to use network-manager as it's a nice little piece of software and handles the fact that i move between networks very neatly. 
Any network-manager users with ideas?
Jeremy

---


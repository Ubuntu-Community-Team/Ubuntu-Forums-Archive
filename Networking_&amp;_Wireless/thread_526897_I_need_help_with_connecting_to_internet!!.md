---
title: "I need help with connecting to internet!!"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Foreverlost410 on 2007-08-16
I need help with connecting to the internet!!

i use a highspeed internet modem connected to my main pc and i want to unplug it out of the ethernet port and put it into my kingston ethernet adapter hooked up on my board on my ubunt u computer

when i put it in i still cant connect the internet its highspeed and can anyboduy please help???


anything else just ask

thanks
foreverlost410

---

### Post by praet on 2007-08-16
Open 
System > Administration > Network 
and check to see if your networking hardware is installed correctly. 
It should show up as a Wired connection (eth# like eth0 or eth1).  The most used connection is by dhcp so highlight your connection, click properties and uncheck roaming mode and select "Automatic configuration (DHCP)".  This change should request a new ip address from your router/isp.

---


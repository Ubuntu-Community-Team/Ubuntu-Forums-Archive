---
title: "ndis intel 3945 not connecting"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by angrysniper on 2008-06-15
Hi, I'm running ubuntu studio 7.10 on a thinkpad T61 and I'm trying to get wireless internet working with ndiswrapper.  I have ndiswrapper installed and the driver for the intel pro wireless 3945 chip that comes in the t61, and on the surface it appears to be working.  I'm using the NETw4x32.inf windows driver.  When I open network settings and select wireless connection properties, in the SSID dropdown box it does list the local wireless networks I usually see, including my own.  However, when I fill in my wep key, ip, gateway and subnet and enable the connection, it appears to work normally, but I'm not able to access anything through my browser.  Is there any way to figure out what the problem is and then what I can do to fix it?  I've also tried disabling wireless security on my router to see if I was simply entering the wep key wrongly, but that doesn't appear to be the problem.  

Thanks for any replies in advance.

---

### Post by chili555 on 2008-06-16
Does it work correctly if you select DHCP and fill in your WEP key?

---

### Post by angrysniper on 2008-06-16
> **chili555 said:**
> Does it work correctly if you select DHCP and fill in your WEP key?

I will try this, however in my network all individual clients have to have a static IP for port forwarding purposes.  I wouldn't be able to keep it that way, so a more permanent solution is needed.  I upgraded to 8.04 last night and I have yet to install ndiswrapper again, but perhaps the upgrade will have fixed whatever the problem was.  I'll post again with the results.

---


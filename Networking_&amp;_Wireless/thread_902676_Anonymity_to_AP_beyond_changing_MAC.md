---
title: "Anonymity to AP beyond changing MAC"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by atkamano on 2008-08-27
hey guys!

First post, so please be gentle.  I have searched for this in the forums, and I could not find this topic.  

Question: I am doing some experimenting with my Ubuntu laptop and trying to create a connection with my router that is completely anonymous.  

I have changed the MAC for my wireless card.  (I checked that the MAC was faked successfully by logging into my router config)  

The problem is that this still does not guarantee complete anonymity, as on the pc description section (which is the column next to the MAC address) it still displays "ubuntu".  

Is there a way to hide from the router, what operating system I am connecting to it with?

hopefully you can help

---

### Post by SpaceTeddy on 2008-08-27
The that is displayed at your router is not figured out by the AP but supplied by your computer when asking for a dhcp lease. You can get around it by not using the dhcp but setting a static ip.
DHCP always supplies the computer name in the DHCPREQUEST. It's just part of the protocoll and nothing you can do about it. The only other solution is that you change your hostname to somethign random aswell

hope it helps :)

---


---
title: "Need WiFi help. odd problem"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by w0lf19 on 2005-06-22
I have a HP Pavilionzx5000 laptop with an integrated broadcom b/g wireless, and I finally got the drivers loaded with ndiswrapper, and it worked, the drivers were recognized and all that.

Then, I went to configure my network.

I am running wireless off of a Motorola wireless router connected to my roommates computer.

I tried everything, iwconfig, ifconfig, the gui config, and tore much hair out. At one point, i was actually able to ping, but then could not access any web-pages. Then, I rebooted, everything un-configed itself, and I had to do it again, and now i get nothing.

A big problem I had with the manual config was the Channel setting, and I have NO idea how to tell what channel the wifi router is running on, as there is no place on the roomie's computer that shows the wifi stats, and I cant find the disk or documentation for the router. 

Any help is appreciated.

Thanks

---

### Post by aamir on 2005-06-23
sudo ndiswrapper -m

this will setup an entry for you card so taht when your machine boots it sets up ndiswrapper, and enables it on the network

---


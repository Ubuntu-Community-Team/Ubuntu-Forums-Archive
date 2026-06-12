---
title: "Wireless networking seems to work but doesn't."
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Imsdal on 2007-07-09
I have a Feisty desktop install that is pretty much all standard. I did nothing at all to get the wired networking to work, I then tried to get the wireless network to work. I have a Netgear 311T card.

I started by going to System -> Administration -> Network. There, I selected Wireless and clicked on Configure. In that dialog, I picked my Network Name in the drop down list (and I also saw my neighbor's network, so I know the wireless card works). I entered Password Type WEP Key (hex) and the proper network password. Finally, I used DHCP and clicked OK.

I then deselected the wired connection and clicked the Wireless connection in the Network Settings dialog. AT that point, everything works fine. However, it's still the wired connection that is in use, because when I unplug it, I lose my network connection. Plugging the cable again immediately restores the connection.

What am I missing here? I have a Win XP box, a Wii and a smartphone who all access the wireless network without problems, so the router should work fine.

---

### Post by fugly50 on 2007-07-09
I am having the same problem as this, if anyone has a solution please reply.

---

### Post by roschell on 2007-07-09
I used to have problems with switching between wired and wireless, and the trick was I had to combine the settings in Administration>Network and also Administration>Network Tools>Network Device 
It was the Network Device which was switching off. Try to start with the second step first Administration>Network Tools>Network Device; select the device you want to use and Configure.
Hope, it helps

---

### Post by Imsdal on 2007-07-10
> **roschell said:**
> I used to have problems with switching between wired and wireless, and the trick was I had to combine the settings in Administration>Network and also Administration>Network Tools>Network Device 
It was the Network Device which was switching off. Try to start with the second step first Administration>Network Tools>Network Device; select the device you want to use and Configure.
Hope, it helps

I tried that and, lo and behold, that worked! When I went to Network Device everything looked perfectly OK (as it indeed did before as well), so I just clicked "close", unplugged the network cable and everything worked. I still have no idea why (or, rather, why it didn't work before) but I am one happy camper now and won't argue with success.

Thanks for the tip!

---


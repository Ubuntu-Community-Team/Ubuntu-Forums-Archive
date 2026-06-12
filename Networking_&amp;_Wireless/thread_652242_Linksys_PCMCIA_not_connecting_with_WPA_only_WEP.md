---
title: "Linksys PCMCIA not connecting with WPA only WEP"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by thebloggu on 2007-12-28
I have a laptop with a linksys PCMCIA wireless card and it is recognized as Texas Instruments ACX 111 54 Mbps Wireless Interface. So it is working but i am not able to connect to router becuase it does not accept wpa only wep. why it is recognized as texas ..... ? how can i fix this ? please help. thanks

---

### Post by zipperback on 2007-12-28
> **thebloggu said:**
> I have a laptop with a linksys PCMCIA wireless card and it is recognized as Texas Instruments ACX 111 54 Mbps Wireless Interface. So it is working but i am not able to connect to router becuase it does not accept wpa only wep. why it is recognized as texas ..... ? how can i fix this ? please help. thanks

It might be that the cards use an identical chip set, and just sold under different brand names.

If you want an easy way to manage your wifi connections install wifi-radar.

sudo apt-get install wifi-radar

wifi-radar is great for wifi access point management on your laptop.

Hope this helps you.

- zipperback
:popcorn:

---

### Post by thebloggu on 2007-12-28
the problem is i dont have internet on that computer. tring to connect wireless and dont have ethernet (cable)

---

### Post by rustybronco on 2007-12-28
> **thebloggu said:**
> I have a laptop with a linksys PCMCIA wireless card and it is recognized as Texas Instruments ACX 111 54 Mbps Wireless Interface. So it is working but i am not able to connect to router becuase it does not accept wpa only wep. why it is recognized as texas ..... ? how can i fix this ? please help. thanksBecause the wireless chipset is a acx111 inside the card, it must be a linksys wpc54g-v2.
I don't know if  the card will work with wpa. you can try installing wpasupplicant through a ethernet cable to the router ( sudo aptitude install wpasupplicant ), but again I have never tried it with that card.

---

### Post by thebloggu on 2007-12-28
yes it is. but wireless is the only way to connect to the network. thanks. it does work with wpa [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1130276681921]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1130276681921")

edit: tried to connect to the network with disabled security and it didn't connect. what should i do?

---

### Post by zipperback on 2007-12-29
> **thebloggu said:**
> I have a laptop with a linksys PCMCIA wireless card and it is recognized as Texas Instruments ACX 111 54 Mbps Wireless Interface. So it is working but i am not able to connect to router becuase it does not accept wpa only wep. why it is recognized as texas ..... ? how can i fix this ? please help. thanks


I mentioned that you can use wifi-radar to manage your wifi network connections, you might also want to take a look at another application called   **wicd**


I just completed a fresh install of Gutsy 7.10 on my laptop and decided to give wicd a try, and it works really great for wifi access point management.

- zipperback
:popcorn:

---

### Post by kevdog on 2007-12-29
You will need the wpa supplicant package installed in order to access WPA networks with this card.   I dont think this package is found on the installation CD, unfortunately you will need to somehow make an internet connection to download the package

sudo aptitude install wpasupplicant

---

### Post by thebloggu on 2007-12-29
wpa supplicant is already installed. i think the problem is with the driver. it just lets me use wep. i need to install another driver but don't know how.

---

### Post by kevdog on 2007-12-29
Ive seen some sites say wpa is supported and other sites stating it isnt.  It may depend on the version of the driver -- I really have no idea due to the conflicting information.  Did you try searching the ndiswrapper website specifically for your wireless card and version to see if anyone has reported wpa working -- is so -- did they link to a driver.

---


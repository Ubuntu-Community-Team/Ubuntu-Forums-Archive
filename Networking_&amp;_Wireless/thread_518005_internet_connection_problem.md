---
title: "internet connection problem"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by DrScum on 2007-08-05
with Ubuntu 7.04 on a Dell Latidude laptop I had the WG511T wireless network card going and everything worked ok.
Today for no ovious reason I can't get an internet connection, Firefox saying "server not found"

I can ping the wireless rooter and I can ping other machines connected to the network but no internet.

ifconfig yields:

ath1
eth0
lo
wifi0-00

ath1 seems to be my wireless device and from the ifconfig output it works ok. 
When I look at my router though I find two computers connected with identical physical adresses, one being connected through my ath1 and one being connected through my eth0. That's where I am out (or at the end of my latin, as we Germans say)


Any suggestions anybody?

---

### Post by Snipersnest on 2007-08-05
Have you tried giving your self a static IP for your wireless so it changes the address?

You should be able to access your wireless card in the Network area if its installed correctly.

---

### Post by DrScum on 2007-08-06
Assuming that ath1 is the wireless card I have tried to give it a static IP and I have tweaked many things to change the address. What I am missing in the network area though is the icon which shows the connection quality (4 vertical bars being filled or not depending on how good the signal is) I believe that that was there before.
However, the facts are that the connection is up (ping) but for some reason the internet is not available.

---

### Post by Snipersnest on 2007-08-06
Are you running any wireless security on your router? (WEP WPA) 
 
If so have you messed with WPA_Supplicant?

---

### Post by DrScum on 2007-08-06
I have access control enabled based on physical address but no encryption whatsoever

---

### Post by DrScum on 2007-09-08
bump

---


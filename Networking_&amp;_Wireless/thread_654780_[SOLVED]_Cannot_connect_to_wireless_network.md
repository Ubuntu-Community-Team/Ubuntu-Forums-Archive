---
title: "[SOLVED] Cannot connect to wireless network"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by edd8990 on 2007-12-31
Hi everybody!

Installed Ubuntu today on my main computer (after having enjoyed using Xubuntu on my eee laptop).

It detects my Wireless cards fine. (I've tried it with both a Netgear wg111v2 and a ZyXEL G-202) but I cannot get it to connect to my network. I'm running a WPA2-PSK network, with a key made up of 63 randomly generated ascii characters. [Yeah, I'm paranoid!] The SSID is hidden, but there is no MAC filtering. My eee connects to it fine (And I've used the same text file storing the SSID and wpa key in it, so I know I have got the key right!) So I'm really stumped as to why it isn't orking. does anyone know why this could be?

---

### Post by jualin on 2007-12-31
You have to check if you have the package WAP-Suplicant or something like that. I was having the same problem and after I installed the package everything worked. Also you could try to check if there are any propietary drivers that you could use. I had a laptop that Ubuntu recognized the Wireless card but could not connect to the network and after installing the drivers through the restricted drivers option it worked.

---

### Post by edd8990 on 2007-12-31
It's WPA-supplicant, and yes I have it. As to the drivers, I can't install anything, as I have no net...

---

### Post by jualin on 2007-12-31
Can you connect if you disable the WPA key in your router?

---

### Post by jualin on 2007-12-31
Does Ubuntu give you the option of installing the restricted drivers. If it does maybe you could connect your laptop through the ethernet port and download the drivers. And then try to connect using the wireless card.

---

### Post by kegobeer on 2007-12-31
Make you SSID visible and see if you can connect.  That's what I had to do.

---

### Post by edd8990 on 2008-01-06
I fiddled about for a bit, but couldn't get anything working. Then I moved back to university (hence the delay in this reply) and the ZyXEL card connects to my new network here [running very similar settings]. The Netgear card wont connect, but that's not a worry to me. I have my net back (Only thing the ZyXEL card can't do is asses network strength, says they are all max strength, which is wrong, but I can live with it!). Thanks for all your help guys!

---


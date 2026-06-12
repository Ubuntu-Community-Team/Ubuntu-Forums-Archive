---
title: "Atheros problems :("
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by PhoenixMaster00 on 2008-09-23
Recently i bought a custom laptop from pc-specialists with Ubuntu pre-installed and everything works fine... except the Atheros Wireless support :( im quite a linux noob but i hav tried every tutorial i could find and nothing seems to work Madwifi, Ndiswrapper just doesnt work and i no from other sites and forums that it im not just being an idiot... Its telling me that im using a Atheros AR242x ive got it to recognize Ndiswrapper as the driver but it still doesnt work and any suggestions would be greatful

Thank You

ps as a side note the laptop also comes with a biometric finger tip reader is there any ubuntu developments in that area?

---

### Post by Crafty Kisses on 2008-09-23
I'd like to see the results of this command:
```
lspci | grep Atheros
```

---

### Post by PhoenixMaster00 on 2008-09-23
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by SilverAdder on 2008-09-23
I have a similar wireless card which gave me a lot of trouble. I got it working wih [this]("http://ubuntuforums.org/showthread.php?t=798485&highlight=atheros+compatibility") script which installed madwifi and got it working fine for me. I hope this helps you.

---

### Post by PhoenixMaster00 on 2008-09-23
Thanks for the help but it didnt work it seems i have a ar5006eg Atheros and so far all i can are tutorials for 07 chipset as i do believe mine seems to be unsupported...

---

### Post by superprash2003 on 2008-09-23
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by PhoenixMaster00 on 2008-09-23
does this work same for hardy heron as wel or should i jus pop gutsy back in until it is supported by madwifi?

---

### Post by superprash2003 on 2008-09-24
you could give it a try

---


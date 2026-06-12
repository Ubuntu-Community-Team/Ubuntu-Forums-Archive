---
title: "Broadcom 4310 Wireless not working even though ndisgtk shows as installed"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by abhinav90 on 2008-10-03
I am having a problem with my wifi in ubuntu 7.10 gutsy.

In Network Manager the wireless connection icon is not coming.

I installed ndiswrapper successfully 

In Ndisgtk it shows one icon for bcmwl6 and hardware present = yes. This happened after i installed this driver for my broadcom wireless card which is Broadcom BCM4310 USB Controller (rev01). 

However, the problem was still not solved. What should i do??
The wireless connection link still doesnt come on network manager.

Please Help!

---

### Post by abhinav90 on 2008-10-03
i realized that i will need the bcmwl5.inf driver file as that is the windows xp driver. bcmwl6 is for vista and hence didnt work. 

Where can i get the bcmwl5.inf file for my dell latitude e6400 laptop with Broadcom wireless card BCM4310.

---

### Post by Ayuthia on 2008-10-03
You might try checking this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by abhinav90 on 2008-10-04
hey i got it to work :)
I just downloaded the bcmwl5.inf file for my wireless card from dell support and my wireless started working.

Thanks for all the help. I love Ubuntu!!

---


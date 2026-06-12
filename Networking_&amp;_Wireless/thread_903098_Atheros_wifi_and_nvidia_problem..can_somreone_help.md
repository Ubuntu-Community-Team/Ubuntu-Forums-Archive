---
title: "Atheros wifi and nvidia problem..can somreone help plz"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by thousandpimps on 2008-08-27
ok so i just bought my laptop..and first thing i did install ubuntu (dual boot) cuz i used to use it before and i like it..but after installing and updating ubuntu things didnt go as smooth..

my computer is compac cq50 laptop
nvidia driver
atheros wireless 
amd athlon x2

this is what is written on my laptop

so in the ristriced drivers i have three options:
atheros hardware access layer (hal)
nvidia accelerated graphic driver (latest cards)
support for atheros 802.11 wireless lan cards

so my problem is that my wiress doesnt seem to work ...i right click on the network thing on the task bar and it shows no wireless networks or anything..

another problem is i think my nvidia may have something to do with it to..as when i check nvidia on my restricted driver ..it tells me to restart and when i do ..i get the splash screen (ubuntu) ...it loads but when it comes to the login screen i dont see anything...the screen goes blank...so plz if anyone can help me that would be wonderful..

tell me if you guys need more information 
thanks a lot

---

### Post by thousandpimps on 2008-08-28
k i'm dumb...i followed a tutorial and it started working..the tar i was getting was old and the ticket had expired so i was only getting a readme file which stated where i can get an updated version ..then my wireless appeared..but now i cant connect ...any ideas?

---

### Post by pakamon on 2008-09-26
The same problem here.
If I install atheros hal and reboot, Atheros will work, nvidia NOT :( Getting 800x600 resolution. If I install nvidia, nvidia will work and Atheros not :( (iwconfig doesn't show wireless interfaces)

---

### Post by Mgiacchetti on 2008-09-26
See this is my problem...

ASUS m70vM-x1  

Nvidia GeForce 9600m GS works out of box in Intrepid.  Sound, fingerprint reader, webcam, pcmcia, 5 in one card reader, and external monitor haven't been tested yet.

Atheros wifi...  iwconfig shows interfaces, ifconfig shows  eth0, lo, wlan0 and wmaster0

no matter which security type i select, atheros will not receive any packets from the router. 

when i click to connect, it shows the network name, a little computer icon, and an empty bar.  

I did have it show a half empty bar ONCE but still could not connect.

the drivers in use are the ath9k  so if anyone has any ideas that could help out...  atheros 928x

---


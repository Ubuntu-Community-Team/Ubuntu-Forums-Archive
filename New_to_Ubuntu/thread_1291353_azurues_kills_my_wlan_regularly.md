---
title: "azurues kills my wlan regularly"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by freak42 on 2009-10-14
hello all,

when I run Azureus, after a relatively short period of time, my wlan connection gets dropped.

issuing a
ifconfig wlan0 down 
ifconfig wlan0 up

seems to reset my wlan and it runs again for a while. I haven't found the exact cause of the problem and appreciate any suggestions.

- it isn't be the router, it has run for years relatively stable, azureus on windows doesn't cause any problems, and while ubuntu looses the wlan connection other computer don't have a problem with it
- I can't find anything interesting in var/log/ .. dmesg debug messages

- it's a HP 8530w laptop (intel chipset with an a/b/g/n card (afaik)), the router runs 802.11g (& b)

any help is appreciated

---

### Post by freak42 on 2009-10-14
I forgot to mention that otherwise my wlan seems to run very reliably, I use my connection extensively with various applications including ssh,sshfs, vnc, games, and of course browsing.

---

### Post by whitethorn on 2009-10-14
Try turning down the amount of simultaneous connections in azureus.  You have to play around with the connection settings.

---

### Post by freak42 on 2009-10-14
do you have some rough numbers a guidance level..?

I decreased max global connections form 256 to 150.. we'll see what happens
(I kept the per torrent connections at 100)

---

### Post by Slim Odds on 2009-10-14
Make sure that you limit your upload speed.

Otherwise your upstream acknowledgements to downstream packets get choked out.

This is a well known TCP/IP issue.

---


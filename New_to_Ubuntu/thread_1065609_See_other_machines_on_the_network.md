---
title: "See other machines on the network"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by constantlycurious on 2009-02-10
Hi all,
I have several Ubuntu machines (8.04) and several XP machines all running on the same LAN. 
The xp boxes can browse the local network much better than the ubuntu boxes, for example I have a web server machine named testwebserver. Any of the XP machines can type testwebserver into a browser and immediately see the server. On the ubuntu machines I have to type the ip address of the server into firefox to get the same results. Typing testwebserver doesn't work. 
Likewise I have a Terastation on the lan that all the xp users can easily browse to by clicking on network hood and then clicking from there. The ubuntu users have to click places, network and then type the actual ip address of the Terastation in order to see its contents. It seems like the windows boxes are running some sort of service that resolves the ip address with the name of the machines but I am not running any sort of local dns server. 
My question is why? Any ideas?

---

### Post by theozzlives on 2009-02-10
Have you installed Samba? My web server, I should be able to type: www-server, 192.168.1,2, my static IP, or [www.theozzmicrosystems.com](www.theozzmicrosystems.com) and it's Ubuntu. I just have one XP dual boot machine.

---


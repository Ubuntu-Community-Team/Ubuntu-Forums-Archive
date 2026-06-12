---
title: "Networking question"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by Bodwin on 2007-07-14
OK here is what I have home:
1.Internet connection using PPPoE protocol
2.3 computers: 2 desktops + 1 laptop
3. Some cables :)
One of the desktop computers is under Ubuntu and it (almost) acts as a router. It has 3 network cards: eth0 - connected to the other desktop PC(also under Ubuntu) ; eth1 - connected to the laptop(running windows XP) ; eth2 - connected to the Internet. I managed to set up my pppoe connection and share it with the other computers. The eth0 network card is using this ip:192.168.1.1 while the eth1 uses 192.168.0.1. There is no bridge between the two connections (but actually I don't need/want it cuz' the router PC doesn't have a monitor so I'll have to bring my 25 kg monitor to the other room). Anyway I can make a remote desktop connection so after so much info my question is: what should I do next to improve the security. Should I install a firewall or something?

---

### Post by KyleBrandt on 2007-07-14
Ubuntu is fairly secure in its default setup.  To set up firewall rules you can either edit iptables or install a gui to do that, i.e. Firestarter.  Other options to harden the system would be to compile and use the grsec kernel, and install Bastille.  The last two are both somewhat advanced things to do, the most important thing to do is it to keep all your systems updated.  You could maybe scan your computer with nmap from a remote connection.   Network security is a very complicated topic, as there are usually many possible vectors for attack.  I personally liked "Hack the Stack" as an introduction to some of these topics, as it is based on the OSI model.

---


---
title: "two wireless cards in one machine"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by gruadp on 2007-10-17
I use 7.10 and still I'm not too happy with the NetworkManager and the roaming mode.

My laptop happens to have two wireless cards. One buildt in to the laptop (ipw2200) and the second one an external pcmcia-card (ndiswrapper).

The buildt in is not working well with my wireless-router (package-loss ~20%) and this is why I have and want to use the second card.

But NetworkManager always connects with the ipw2200-card first and there is no way to tell it, that it should use the ndiswrapper-card. I have to manually choose this card in NetworkManager. As soon as the connection goes down (hibernation of the laptop, moving in uncovered aerea ...) and up again, then the ipw2200-card is connected to again.

Where can I set once and for all, which of these cards is used??

Additionally NetworkManager goes crazy every few days: It does not connect at all with no card, but takes up 100% cpu-time until its killed -9.  This is where I usually freak out and connect to wlan really manually using iwlist and iwconfig which works without any problem.

NetworkManager is better than in any previous version, cause it at least works sometimes. But it still causes big problems and I had to move the ndiswrapper-module to /etc/modules manually to get a chance on my external card :)

---

### Post by spd106 on 2007-10-17
Go into System -> Admin -> Network and turn off roaming mode for the Intel card. You can set it  link local or a made up static address and it shouldn't interfere with the other card any more.

Failing that just blacklist the ipw2200 driver in the /etc/modprobe.d/blacklist file. That will probably save some cpu interupts too.

---


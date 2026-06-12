---
title: "Just question:)"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by reauthor on 2007-04-21
hy guys..
I just would like to know if it posible in Feisty to setup Networ-manager-gnome
to work in wireless enviroment(WPA2-PSK or WPA2AES) whit second or virtaul IP...Yes here is one HOWTO(sticky) on this forum but that is a pain in ### specially for more than one PC..

---

### Post by spd106 on 2007-04-22
I'm not quite sure what you mean. If you're after 2 phase authentication (eg EAP MS-CHAPv2) then I'm afraid that that this is not currently supported by Network Manager. It is under development for the next major release.
There are other applications that do support this feature, though I have not tried it personally I understand that Wicd is capable of this. See [http://ubuntuforums.org/showthread.php?t=414001](http://ubuntuforums.org/showthread.php?t=414001)

---

### Post by reauthor on 2007-04-25
Thanks for the answer but maybe my question is not understandable.
If I need two static address for one interface (wireless interface) and few static routes whit WPA2 AES encryption and Enterprise (RADIUS) authentication is it  possible to make work this combination  with Network-Manager-Gnome or some other utility..This combination works like a charm in XP or Vista.In Edgy  works too but only whit WEP encryption and network-manager as a standard utility in Edgy.

---


---
title: "eth1 (intel pro wireless 3495) dissappeared on edgy upgrade"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by gripepe on 2006-11-04
Hi,

I have been hearing about problems related to the ipw3495 driver on edgy, relating connexion to networks. But my problem is that Edgy won't show up my wireless interface. When I run ifconfig, for instance only the eht0 and loopback are shown. In dapper, i also had eth1 for my wireless interface

I had been using Dapper since some time ago, and I had no problems at all when switching networks or using the embedded button for turning on/off the wireless transmitter, but since the upgrade it just dissappeared. Neither the button works now. ¿Could it be something related to the keyboard layout?

The device manager shows that the internal card is there, using the ipw3495 driver. My laptop is a Dell Inspiron 640m.

Thanks for your help.
Marcos Bernal

---

### Post by anguste on 2006-11-04
Yes I have exactly the same problem with you buddy... I'm using a Dell Latitude D520, whose wireless interface card is also IPW3495ABG.

It used to work fine with Dapper but just can not show up in Edgy.

Anyone can help on this topic? Appreciations...

---

### Post by gripepe on 2006-11-05
finally got it working. I downloaded and installed the linux-686 generic restricted modules. Now the switch works again, as well as the wireless interface. Thus, another bug appeared: if i boot the computer without having enabled the wireless led, it crashes.

Still thinking on that.

---

### Post by Maxwzell Rain on 2008-05-05
Just to inform others who are looking for a solution to this problem : 

Wireless wasn't functioning at all after the clean installation of Hardy.

Installing the modules and restarting the system worked for me as well.

Good luck.

---


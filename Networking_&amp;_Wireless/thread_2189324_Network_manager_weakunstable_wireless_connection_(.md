---
title: "Network manager weak/unstable wireless connection (Intel 7260)."
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by hrnsk77 on 2013-11-21
Network manager wireless(intel 7260) wont work so switched to Wicd. 

Works fine but then it seem like i need network manager to set up my VPN and combining that with Wicd dont work.

Tried to install Kvpnc but cant seem to get that working or find any good pages/howto Kvpnc and Ubuntu 13.10.
(might be something on KDE packages?)

Cant seem to find any other ways to set up a VPN with Ubuntu.

Anyone got experience with Kvpnc and Ubuntu 13.10?
or any other good ideas to solve this wireless/VPN problem?
anyone with similar solved problems? :)


Getting a bad headache here.
and ye, me and Linux is pretty fresh..

---

### Post by hrnsk77 on 2013-12-03
Hi again.

After posting last post I desided to focusing my effort to make Network Manager solution working.

The only thing that has seemed to work for me amongst all the things i found out there (nothing spesific on 13.10 and the Intel 7260 card.) was disabling 802.11n protcol.
As described here in "solution 2" : [http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

This seemed to stablize the connection, at least good enough for surfer web. but no more, stable but weak.


Anyway i know this is no solution, but there seems to be a problem with 13.10 and the Intel 7260 card.
Post this and hope that someone else more experienced will come up with a fix.

---

### Post by eva-evapz on 2013-12-07
[SIZE=3]Hi,

Here is what I found about your pb, and read that this worked for many people with intel cards issues.

This should fix your issue and let you use the network-manager, then openvpn via the network-manager.

First make sure you have the '[/SIZE][SIZE=4][COLOR=#0000ff][FONT=Times New Roman]iwlwifi[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#444444][FONT=Times New Roman]'[/FONT][/COLOR] driver for your intel card installed

check this in your connection details :[/SIZE]

[IMG]http://blog.erwan.me/public/captures/Informations_sur_la_connexion_001.png[/IMG]


[SIZE=3]Then run those command lines in a terminal :

> **sudo rmmod iwlwifi**

> **sudo modprobe iwlwifi 11n_disable=1**

If your wlan connection works fine (better/regular speed, check again your connection details) then do that to make it permanent :

> **gksudo gedit /etc/modprobe.d/iwlwifi.conf**

a white page will open, then add this :

> **options iwlwifi 11n_disable=1**

save and quit gedit.

Let me know if it does work.

see source (but french) : [http://forum.ubuntu-fr.org/viewtopic.php?pid=10624251](http://forum.ubuntu-fr.org/viewtopic.php?pid=10624251)[/SIZE]

---


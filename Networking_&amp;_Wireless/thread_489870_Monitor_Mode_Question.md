---
title: "Monitor Mode Question"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by database_dan on 2007-07-01
I hope you guys can help me out on this one. I am using Feisty Fawn and have a Linksys WMP54G (Ralink 2500 chipset). When I put my card into Monitor Mode

```

sudo iwconfig ra0 mode Monitor

```

It will only stay in monitor mode for about one minute, then it automatically switches back to managed mode. It will revert back to managed mode when aircrack-ng or kismet is running. It will also revert back to managed mode when I don't do anything (ie: let Ubuntu idle).

Any ideas to either:
a) find out what is causing it to switch
b) keep it from switching

Thanks for any help guys,
~Dan

---

### Post by database_dan on 2007-07-03
[IMG]http://img.photobucket.com/albums/v314/SilverSurfer77/General/5thElement.jpg[/IMG]

---

### Post by jollyr0ger on 2007-07-14
have you tried to put your card into monitor mode with the tool distribuited with the aircrac-ng suite?

you have to digit this:
airmon-ng start eth1


then use aircrack to do what you want.

after 
airmon-ng stop eth1

---

### Post by database_dan on 2007-07-14
> **jollyr0ger said:**
> have you tried to put your card into monitor mode with the tool distribuited with the aircrac-ng suite?

you have to digit this:
airmon-ng start eth1


then use aircrack to do what you want.

after 
airmon-ng stop eth1

jolly,
thanks for the reply. i tried this and the result was the same, the card stayed in monitor mode for a minute, then switched back to managed mode.
~dan

---

### Post by t1n0m3n on 2007-07-19
Hi, I am having the same problem.  I set the card to monitor and it reverts to managed after about a minute.  I just set it to monitor every minute or so and Kismet seems to work fine...  Its just annoying

---

### Post by t1n0m3n on 2007-07-19
Oh, I just updated my sig with my setup...  :)

---

### Post by t1n0m3n on 2007-07-19
ahh, ok, I found my issue.
Click on knetworkmanager, options, disable wireless
then do a
"sudo iwconfig ra0 mode Monitor"

("sudo iwconfig eth1 mode Monitor" for my computer)

This seems to have stopped the managed autoswitching for me.

---

### Post by t1n0m3n on 2007-07-19
Keep in mind that if you "Quit" from the systray icon for networkmanager, that only stops the tray icon...  networkmanager is still running (/usr/sbin/NetworkManager and /usr/sbin/NetworkManagerDispatcher)

---


---
title: "Can't see networks"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by ronfedele on 2007-01-02
I cannot see networks in network manager. If I type in ssid I connect but if I do not know what it is I cannot use it.

help

ron

---

### Post by zappa86 on 2007-01-02
What does iwconfig have so say about it. Run that and post the output. also do an ifconfig so we can see if its getting an IP. What network card are you using. What network are you connecting to? does it have security?

---

### Post by spd106 on 2007-01-03
Try setting the AP to broadcast it's SSID. 

Network Manager can sometimes have trouble finding networks that do not broadcast their SSID.

---

### Post by rigreves on 2007-01-22
Have same issue here. Was running Edgy on my Compaq Presario 2171 US with my DWL-630G D-Link pcmcia card. I had some other issues as well including some Mplayer support for Firefox/Swiftfox and a recnt business trip to Raleigh made it obvious what I needed to do....Switch back to ---- Dapper!

Dapper uses my Atheros linux native driver, and I am able to see the SSID's no problem. The signal level is also accuratley represented. I would suggest taking a look at iwconfig and see what it says before doing what I did. My only issue now is the small annoyance of the video driver that leaves black streaks on the "radio" buttons until my mouse passes over them.

---


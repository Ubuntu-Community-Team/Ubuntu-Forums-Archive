---
title: "Wireless bandwidth usage monitor"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by jerrynewt on 2013-12-31
Just wondering if there is a netspeed like app for monitoring my wireless network bandwidth usage. I have an iPad connected and was wondering about the download and upload speeds when it is being used. Thanks for your time.

---

### Post by varunendra on 2014-01-04
There are many, just do a search in Synaptic or Software Center.

The System Monitor already shows the live Network Usage under "Resources" tab. For a permanently running lightweight alternative, I use "**nload**" which is a commandline program (usage example : "nload -u K wlan0").

For a detailed history and permanent record of bandwidth usage, I find "**vnstat**" to be perfect (usage example : "vnstat -d -i wlan0"). It is very versatile and also has the ability to show the stats in 'live' mode (although it is not meant for that purpose). The benefit of using commandline tools is that they are lightweight and you can use them in your own scripts, using the output whatever way you like.

---


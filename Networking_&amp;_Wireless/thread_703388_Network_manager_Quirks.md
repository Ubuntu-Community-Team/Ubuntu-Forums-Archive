---
title: "Network manager Quirks"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Matthijs van Henten on 2008-02-21
Hi, here's a question: why does nw-manager has such a hugely hard time connecting to my WPA - secured network, while a the commandline tools bring up the connection in seconds?

Some of the quirks are:
- looking up the essid in use, it reporst the wrong essid ( my network's name is home, it says homed)
- although the router's strength is excellent, the two green dots seem to appear at random interval, connecting to my neighbours' router, with far lesser strength - or worse - trying to connect to some other secured network.
- reporting different signal strengths depending on the time of day, but not the location of the laptop

There is some suspicion of interference being the culprit ( having lots of babyphones and lots of digital tv on the 2.4 band in the area), but how come the connection seems stable when setup manually? Is nw-manager forgetting to put the card into managed mode?

A windows and macosx computer sitting next to this one, both have excellent connection, and disabling nw-manager, I'm homefree on the linux too. Any way to improve this, so I don't have to disable nw-manager and fire a shell script every boot? I'm a big fan of automagic things.

ps. this is what I run to get a stable connecion:

#!/bin/sh
echo "Killing running wpa_supplicant"
killall -9 wpa_supplicant
echo "Setting up wlan0"
iwconfig wlan0 essid "home" mode managed
echo "Starting wpa_supplicant"
echo "wpa_supplicant -c /etc/wpa_supplicant.conf -iwlan0 -B"
wpa_supplicant -c /etc/wpa_supplicant.conf -iwlan0 -B
echo "running dhclient requesting an ip"
dhclient wlan0

---

### Post by R13120(1&lt; on 2008-02-21
you might try wifi- radar. it's in add remove programs. it's less Trixy

---


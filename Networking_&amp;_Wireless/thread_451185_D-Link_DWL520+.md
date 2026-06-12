---
title: "D-Link DWL520+"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by KMW on 2007-05-22
Is anyone else having problems with this card or is it just me? Or, am I the only one using this card with Feisty? Under supported hardware it states this card "just plain works". Not!!!!

---

### Post by bigken on 2007-05-22
I also have the same problem to make it work I use these comands in the terminal

sudo iwconfig ra0 essid (name of network)

sudo dhcliednt ra0

and it works

---

### Post by KMW on 2007-05-22
I tried a sudo iwconfig the other day and still couldn't connect.

---

### Post by bigken on 2007-05-26
for some reason mine is now working ok without having to use the commands strange

---

### Post by KMW on 2007-05-27
Reset router to defaults, rest router and changed ssid, channel and password,. Reset cable modem and configured Wireless Networking , all under Win XP then rebooted Feisty and removed Network Manager then rebooted again. Reset network with the new essid, and password and it's been running ever sense.

From the looks of the poll in networking looks like wireless isn't doing so well overall.

---


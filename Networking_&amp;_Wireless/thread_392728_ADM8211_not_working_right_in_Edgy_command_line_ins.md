---
title: "ADM8211 not working right in Edgy command line install"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Durito on 2007-03-24
I'm not able to get my wireless card working properly in an Edgy command line install. The system seems to see it and use the right driver (ADM8211 in an SMC 2635W), because it shows with in iwlist/ifconfig/iwconfig, and I can change essid/txpower/whathaveyou without any problems. However, it won't connect. When I use **$sudo iwlist eth0 scan**, it immediately returns a null result, without making a search attempt.

Looking at the settings, Tx-power is off. Could that be it? Using **$sudo iwconfig eth0 txpower on** or **$sudo iwconfig eth0 txpower auto** has no effect and returns no message, but **$sudo iwconfig eth0 txpower 15**, does change the Tx-Power value from off. Doesn't seem to do anything else though. Any ideas? I'm sure it's probably just one basic setting I'm missing. 

I've got an old TP600e (400MHz, 256Mb) that I've been running Dapper on, but am trying a command line Edgy install because of the system runs way too slow with the full Ubuntu/Gnome load. This wireless card worked out of the box with the Dapper Live CD install, but I haven't used it with any other Ubuntu installs. So, I'm not sure if it's a command line install issue, or an Edgy issue, or neither. Or both. :confused:

---

### Post by Durito on 2007-03-25
[FONT=Palatino Linotype]Scratch this--I figured it out.[/FONT]

---

### Post by _profox on 2007-04-10
> **Durito said:**
> [FONT=Palatino Linotype]Scratch this--I figured it out.[/FONT]
Care to share? :) I know someone with the same problem.

---


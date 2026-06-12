---
title: "[Wireless] Power save"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by LeDieu on 2008-01-01
Hello,

I have a question about saving power on my wireless interface.
Powertop reports that i can reduce the power of my wireless interface. I can do this by the following command: iwpriv eth1 set_power 5

What i wanna know is: how can i set this option as a default.

Greetz,
LeDieu

---

### Post by santosh_gr on 2008-01-01
You can reduce the power used by your wireless device by modifying the power options with iwconfig command.

e.g.  iwconfig wlan0 txpower 5

I havent tried it out myself, so dont know the implications of change the power settings for the card.

---

### Post by santosh_gr on 2008-01-01
Sorry the correct command is to use power options with iwconfig.

You will have to read through the man pages for iwconfig to see what options you can set.  e.g. iwconfig eth0 power saving 3

---


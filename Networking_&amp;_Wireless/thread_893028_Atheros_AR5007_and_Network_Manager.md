---
title: "Atheros AR5007 and Network Manager"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by alligoodw on 2008-08-17
I've installed the Atheros AR5007 driver in Ubuntu 8.4.  If I go to system/administration/network and turn off roaming, my wireless shows up with an availability rate of 88%.  That's all good and fine. It also list my neighbors wireless connection at 15%.

However, should I go and select the network manager from the taskbar, right clicking on it, I see that network and wireless are enable (with roaming selected), but when I go down the menu and select configure wireless, my wireless connection isn't listed there.  

What am I doing wrong?  Does any of this make sense?

---

### Post by nicedude on 2008-08-19
Give me the output of the following commands and I can tell you what you might have going on. I use a AR5007 myself and can tell you they do work but mine only did after installing the correct driver. It was enough of a tough job that I wrote a guide on it for others. But please give me the folling commands outputs and also tell me what driver you tried to install.

COMMANDS TO RUN IN A TERMINAL 1 AT A TIME

lspci -n

iwconfig

sudo iwlist ath0 scan

Armed with that as well as what driver you are trying to use I can advise you as to what may be wrong.

---


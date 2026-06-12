---
title: "Belkin F5D7230-4, I DON'T want to go back to Windows!"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by tibrslackey on 2007-01-18
Please HELP! I am very new to Linux. I had been brainwashed by Windows for a long time. If I can't click on it or if it doesn't autorun I am lost. I am in desperate  need of help. I've been reading the forums and still can't figure out how to get my Belkin F5D7230-4 Router to work. (I'm not even going to mention the wireless F5D7000 wireless cards I have on my two other computers). I have the installation disk. I have installed the dapper drake edition. Can someone please save me from lord Bill and walk me through setting up my router correctly? Like I said, I am the click master so I will probably need someone to spell out the script for me.

---

### Post by spd106 on 2007-01-18
How do you mean set it up? I didn't need to do anything different to the windows PCs to get it working. Plug and play surely. If you mean what wireless settings can Ubuntu handle, it can do them all WEP, WPA-PSK TKIP/CCMP.

Can you connect to the router's web page? Usually 192.168.2.1 on Belkin ([SIZE="1"]grumble[/SIZE]) routers. Have you been able to ping it? You can check whether you received an ip address by clicking on the network-monitor tray applet and selecting the Support tab. If there isn't one there then you may have to open a terminal and try typing **ifconfig**, and **iwconfig** for a wifi card.


The wireless cards shouldn't be too much trouble, though it would be useful for you to mention the exact model version and revision number. Maybe a look at the output of **lspci** from a terminal as well.

---

### Post by tibrslackey on 2007-01-18
It's not Plug and Play. I somehow need to install the driver but I am lost. I want it to go from the cable modem to the wireless router to the computer but it's not working. I'm connected through the cable modem but when I connect the router...nothing.

---


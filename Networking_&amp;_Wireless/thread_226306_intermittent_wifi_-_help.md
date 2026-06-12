---
title: "intermittent wifi - help"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by landwomble on 2006-07-31
Hi All,
Got an IBM X31 running Ubuntu 6.06 and am using a cheapo no-name wifi card.  It's detected fine, and generally seemed quite happy but now is intermittent.  Typically it doesn't work on boot, but will eventually start working if I tinker - i.e. go into wifi-radar, come out, generally mess with the connection.

Can anyone give a newbie some ideas for stuff to check or logs to post here to get some help?  It's driving me mad as it's intermittent.

I'm using WEP, wifi-radar and the card itself is correctly picked up as wlan0.  (Card works fine in Windows, so not a hardware issue).  When not working wifi-radar shows it as connected, but to local loopback 127.0.0.1 rather than correctly in the 10.0.0.x range my router's handing out via DHCP.  Tried it on static IP as well and no difference.  Like I say, it *has* worked and intermittently does, so I'm at a bit of a loss...

Any help much appreciated, I'm getting towards the end of my tether with this...
Ric

---

### Post by x64Jimbo on 2006-07-31
Have you messed around with the CLI at all? I have found that the graphical interface managers aren't really up to the industry standard yet. 
Some stuff to try
sudo iwconfig wlan0 essid <SSID> key <key>
sudo dhclient wlan0

---


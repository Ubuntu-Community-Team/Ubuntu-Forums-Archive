---
title: "Wireless network management woes..."
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by Thumper322 on 2006-11-30
Hello all,

With a bit of work (gotta love Ethernet and the Ubuntu Wiki ;)), I've managed to set up my WPC54G card using **ndiswrapper** and **Network Manager**. Everything's working fine, but when I'm having a few issues with Network Manager:
[LIST]
[*]To connect to my work network, which has a hidden ESSID and uses WPA, I have to manually choose "Connect to new wireless network," then type in the ESSID and passphrase manually. After doing this, **nm-applet** asks for my password to connect to my "keyring"; I assume this is to automate future logins, but Network Manager never connects on its own.
[*]When I'm connected, the Network Manager applet always shows full signal strength, even when this is not the case.
[*]And, finally, when I select my home network from the drop-down list, the signal strength bar is empty--I'm guessing because [progressbars are invisible]("http://www.ubuntuforums.org/showthread.php?p=1827662") on Edgy's default theme.
[/LIST]

Is there some way to fix any of these? I've had a look at [Connection Manager]("http://ubuntuforums.org/showthread.php?t=299462"), and it seems promising, but apparently it can't connect to networks with hidden ESSIDs.

I'm afraid I don't really know my way around that well yet; I only installed Ubuntu a week ago, and this is my first Linux distro.

Thanks in advance for any help.
~Thumper322

---

### Post by KingBahamut on 2006-11-30
For hidden IDs I normally use swscanner, it might seem a little obtrusive, but its effective nonetheless 

sudo apt-get install swscanner

Im not sure about the others (wifi-radar, knewtorkmanager, or wlassistant....look at those).

---

### Post by Thumper322 on 2006-11-30
> **KingBahamut said:**
> For hidden IDs I normally use swscanner, it might seem a little obtrusive, but its effective nonetheless 

sudo apt-get install swscanner

Im not sure about the others (wifi-radar, knewtorkmanager, or wlassistant....look at those).

Thanks for the suggestion, KingBahamut.

If I install swscanner, then do I need to remove Network Manager? Also, does swscanner have features similar to those of Network Manager (panel applet, signal strength, etc)?

---

### Post by KingBahamut on 2006-11-30
[http://www.swscanner.org/](http://www.swscanner.org/)

---

### Post by Thumper322 on 2006-11-30
> **KingBahamut said:**
> [http://www.swscanner.org/](http://www.swscanner.org/)

Hmm... I'll give it a go as soon as I get on my Ubuntu box. Thanks!

---


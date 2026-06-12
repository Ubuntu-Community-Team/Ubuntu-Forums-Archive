---
title: "Feisty &amp; Broadcom 4306"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-04-20
Hi


Kubuntu Feisty 7.04

I as trying the new Fiesty LiveCD today.

I tried the KWifiManager to connect a Broadcom 4306 wifi card & noticed that it automatically identified my chip as "eth1" & gives the opportunity to select WPA.

 However, after adding the appropriate WPA info into KWifiManager, it wasn't able to connect.

Has anyone had any luck out-of-the-box with WPA & Fiesty, using KWifiManager? Would a HD install solve the connection issue?


Thanks for any input.

---

### Post by DapperMe17 on 2007-04-21
bump

---

### Post by winter7 on 2007-04-21
I have the same problem... I have it installed on the HD and still no go.

---

### Post by RobN on 2007-04-24
I'm VERY new to Linux, but after searching around the forums found this, which is what finally started everything working for me:

bcm43xx-fwcutter 

Go to synaptic (under System/Administration on the menu) and search for it. Install it. Run it once (sudo bcm43xx-fwcutter) and it does its magic.

Search the forum for fwcutter for better directions from more knowledgeable people.

---

### Post by jasonbrisbane on 2007-04-26
Hello,

Upgraded from 6.10 and managed to get wireless working with Wicd and put the laptop in suspend.
Since then I've not been able to get it working again. :mad: (That is with WPA!).

I've installed and removed network-manager-gnome, network-manager, wicd, wireless-tools, wpasupplicant and reinstalled all several times and to no avail.

I've been playing around with /etc/wpa_supplicant.conf and /etc/network/interfaces...

The consensus seems to be to removed all details form the interfaces file except for the lo entries and reboot and to let network manager to handle it.

In the system log it seems to get to stage 4/4 of the wireless handshake (in Administration ->System Log-> ?syslog) and to simply "timeout" near the end.

Crazy thing is it all worked perfectly in 6.10 with niswrapper, which I have to keep using.
Different programs seems to attempt it at various stages but they simply wont connect - not even to the open network!

I  **really** dont want top have to resort to a wired network with a youn one on the way...
It took me about 10 days to get the wireless working on 6.10 so I will perservere...
(PS Any help would also be appreciated!)

---


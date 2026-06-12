---
title: "Wlan connection lost after a while (RT2561)"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by winterg on 2008-05-23
Wlan connection is lost after being online for a while. Never had any problems under XP so I guess this is some driver issue.

What to do? I was thinking:
-Install a rt2x00 driver: [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
**or** 
-Use ndiswrapper with Windows driver: [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

SPECS:
Gutsy Gibbon on a notebook
RaLink RT2561/RT61 802.11g PCI (pcmcia)
Wicd and WPA security

[SIZE="1"](btw my other thread where I mentioned this problem ran dead for some reason :? [http://ubuntuforums.org/showthread.php?p=4760264](http://ubuntuforums.org/showthread.php?p=4760264))[/SIZE]

---

### Post by mapes12 on 2008-05-23
> Install a rt2x00 driver: [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

This would be my bet. I tried ndiswrapper but after a while the windoze driver just gave up on me.

---


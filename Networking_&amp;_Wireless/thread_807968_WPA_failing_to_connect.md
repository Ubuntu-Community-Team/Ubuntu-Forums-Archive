---
title: "WPA failing to connect"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by myonta on 2008-05-26
Background: I'm running Hardy 64 and I use TRENDnet's TEW-452BRP Wireless Router and TEW-443PI Wifi adapter in this machine. There are at least 2 other computers on the wireless network at any given time (usually WinXP boxes).

Typically I either run my network open or with MAC filtering. This time, however, I decided I would like to use WPA-PSK (so far without filtering). So, I setup my router to use WPA-PSK, selected "automatic" for TKIP/AES, entered a passphrase and went to work on various machines. 

Initially it worked on my Ubuntu-box but whenever the system restarts (and sometimes without restarting) it becomes unable to connect returning a 169.254.0.0. I end up having to change something in the network settings then change it back to force it to re-initialize my network. Additionally, this method doesn't always work.

Obviously this is an extremely annoying problem (much like the JRE error that OpenOffice keeps giving me since upgrading). Any ideas on where to look and what to do are greatly appreciated.

~Jon

---

### Post by mapes12 on 2008-05-26
Here's some helpful links:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29%7C%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29%7C%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

:guitar:

---

### Post by asanti on 2008-06-13
I just installed Hardy Heron version 8.04 and also had problems with the wireless, every aspect of it. However I got the wireless to work after several tries.  This is what I did. Using the packet manager I searched for Network manager, WEP, WPA and installed those packages.  Restarted after each install. Then I installed NDISwrapper and Madwifi packages using the package manager.  I did all of this without having the buscard installed in the computer.  After installing all of the packages I installed my buscard in the computer, clicked on the network icon and selected my SSID, C&P my network key in the network manager and my wireless was working.  I read all of the post and most of them are having you install everything manually.  I got this to work using a Linkys card and a Dlink.  Works great.  I hope this helps anyone seeking wireless help.

---


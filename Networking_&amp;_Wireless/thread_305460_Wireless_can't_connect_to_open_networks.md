---
title: "Wireless can't connect to open networks"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by DigitalDingo on 2006-11-23
I recently installed Ubuntu Edgy on my laptop, and so far everything seems to be ok – except for the Network Manager. The wired network is working perfectly, but the wireless is not.
I am able to connect – through Network Manager – to secure/encrypted wireless networks, but when I try to connect to open networks the Network Manager disappears for about one second, then reappears without any changes! The network I'm trying to connect to isn't even marked. Does anybody know how to solve this?
I'm using an Intel PRO/Wireless 3945ABG Network card, but I bet it's some security option I need to get rid off...

---

### Post by Hmarroqu on 2006-11-23
[http://ubuntuforums.org/showthread.php?t=292407](http://ubuntuforums.org/showthread.php?t=292407)

---

### Post by NetworkGuy on 2006-11-23
There is also a bug reported in launchpad that Network Manager has issues connecting to unsecure networks.

---

### Post by FrodoB on 2006-11-23
Could giving it a managed command like this in the interfaces file help perhaps:

pre-up iwconfig wlan0 mode Managed

changing wlan0 to your device name and giving it this line first thing after the section starts? Just a wild stab in the dark.

---


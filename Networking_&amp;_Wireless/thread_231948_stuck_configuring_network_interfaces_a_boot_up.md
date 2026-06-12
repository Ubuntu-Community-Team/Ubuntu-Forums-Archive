---
title: "stuck configuring network interfaces a boot up"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by geeper6 on 2006-08-08
I followed the instructions on the forum [https://help.ubuntu.com/community/Wi...r/RalinkRT2500](https://help.ubuntu.com/community/Wi...r/RalinkRT2500)

to modify setup to take WPA PSK but when I use the 'auto ra0' command and have the card plugged in when I reboot the startup freezes at 'configuring network interfaces'. And then I have to disconnect my wireless card and reboot and then once everything starts up plug the card back in and activate it through Networking.

Otherwise the card works and connects great.

Is there a way to automatically activate the card at startup? without killing it at configuring network interfaces?
Thanks for the help,
G

---

### Post by geeper6 on 2006-08-08
nevermind found the answer here [http://www.ubuntuforums.org/showthread.php?p=1301594](http://www.ubuntuforums.org/showthread.php?p=1301594)

the ifup and ifdown worked like a charm. Boots up and starts the wireless card and connects to the network.

---


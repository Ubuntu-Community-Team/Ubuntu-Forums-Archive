---
title: "Belkin F5D7050 v 3000 help!"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by shift_06 on 2007-07-29
Hi, i tried

> [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29)

 and got up to Step 6 - Configure the network settings for the rt73 device i am stuck and this is what i pasted into the text document

> [INDENT]# rt73 wireless network device using DHCP
iface **wlan0** inet dhcp
pre-up ifconfig **wlan0** up
wireless-essid belkin54g
wireless-key f9fe82abc0
auto **wlan0**[/INDENT]

But when i go to step 7 it doesnt work


By the way the guide said that the bold wlans should be rausbs but im really confused so any help would be greatly appreciated!

ps. Shall I try this: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)  ?

---


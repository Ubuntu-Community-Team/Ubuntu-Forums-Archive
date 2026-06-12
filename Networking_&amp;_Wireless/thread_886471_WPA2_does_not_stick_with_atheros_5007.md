---
title: "WPA2 does not stick with atheros 5007"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by steam73 on 2008-08-11
I am fairly new to linux and very new to Ubuntu. I installed Ubuntu just yesterday (8.04) on an Acer Aspiron 5720 with atheros 5007 wifi. My non-computer-liking wife was complaining about vista being very slow, and XP does not have a good working wifi driver for this wificard (not when I tried some time ago). The method of installing the atheros driver in this post: [http://ubuntuforums.org/showthread.php?p=5565255#post5565255]("http://ubuntuforums.org/showthread.php?p=5565255#post5565255") worked, but I was still puzzled about how to get connected. After a few minutes of looking around I found this kind of works.
What I did was click on 'System/network' then 'unlock' and click on the wireless-icon. There I inserted the SSID, WPA2, and password. This worked like a charm. But after a reboot, the connection does not come back. When I look at the wifi setting, it is changed to WPA i.s.o. WPA-2!

How can I make this setting stick to WPA-2? And is there a command-line way to doe this?

---

### Post by steam73 on 2008-08-11
Don't mind this thread. I was a bit too early in posting, sorry for that!.

I found a lot more info on this forum than I thought possible. I will first try the command line stuff from kevdog and wieman01. If then the wpa2 does not 'stick' either, I will post here again.

---

### Post by steam73 on 2008-08-12
Ok, I am one step further now:
The problem is not that wpa2 does not stay in the networking file, only it does not show in the network manager. To get connected it helps when I do:
 sudo /etc/init.d/networking restart
Just 'start' does not fix the network.
I had only ath_pci at the end of the file: /etc/modules. Therefor I added ath_hal (wieman01 howto), but this did not fix the problem. I still have to do a networking restart to get wifi up. Can anybody help me out?

---


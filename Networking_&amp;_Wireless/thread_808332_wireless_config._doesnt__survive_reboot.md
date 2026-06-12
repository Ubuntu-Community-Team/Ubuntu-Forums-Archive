---
title: "wireless config. doesnt  survive reboot"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by lazyjoe on 2008-05-26
Hello, 
I just installed ubuntu 8.04 (gnome)on my gateway mt3705 laptop. I was unable to find a driver for the wireless component net8185.  I managed to get it setup using ndiswrapper.  I setup the windows driver just fine net8185.inf
Then I entered my ssid and wep.   Then I entered these 2 lines
sudo depmod -a
sudo modprobe ndiswrapper
After doing that, the wireless works great.  However, after every reboot, wireless is not setup anymore and I have to enter those 2 lines back into terminal.  Also, on a unrelated topic, any links on my desktop to directories on my windows partition are inactive until I select the media seperately from the gnome menu. This too does not survive a reboot. However, just about any about any other config change survives a reboot
I'm new to linux and gnome, so I may be overlooking something obvious. Also, for clarification sake I installed this using WUBI on a seperate partition and the file system is NTFS.

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out.

If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent tutorial. Good to use with the tutorials from the previous links:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

:guitar:

---


---
title: "Need Help Getting Wireless Up at Boot/Login with Static IP - rt61"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by zobcat on 2008-03-05
I've tried all of the fixes for similar problems here on ubuntuforums to no avail. I now must ask for some guidance. I'm not an avid linux user, but I understand enough. So here goes:

I can connect wirelessly through the network-manager and I have a "location" saved within the app. However, when I reboot, my wired connection seems to be competing with the wireless. All I have to do is apply the "location", which just selects the wireless connection with the settings i want (static ip, essid, wpa, etc.) 

This wouldn't be a big deal, however I have no plans on ever being near this computer. It's going to be in another room, and I will be using remote desktop to connect to it. When the computer is turned on in the morning (there will be no input devices nor a monitor connected to it) it will auto login, but I need the wireless to connect to the network so that I can connect to it from my office.

If you can help, just let me know what you need. (i.e. ifconfig, iwconfig, lspci, etc.)

Thanks in advance

EDIT: My wireless starts working after a network restart now. 
```
sudo /etc/init.d/networking restart
```

Now, all I need is help with getting a shel script to work properly at login to restart the network, like this guy: [http://ubuntuforums.org/showthread.php?t=599427&page=2]("http://ubuntuforums.org/showthread.php?t=599427&page=2")

I followed everything he did verbatim (I think) and still nothing. 
(talking to walls)

---


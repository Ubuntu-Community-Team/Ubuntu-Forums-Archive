---
title: "Automatic Wireless Detection"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by jopv on 2007-06-12
hi

Installed Ubuntu Fiesty fawn on my laptop (Thinkpad Z60T) a few weeks ago and it went fairly smooth. My wireless network was not automatically detected but I managed to get it to work using 'Static IP Address'.

The problem I have is that every time I shut down the laptop and boot back up I have to manually switch on the wireless connection i.e. I have to first uncheck and then check the check box in the Network Settings window.

Is there a way I can get the wireless connection to switch on automatically when I boot up? Do I have to change something in the 'interfaces' file under /etc/network/ ?

Also, how do I get the wireless LED to work? I also have an external wireless switch and would love to get that working. Any help would be appreciated.

Thanks, JOHN

---

### Post by spd106 on 2007-06-14
According to this wiki page [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadZ60t](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadZ60t) you have an Atheros card that uses the madwifi driver (ath_pci).

I have had some trouble with intermittent connections and I found that reinserting the driver sometimes allows me to connect to my AP.

A more reliable method is to disable network manager and use wpa_supplicant from the /etc/network/interfaces file. This requires editing text files, so it does require some confidence/experience with Linux. There is a useful guide to doing this in the Wireless Security WPA etc sticky [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539).

---


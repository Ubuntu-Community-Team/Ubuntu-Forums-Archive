---
title: "Drivers set up, everything done, yet still No Connection(No DHCPOFFERS received)"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by nismoskys on 2007-10-21
Please help, I've been trying to get this wifi working for at least 2 hours.
My Network adapter is a WUSB54GP.

I finally got the ndiswrapper driver working roughly following kevdog's [guide for that]("http://ubuntuforums.org/showthread.php?t=574501").. now when i try to configure my network through network settings, it even detects the name of my network, so i click it, and type the 10-dig hex below it for WEP, but nothing happens, i get no confirmation of connection and of course, firefox doesnt work etc.. 

Driver=ndiswrapper+wusb54g driverversion=1.48+The Cisco-Linksys, LLC.,01/
I just installed the OS (7.10) this morning and have just been trying to get the internet working
I have a broadcasted ESSID, and its WEP. I followed kevdog's [WEP instructions]("http://ubuntuforums.org/showthread.php?t=571188") exactly.
Everyhing goes fine but at the end of sudo dhclient wlan0, i don't get a DHCP offer from 192.---

this is what I get at the end ```

Listening on LPF/wlan0/00:0f:66:11:3c:fb
Sending on LPF/wlan0/00:0f:66:11:3c:fb
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```



--also I have no other way to connect to the internet on the computer other than by restarting and booting into Windows.. so I can't really download anything there. I'm on a laptop right now just so I can get onto ubuntuforums for some help.

thank's alot... your assistance is appreciated :)

---

### Post by nismoskys on 2007-10-21
bump..please help i dont know what else to do..

---

### Post by nismoskys on 2007-10-21
come on.. anyone.. please?

---


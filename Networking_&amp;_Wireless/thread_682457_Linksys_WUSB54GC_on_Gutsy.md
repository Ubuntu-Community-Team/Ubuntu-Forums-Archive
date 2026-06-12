---
title: "Linksys WUSB54GC on Gutsy"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by markhorrocks on 2008-01-30
The list of supported wireless cards lists the Linksys WUSB54GC card as supported out of the box in Gutsy Gibbon. I take this to mean that it will use an unrestricted driver built into Gutsy.

I purchased this card today to replace a Linksys WPC54G v3 which is not supported. Indeed, the Network (gnome?) thingy sees an ESSIS named Linksys, I select it and select WEP (ascii) and type in the security code which my windows machine uses. The light on the wireless card flashes briefly but no connection. I cannot ping the router. (linksys WRT54G).

There does not appear to be an option for selecting no security in the network configuration.
Does the fact that the card is visible mean that I don't need a separate driver? I want to use an unrestricted driver and not NDISWRAPPER if possible. 

Any help appreciated. Sorry if this issue is covered elsewhere, I can't find it. I just installed gutsy last night to my Dell Inspiron 8100 laptop (512MB RAM) for the first time.

---

### Post by markhorrocks on 2008-01-30
dhclient wlan0 reports:
there is already a pid file var/run/dhclient.pid with pid 134519120

wmaster0 unknown hardware type 801
wmaster0 unknown hardware type 801
listening on LPF/wlan0/00:1d:7e:03:fe:9b
sending on LPF/wlan0/00:1d:7e:03:fe:9b
sendng on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255  port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255  port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255  port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255  port 67 interval 1
no DHCPOFFERS recieved

---

### Post by markhorrocks on 2008-01-30
I read that the Linksys WUSB54GC wireless card worked out the the box but my experience is anything but. I really need help here as I am new to Linux. Can anyone say whether I need to use NDISWRAPPER to install the windows driver or not? The Network Manager can see this card but there is no hope of it connecting. The laptop is sitting right next to a windows laptop which connects fine to the router. 
If I can't get this acrd working, Ubuntu is a disaster.

---

### Post by rmknowles on 2008-02-09
For the record, this adapter works fine for me with Gutsy.  I just installed the OS, plugged in the adapter, and configured it with the plain old Network window.  I've got WPA enabled too.  I'm not a Ubuntu/Linux guru, but I'd be happy to post config information from my system to compare with the config on your system.

---


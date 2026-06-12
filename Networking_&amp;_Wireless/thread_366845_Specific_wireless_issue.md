---
title: "Specific wireless issue"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by Falkon MX-5 on 2007-02-21
Okay, here is the scenario:
I want to connect to the wifi network at school.  
They use WPA and I know the key.
The SSID is NOT broadcast.  
I'm trying to use wpa_supplicant to connect.  I edited wpa_supplicant.conf and added an entry for this network and even tried adding the bssid of the router that shows up.  I do NOT know the ssid, just the WPA key.  
When I run wpa_gui, it just scans forever and never associates or connects.  It's like it can't find the network.  I pretty much tell it to use ANY ssid and use the specified key.  It won't even associate even though I gave it the bssid of the router.  

What can I do to get this to connect?  It works fine on other open networks and it works on another router that doesn't broadcast ssid, but I know it's SSID.

Any help?

---

### Post by gradedcheese on 2007-02-21
Do you know the access point ID (ie: its MAC address)?  If you have physical access to the AP, it should be written on the bottom or something.  You can associate to an AP by ID rather than SSID if needed.

---

### Post by Falkon MX-5 on 2007-02-21
The scan picks up the MAC [BSSID] and I've tried putting it in explicitly in wpa_supplicant.conf, but it still just sits there and doesn't ever associate.  Also, aircrack is being a big turd with my card and won't work, so I can't get the SSID from airodump.

---

### Post by teaker1s on 2007-02-21
install [COLOR="Red"]network-manager-gnome[/COLOR]
select connect to other network and type in essid and choose encyption type

---

### Post by Falkon MX-5 on 2007-02-21
Network manager doesn't handle WPA, wpa_supplicant does.  wpa_gui is the gui front end to wpa_supplicant.  I run XFCE, but I'll try the gnome version.  I don't see this working.

---

### Post by teaker1s on 2007-02-21
well I'm using network-manager-gnome with ndiswrapper and wpa works because I'm using it

---

### Post by Falkon MX-5 on 2007-02-21
I don't need ndiswrapper, though.  My card is fully supported by kernel drivers.  I'll try it out.  The problem is that it won't associate without the SSID.  It should, windows will.

---

### Post by gradedcheese on 2007-02-21
right, don't use ndiswrapper.  network manager + wpa_supplicant (which it grabs automatically when you install) should do it.  If not, like I said, you should be able to associate by AP MAC if needed.

---

### Post by Falkon MX-5 on 2007-02-22
I decided to test it out.  I set the router to not broadcast SSID.  Well, now the network just sits there like a lame duck.  I told it what MAC to use and the SSID and all, and it still doesn't associate.  It just says it's scanning.  The network-manager-gnome doesn't do anything but sit in the tray saying that no networks have been found.

---


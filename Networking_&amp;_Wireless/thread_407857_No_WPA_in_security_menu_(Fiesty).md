---
title: "No WPA in security menu (Fiesty)"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by jonnymccullagh on 2007-04-12
Hi,
I bought an Edimax EW-7128G (RT2561/RT61) PCI wireless adapter for my wireless network. I couldn't get it working on Ubuntu 6.10 so I installed the latest Fiesty 7.04 beta today.
I already have another computer using Ubuntu/Kubuntu 6.10 connecting to my wireless network but this other machine uses a Linksys (Atheros) card.

After installing Fiesty (loving it:D ) I can see my wireless network (ra1) with the little shield beside it and when I click on it to connect I get the passphrase dialog box. My problem is that in the wireless security menu I only get 3 options for WEP security i.e. 128-bit, 64 Hex and 64 Ascii. There is no option for WPA? 
I am sure that the router is set for WPA as I have logged into the router to check and my other machine (Ubuntu 6.10) is using wpa_supplicant etc.

So I checked the Wireless Adapter box thinking that it might not support WPA and it says it supports WEP, WPA and WPA2.

I am out of ideas ... does anyone know anything I can try?
Thanks in advance,
jonny

---

### Post by spd106 on 2007-04-13
Network Manager can have trouble identifying the encryption method if your router is set to not broadcast it's SSID. 

You will probably have to add a new network to get the WPA option. It should not be a problem on subsequent connections.

---

### Post by ericdsr on 2007-04-14
I beat my head against the wall for 2 days trying to get wireless running on my 2nd box under Feisty only to later read that Network Manager is a major issue in that beta release. I ended up going back to 6.10 for now. Hopefully on 4/19/07 the real Feisty will be all shiny and working wirelessly again, it looks great...

---

### Post by huygens on 2007-04-14
The problem with RT61 chipset (and rt2x00 family) is that there driver is not 100% compatible with NM (NetworkManager). See: [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

Only unencrypted or WEP network can be set-up using NM and ralink rt2x00 chipset.

If you want to use WPA or WPA2, you will need to deactivate (remove) NM and set-up WPA in the configuration file manually. Check the forums for threads about RT61 or RT2x00 and WPA.

---


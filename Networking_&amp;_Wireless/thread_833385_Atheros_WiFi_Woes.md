---
title: "Atheros WiFi Woes"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by TheZorch on 2008-06-18
I previously had a video problem on my laptop which is now corrected.  Had to do the same fix on my desktop.  This is a new problem.

My Acer Aspire 4520 has an Atheros AR5007EG 802.11b/g Adapter (242x chipset) in it.  After installing Ubuntu 8.04 jockey-gtk (Hardware Drivers on the Administration menu) reports that the drivers "Support for Atheros Hardware Abstraction Layer" and "Support for Atheros 242x 802.1x Wireless Adapter" are both Enabled and In Use.  However, under Network in the Administration menu all I see are Wired Connection and PPP Connection.  I haven't been able to find an interface in Ubuntu which will allow me to configure a WEP connection to my router (the WPA2 it has isn't compatible with our Nintendo Wii so we need to use WEP).  I've also installed ndiswrapper and used the Windows XP drivers for this device.  ndiswrapper installs the drivers and reports that the device has been found, however I still can't configure it in any way.  I tried the guide on how to setup a Wireless Connection without using the Network interface, but that didn't help either.  

I really need help getting this to work.  My laptop is dual booted with Vista and Hardy, and I'm using Hardy as my main OS.  I also use Ubuntu on my desktop system which has a wired connection.

---

### Post by Dizzle7677 on 2008-06-18
Sounds like all you have to do is deselect the Atheros drivers [pci and hal] under Hardware Drivers and blacklist the atheros_pci. In a terminal do 'sudo gedit /etc/modprobe.d/blacklist' add 'blacklist ath_pci' to the bottom of the file. The 64-bit windows drivers I use are at [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz). If you use 32 bit use these [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz). did you install the ndis stuff - (ndisgtk, ndiswrappercommon,ndiswrapper-utils) ?

---


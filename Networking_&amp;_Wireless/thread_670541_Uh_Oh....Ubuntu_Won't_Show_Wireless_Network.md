---
title: "Uh Oh....Ubuntu Won't Show Wireless Network"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by NuNn DaDdY on 2008-01-17
When I installed the ndiswrapper on the HOWTO I went to see if it worked, however when I click on the wired connection to switch to my wireless connection it no longer shows up and I cannot find it. What would I need to do to get it working or how would I get back to where I started before I installed ndiswrapper.  I tried to locate the directory where ndiswrapper was installed but I couldn't find it. When I tried "locate ndiswrapper" I didn't really have anything useful come up.

---

### Post by PhaderSYD on 2008-01-18
I am using ndiswrapper drivers too, network manager is not very good IMO, I prefer Wicd manager (attached), make sure you remove network-manager from synaptic package manager first.

Also you can check wireless in terminal:
sudo iwconfig - shows wlan0 connection status
sudo iwconfig wlan0 essid <networkname> - connects to network
sudo iwlist wlan0 scan  - scans for wireless networks




Ndiswrapper installations are stored in /etc/ndiswrapper/
To remove drivers:

sudo ndiswrapper -r <drivername>

---


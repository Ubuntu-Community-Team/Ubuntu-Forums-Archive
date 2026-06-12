---
title: "Got WIreless to Work - Hardy with D-Link PCI card"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by dumb?don on 2008-09-03
I am new to Linux and am trying out Ubuntu to see if I could use an old, old system to connect to the internet.  It is working, but not perfectly.  This may help other new users.

SHORT VERSION:
1. Use Ubuntu website to select card that works (I chose D-Link WDA-2320)
2. Install card and reboot.  Should automatically detect.  Can confirm with system - administration - hardware drivers, look for Atheros HAL and Atheros 802.11.
3. Try connecting to the internet.  Mine did not connect.
4. Use system - administation - network to see if your wireless network shows up.  Mine didn't.  If it does, select it and go to step 7.
5. Highlight wireless connection, then click on properties and uncheck enable roaming box.  Use pull down menu to find your network.  Go to configuration and use pull down menu to set automatic configuration (DHCP), (enter WEP, WPA passwords if appropriate)
6. Click okay to save changes.
7. REBOOT system
8. Should work - can use system - administration - network tools to ping a website ([www.google.com](www.google.com) or [www.yahoo.com](www.yahoo.com) for example) if needed to make sure you are communicating.

LONG VERSION:
I used the Ubuntu website to find out which cards seem to work with the least amount of problems and chose to use a D-Link WDA-2320 PCI card.  Picked it up at the local Office Depot for about $50.  Installed the card and got an indication that the card was recognized automatically (system - administration - hardware drivers showed Atheros HAL and Atheros 802.11 support were installed).  But couldn't connect to the internet.

The Ubuntu website mentions running a command that installs madwifi-tools, but I kept getting an error saying the file couldn't be found (still have no idea where it is at). An aside for those new to Ubuntu - to open a terminal window use applications - accessories - terminal. This could be why the system isn't working correctly, but who knows.  Followed a lot of the troubleshooting information and ran config, etc. and everything looked like it should, but still no internet.

Opened up Network (system - administration - network), my network did not show up automatically so I highlighted wireless connection and clicked on properties, unchecked the enable roaming box, used the pull down menu to find and select my network.  I don't used WEP or WPA so I didn't need to enter any additional information.  Used the pull down menu in the configuration box to automatically configuration (DHCP).  Clicked okay.  Still no internet connection.  Gave up and tried again the next day.  Used network tools (system - administration - network tools) to ping [www.google.com](www.google.com) and it worked.  I did some experimenting and it seems as though after disabling roaming and selecting your network, you MUST REBOOT the system for the changes to work.

Good luck.

---


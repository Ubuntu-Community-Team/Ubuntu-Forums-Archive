---
title: "How to re-run wireless autoconfiguration"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by zmxncbv on 2008-03-19
Very new linux user.  Installed Kubuntu 7.10 on HP Pavillion zd8000.  The automatic configuration properly found and configured the wireless adapter, and once the proprietary drivers were activated, wireless networking worked correctly with one exception: on each login to the WPA wireless router it was necessary to reconnect to the network manually by right-clicking on the system tray KNetworkManager icon and selecting the named wireless network.

In a misguided attempt to automate the wireless network reconnection, I selected the manual configuration option from the KNetworkManager icon's right-click menu, selected the  wireless interface (eth1), selected "Configure Interface," from the pop-up window selected "Activate when computer starts" and "Automatic."  Upon saving, not only did the system not reconnect automatically, it was unable to connect at all.  I was also unable to undo this change, as once either Automatic or Manual is selected in the "Configure Device eth1 - KDE Control Module," no option is available to again de-select both.

While poking around looking for a solution to the above screw up, I further admit to right clicking on the KNetworkingManager system tray icon and selecting Options>Configure, and  after selecting the Wireless Networks tab, selecting and removing the profile for the trusted wireless network, hoping the system would then rediscover and create a new profile.  Now, when right-clicking on the KNetworkingManager icon, no networks, wired or wireless are offered, and the only options are "Manual Configuration," "Options," "Help," and "Quit."  I have also tried both Wifi-Radar and Wireless Assistant without success.  Both find my wireless router, as well as many others in the neighborhood, but are unable to connect to any, including open access points.

Is there a simple way to delete all networking configurations and let the wireless networking autoconfiguration routine from the installation setup reinstall networking as it was?  Is there another solution to determine and correct everything I have screwed up, both with the initial mistakes detailed above, as well as anything else I have now done in trying to repair the damage?

Absent a solution from this forum, my next attempt will be to just delete Gutsy, and attempt a fresh install when Hardy is released next month, since I know the Kubuntu installation correctly (and amazingly) detects and installs *everything* on this notebook.

Thank you in advance for any assistance.

---

### Post by Denizen08 on 2008-04-13
I have the same problem. I want to re-enable auto configuration of wifi management on my laptop.

My case is the same as yours, although my wifi device is an Intel PROSet/Wireless 2100/2200 (or sumthing close to that, sorry I've forgotten). My device works properly under Windows and Kubuntu, but I am having problems with connecting to WEP enabled wifi infrastructures (routers, I guess) and just randomly connects to my neghbor's... I really want to have this fixed without having to reinstall the entire OS.

Could there be a small configuration file for kdenetwork that I can delete and have it regenerate the file to default values in the root directory or ~/... ? I'm sure a fresh install of the OS is unnecessary for this trivial task.

---


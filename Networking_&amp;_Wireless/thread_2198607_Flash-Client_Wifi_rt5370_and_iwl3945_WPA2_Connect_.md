---
title: "Flash-Client Wifi rt5370 and iwl3945 WPA2 Connect but no Internet"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by beartham on 2014-01-09
Hello, 

I am seeking to start a collaboration project to solve the Linux Wifi issue, once and for all.](*,)

**Universal XCS Client Portal Appliance Collaboration Initiative**:idea:
 
I am testing a live usbflash Ubuntu 12.04 LTS appliance intended for plugging into arbitrary laptops, converting them to X-Client hosts as terminals to a Ubuntu 12.04 cloud server used for scientific development and as a cluster-supercomputer interface executive. It is to become an X-client-server (XCS) client part of a cloud front-end portal for end-user interactive scientific modeling and application prototyping. 

*_** Unified XCS Front-End for Auto-Interaction**_* - The idea is to share the desktop look and feel on both client and server, as a front-end image. We are developing "auto-interactive" server-side interfaces (CLI Menus and Gtk-GUIs) which automate higher-tier development Perl scripts to setup and drive comparative modes of gang editing using Meld and gang-editors like Jedit, Kate, and Geany in concert with Konqueror (for example see these wrappers for [Glade]("http://www.metacalculus.com/Metacybernetics/EG.html") and [Yacc]("http://www.metacalculus.com/Metacybernetics/GAEMY.html")). Over time we intend to migrate appropriate portions of this auto-interaction to the X-client appliance.

As my colleagues and I are focusing on this server-side work, we are seeking to collaborate with a sysadmin team who would handle Wifi driver issues and maintain this X-client live-flash host. This could even be a business for this team to distribute these usbflash appliances with the kind of reliable Wifi performance enjoyed by Windows or Mac users, but not Linux users today. What I would like to see is the kind of setup reliability I have experienced with Puppy Linux. But I prefer the KDE 3.5 fork, Trinity.

We believe this XCS WAN approach will see a renaissance in the near term, as a departure from the web-brower/server WAN model, due to its superior interactive capability, front-end/back-end GUI/CLI intimacy, and overall simplicity. 

*_**The Wifi Problem I want hand-off to somebody**_* - In my testing with the usbflash appliance, I have no problem with ethernet, but I have not been able to get Wifi working with either the laptop's internal PCI adapter wlan0 (Intel PRO/Wireless 3945 ABG/BG) or an external usb dongle wlan5 (Ralink rt5370). I can connect to my Wifi router (Linksys 4200) with both using WPA2 via the wpa_supplicant configured by wpa_gui. I use wifi-radar as the user interface, to scan and connect with both adapters. But I cannot browse with either on the Internet, even though I have no problem with an identical laptop running Windows VISTA on the same subnet.

My laptops are old HP pavilion dv6000 core-duo T2250s, and I use a Belkin 7-port usb switch to connect the wlan5 Ralink dongle. The first time I tried it, the Ralink dongle did work. But after I rebooted the flash drive, it did not continue.

I would appreciate some expertise in dealing with this problem now. And I would like to invite people to join in collaboration to make this appliance universal.

TIA,:)

beartham (Joseph Thames), Santa Fe, NM

---

### Post by chili555 on 2014-01-09
> I have not been able to get Wifi working with either the laptop's internal PCI adapter wlan0 (Intel PRO/Wireless 3945 ABG/BG)I'll be happy to troubleshoot that; I have one and it performs beautifully for me. 

Is Network Manager running here? If not, why did you decide to use wifi-radar, etc. instead?```
ps aux | grep -i network
```If NM is not completely removed, it will be somewhere between extremely difficult to impossible to wrest control of networking from it.

Are there any clues here?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```Ideally run after you tried and failed to connect with wireless only.

---

### Post by beartham on 2014-01-09
Thank you Chili555,

Well now I'm embarrassed. Wlan0 is working with the ethernet unplugged and the Wlan5 dongle unplugged. I'm going to do some more testing.

Network Manager is running.

I chose wifi-radar because it has a simple interface that goes with wpa-gui, and has a nice popup that tracks wpa_supplicant and dhclient calls. So I thought it would be a warm-fuzzy for my end-users who are not Linux types.

Expecting trouble, I had installed practically all Wifi packages Synaptic had. Then when wifi-radar worked the first time with wlano, I uninstalled wicd because it was a memory hog.

I'm building these flash drives to send to my QA-users, who are senior scientists, but mostly Windows users, now.

Since I don't know what laptops they have, i want generic drivers that have a large footprint, like rt2800usb for the Ralink dongle that I can have the buy on ebay for about 5 bucks.

I would appreciate any advice.

Thanks,

Bear

---

### Post by chili555 on 2014-01-09
I'm not sure what could be simpler than NM. A balloon pops up to tell you that networks are available, you click on the network you want, supply the WPA password and connect. I was a hater myself for several years until a 70-something lady under this very roof exclaimed, "Oh, cool, I'm connected!" Has that not been your experience? [http://www.techotopia.com/images/d/de/Ubuntu_10.10_networkmanager_menu.jpg](http://www.techotopia.com/images/d/de/Ubuntu_10.10_networkmanager_menu.jpg)

I'm not sure I could recommend the $10 USB devices that use rt2800usb without a little work. We get a lot of can't-connect, drops, slow complaints about the rt2x00 suite. [http://ubuntuforums.org/showthread.php?t=2150086](http://ubuntuforums.org/showthread.php?t=2150086) for an unsolved example.

I've had some luck installing the backported driver from 3.12.2. I'd be happy to work with you on that if you'd like.

---


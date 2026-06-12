---
title: "Error: The System Network Services Are Not Compatible With This Version"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by kernelles on 2015-11-01
Fresh install of Ubuntu 15.10 x64 on my Asus K52J laptop. Networking setup worked fine, until I rebooted. Now, missing networking applet, and attempts to access networking through system settings result in the error message, "The system network services are not compatible with this version." I am still connected to the network, as it connects automatically. But I can't connect to a new one, at least with the GUI. This laptop has never had an issue with any previous releases of Ubuntu. Can anyone post a solution for me?

---

### Post by kernelles on 2015-11-07
Anyone...?

---

### Post by ozmagoo on 2016-02-11
I've got exactly the same issue - 15.10 64 bit on an AMD Phenom desktop system...   No applet on status bar, can't access network settings from System Settings...

Machine was up, then just suddenly dropped off the network...  Won't get an IP address over DHCP...  repatched it into switch... still ongoing....

Also - as root unable to ifdown the interface (enp3s0 - P.S. I really hate the new ethernet device naming schema!)...

I'm worried it's going to happen now with my Asus UX501 laptop too - built both at the same time - pretty much get updated together...

---

### Post by ozmagoo on 2016-02-11
Update - I removed ALL PCI NICs from my machine, left it just using the on-board NIC - apt-get update, apt-get dist-upgrade, apt-get autoremove...  rebooted...

Still no fix... I've worked around my issue (had to dedicate an IP address on my DHCP server for the NIC) - but it's still not running the status-bar applet and complains about [COLOR=#000000] "The system network services are not compatible with this version."....

[/COLOR] Linux gilgamesh 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

I don't need WiFi on this box - but if the same thing happens on my Laptop I'll be looking at an O/S re-install...  probably go back to 14.04 LTS (or Elementary).

[COLOR=#000000]


[/COLOR]

---


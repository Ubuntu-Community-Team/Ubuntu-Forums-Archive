---
title: "Edgy Kubuntu Forgets ESSID"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Thund3rstruck on 2006-10-29
Hi guys,

Quick question... everytime Kubuntu 6.10 boots it forgets my WiFi ESSID and I have to manually set it with iwconfig or the settings applet in order to bring the network up. What can I do to make the system remember my ESSID?

The GUI applet for the network has the name of my ESSID in it, but iwconfig says that my ESSID is unmanaged or something like that until I change it manually and then bring the interface down and up again.



Thanks

---

### Post by supermihi on 2006-10-29
You could try knetworkmanager if your card's driver is supported by NetworkManager. knetworkmanager stores ESSIDs and WEP/WPA keys in the KDE wallet.

---


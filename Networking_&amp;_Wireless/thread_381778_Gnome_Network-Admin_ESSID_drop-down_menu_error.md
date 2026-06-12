---
title: "Gnome Network-Admin ESSID drop-down menu error"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by saveryquinn on 2007-03-11
I'm running Edgy on a Dell Inspiron 6400 duo-core using NDISwrapper to run the internal Broadcom  BCM4401 wireless.  While the wireless runs fine, I've had one annoying quirk to the wireless I'm curious if anyone has run into before.  To connect to wireless in a public location, I have ended up having to use a combination of WiFi Radar and the Gnome network-admin tool.  Why?

1. The Gnome network-admin tool's dropdown list of detected ESSIDs for wifi fails to display any detected wireless networks.

2. On the other hand, WiFi radar lists every wireless network available even those with extremely low signal.

So, to connect to a public wireless network I have been opening WiFi Radar to detect accessible networks.  WiFi Radar cannot by itself connect to any detected network.  Then opening Gnome network-admin I type in the ESSID of a selected wireless network.  Gnome network-admin then connects to that network.  WiFi Radar will then accurately report my connection status to that given network and my DHCP assigned ip addy.  

Is this a software conflict between the two programs?  I tried uninstalling WiFi radar, re-installing network-admin, but the quirk persists.  Is it a ndiswrapper issue?

Any suggestions will be pursued!  Thanks!

---

### Post by Algoritm on 2007-03-12
I have the same problem. Onboard wifi, P5AD2 premium motherboard.

---

### Post by Michael Cornelius on 2007-03-12
I have the same problem: Dell Precision M60 laptop, Intel WM3B2200BG (PRO/Wireless 2200BG).

```
sudo iwlist eth0 scan
```

The above command will list the ESSIDs in the area, but the the dropdown in network-admin has no entries. I can enter an ESSID manually in the network-admin combobox, after which it will associate with and use that wireless network.

---

### Post by Michael Cornelius on 2007-03-13
Known problem: [https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159)

---

### Post by weijie90 on 2007-03-26
Try commenting all the lines that  don't contain "lo" in /etc/network/interfaces

---


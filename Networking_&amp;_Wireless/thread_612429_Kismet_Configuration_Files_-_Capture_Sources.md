---
title: "Kismet Configuration Files - Capture Sources"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by rockstar on 2007-11-13
I have a very specific question to ask about Kismet configuration.  I cannot figure out what line to put in the capture sources line.

Using the Kismet documentation I've found I need the following parameters: 'source=type,interface,name[,channel]'

I have a Linksys WMP54G pci adapter

Using iwconfig I determined that the interface would be - wlan0

I know that the Linksys card uses a RALINK chipset.  I thought when I bought this that it would be compatible, but according to the Kismet website there are more than one version of this card and this chip.

Under Kismet Capture Sources Documentation i found several Ralink drivers that were supported, however my RAlink was different then there drivers.

I am so confused, can anyone help me sort this out?

---

### Post by henriquemaia on 2007-12-08
bump

---

### Post by rockstar on 2008-03-31
Turns out my WiFi card wasn't compatible.  I used kismet forums to find that out.  Now I have to buy another wi-fi card

---


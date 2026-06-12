---
title: "Cannot print to USB printer via wireless router"
date: 2017-12-02
forum: Networking &amp; Wireless
---

### Post by somebody.on.earth on 2017-12-02
BACKGROUND: I have a Canon E400 USB printer connected to the USB port of my D-Link DSL-2750U wireless router. My laptop running Ubuntu 17.10 + Win10 (dualboot) is connected to that router via wifi. The network address seems to be **[http://192.168.1.1:631/printers/E400](http://192.168.1.1:631/printers/E400)**. I am trying to print to this printer wirelessly. 

The funny thing is that when I ping 192.168.1.1:631, both in Ubuntu and Windows, it fails saying it doesnt exist. But I can surely add the printer with the same address "http://192.168.1.1:631/printers/E400" and even print pages successfully!! :confused:
 Any explanation for this ? 

In ubuntu, I can add the printer but I cant print anything. When I try to print, I get errors like **cups-ipp-missing-validate-job**, **cups-ipp-missing-job-id **and **cups-ipp-missing-printer-state-reasons**. When I try to add the printer, I get 2 drivers under Canon > E400 : "Canon E400 series v4.10 (recommended)" and "Canon E400 Series - CUPS+Gutenprint v5". I've tried adding with both the drivers and also the Generic Text Only driver, but to no avail.

[I]For info: 
I've already installed the latest printer driver available from Canon's website
I can print via USB without any issues
There's a green tickmark over the printer name in printer settings[/I]

Please help. Any logs or more info can be provided if required.

---


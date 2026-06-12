---
title: "My wifi adater is there, but the network-manager doesnt recognise it"
date: 2024-07-15
forum: Networking &amp; Wireless
---

### Post by twabcxyz on 2024-07-15
Sorry for this format-crap, im new to this forum and bb-code-tag doesnt seem to work. My wifi worked before i upgraded to Ubuntu 24.  This is the output of  sudo lshw -C network __  ```
   *-network          Beschreibung: Kabellose Verbindung         Produkt: Comet Lake PCH-LP CNVi WiFi         Hersteller: Intel Corporation         Physische ID: 14.3         Bus-Informationen: pci@0000:00:14.3         Logischer Name: wlan0         Version: 00         Seriennummer: 94:e6:f7:63:55:1a         Breite: 64 bits         Takt: 33MHz         Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical wireless         Konfiguration: broadcast=yes driver=iwlwifi driverversion=6.8.0-38-generic firmware=77.206b0184.0 QuZ-a0-jf-b0-77.u latency=0 link=no multicast=yes wireless=IEEE 802.11         Ressourcen: iomemory:600-5ff irq:16 memory:6025104000-6025107fff   
```  __   However, if I go to the system settings, the page just shows 'no wifi adapter found' How can I solve this?   a

---

### Post by coffeecat on 2024-07-15
> **twabcxyz said:**
> bb-code-tag doesnt seem to work. 

Welcome to the forum. 

BBCode is working just fine. You are probably using a browser add-on/extension which is breaking forum functionality. A good start in finding the culprit is anything that interferes with javascript. The noscript extension is a notorious repeat offender in this regard.

---

### Post by jeremy31 on 2024-07-15
See the wireless script link in my signature and post results

---


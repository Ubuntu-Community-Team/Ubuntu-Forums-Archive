---
title: "[SOLVED] cannot wifi to d-link dir-615, can to other routers"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by gwoodruff on 2008-08-19
Howdy, I have a weird one.
I have a D-link dir-615 that I cannot get Ubuntu to wifi to. ( wife can / vista WPA2).
I  cannot establish a connection unencrypted or encrypted wpa1 or 2.
I have a 2nd router (siemens) that I can wifi to with same config files and settings. (unencrypted, wpa1&2).
When attempting to connect to the d-link the link light does not come on after issuing the wpa command as it does with the simens router. I have attached wpa_suppliant.conas well as output from debbuging with command line (wlog). Any help would be greatly appreciated.

Thanks, Gary
.

---

### Post by gwoodruff on 2008-08-27
I have it working now. I un-installed ndiswrapper and used madwifi for the driver. I also tried Wicd for the manager. I could get Wicd to connect but it used alot of processor and memory (fan would start at launch of Wicd and system slowed way down). I reverted back to network-manager and everything works fine with the exception of no link or activity lights on the wifi card (dlink dwa-645), They did work with the ndiswrapper and the win driver. I am still puzzled why I could connecet to one router but not another using same security settings!

---


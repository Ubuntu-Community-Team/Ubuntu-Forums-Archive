---
title: "P5B-MX Wifi-AP"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Radomir on 2007-05-12
I installed Feisty almost a week ago on a new computer, and everything is working smooth - except wireless. Feisty recognizes that there is a card, after sudo update-pciids saya it's an Atheros 5006 EG card, but it's not working with madwifi in linux-restricted so i uninstalled and try to install drivers from latest madwifi snapshot, but failed. I can modprobe ath_pci, but interface is not visible, and I get kernel panic random on boot. Was anyone able to get wireless on this mobo working? I see it is supported on mad wifi page, [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)...

---

### Post by stchman on 2007-05-14
> **Radomir said:**
> I installed Feisty almost a week ago on a new computer, and everything is working smooth - except wireless. Feisty recognizes that there is a card, after sudo update-pciids saya it's an Atheros 5006 EG card, but it's not working with madwifi in linux-restricted so i uninstalled and try to install drivers from latest madwifi snapshot, but failed. I can modprobe ath_pci, but interface is not visible, and I get kernel panic random on boot. Was anyone able to get wireless on this mobo working? I see it is supported on mad wifi page, [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)...

Follow the procedure I have laid out on my site to get Atheros cards and madwifi working.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

This worked on my laptop.

Hope it helps you.

---

### Post by amoocool on 2007-06-26
I have the same mobo i followed the instructions on the website but still my wifi is not detected. While booting there is an line which says 'this revision of hardware not supported'.

---

### Post by amoocool on 2007-10-04
got it working with ndiswrapper 1.48 with net2425.inf net2425.sys and aw5006.cat driver files fom xp.Works well with ar5007eg driver files too. Don't install madwifi if installed uninstall madwifi.

---


---
title: "Ath9k on AR5416"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by LittleKoy on 2008-09-10
Am I the only one who's having troubles with ath9k on a AR5416-based card? It connects, but the connection comes and goes as it wants... I didn't have this problem when I was using ndiswrapper

---

### Post by awwong on 2008-09-12
No, I'm having similar problems using kernel 2.6.27-rc3.  I'm trying to upgrade to rc6 to see if the connection stability improves.

---

### Post by oobe-feisty on 2008-10-18
was wondering if you guys have had any luck on this im about to install the 
Ath9k for AR5416 wmp-300n linksys and wanted after i finish compiling a new kernel are the any recent updates that have fixed this

---

### Post by tatrefthekiller on 2008-10-21
Did you try with Intrepid (Ubuntu 8.10) ? It contain the 2.6.27 kernel with ath9k. It should work out of the box.

---

### Post by pseudorandomname on 2008-12-14
I have also been seeing these issues with my AR5416 (Dlink DWA-552) when the connection works it's fast, but it seems to stall randomly.  NetowkrManager doesn't "drop" the connection, the packts just stop getting through.  I've seen this problem on every Intrepid kernel I've tried to date.  I was so frustrated I went back to Gentoo, but I am seeing similar problems there.  All 2.6.27 kernels, all ath9k drivers.

---

### Post by mrtn86 on 2009-06-04
is there any improvements with *AR5416* chipset and ath9k drivers? I am planning to build a 802.11b/g/n WAP using **D-Link DWA-547** card. As much as I have researched, there is no other PCI 802.11b/g/n card, which supports ath9k drivers and *master mode*. However, any comments about *AR5416* and ath9k on latest drivers/kernel releases? ;)

---

### Post by berland on 2009-08-25
I am also planning to build a WAP (wireless access point), and thinking of buying DWA-547 (EU-version with AR5416). Did you have a go at it?

---

### Post by pseudorandomname on 2009-08-25
I still have not had any great success with this chipset under ubuntu.  My wireless performance under windows is excellent, but it is so bad under Ubuntu as to be essentially unusable.  I try again every few weeks, but so far there have been no significant improvements.

---


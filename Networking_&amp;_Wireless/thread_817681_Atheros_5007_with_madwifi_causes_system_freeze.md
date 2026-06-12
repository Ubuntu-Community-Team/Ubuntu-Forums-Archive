---
title: "Atheros 5007 with madwifi causes system freeze"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by henkeb on 2008-06-03
Hey guys. Really weird problem, I recently got my onboard atheros wifi to work using the madwifi-r2756-something-something driver after many hours of painful googling and trial-and-error. But now for the strange part, after a while (15,30 mins, an hour, it varies) my system will start lagging (I'm on an LG E500 laptop), sometimes freeze and also it will not detect any wireless networks. I'm pretty sure it's the wifi because if I try to remove the ath_pci module with modconf I get an error message saying: couldn't remove ath_pci, segmentation fault or something like that. If I reboot I can remove the module and the lag/freezing stops.
Any ideas? I've been searching the forum and googling but to no avail.

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by henkeb on 2008-08-22
Thanks a lot, gonna try that right away.

---


---
title: "Gutsy Madwifi-ng aireplay-ng injection"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by echodep on 2007-11-15
Hi all, I have a Ubiquiti SRC Atheros card that I'm struggling to get airepay working with.  I've removed the restricted Madwifi driver and installed Madwifi-ng from SVN, Aircrack r2277 patch and aircrack-ng 0.9.1 from source.  Monitor mode works fine with airodump and kismet but when I try to do a replay test the machine locks up.  I've also added ath_hal to /etc/default/linux-restricted-modules-common, although ath_hal still seems to load.  I don't get any errors in dmesg when the card is inserted and after the crash there is nothing of value in syslog.

Are there any further troubleshooting steps I can take?

thanks, Echo.

update....

If I create a VAP with airmon-ng start wifi0 11, I get an error Error for wireless request set frequency.  It does create a VAP ath 30+ but fails to put it into monitor mode.  If I destroy this VAP and try again everthing seems to work correctly and a VAP is created as ath0.  iwconfig confirms that it is in monitor mode.  I try aireplay -n test and the machine locks up.  If I create the VAP with "wlanconfig ath create wlandev wifi0 wlanmode monitor -bssid" the VAP is created, airmon-ng doesn't lock but it doesn't find any networks during the test.

---

### Post by notnhatknot on 2007-12-25
could you tell me exactly how you removed the restricted drivers and installed latest madwifi from svn? I cant seem to get it right on freshly installed version of ubuntu gutsy 7.10.

---


---
title: "ASUS EEETOP RTL8192SEVA Hard Blocked"
date: 2017-09-04
forum: Networking &amp; Wireless
---

### Post by dvboom on 2017-09-04
I have an ASUS EEETOP with a Realtek RTL8191SEVA wireless built-in, reported hard-blocked by rfkill.  Some details: 

1. rfkill unblock all doesn't work
2. Reboot into Windows - wifi works perfectly. 
3. Wireless lamp is lit on the computer.
4. Network Manager Enable Wireless option is grayed out. 
5. No combination of FN-x keys work to enable the wireless.
6. dmesg: rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
               Loading firmware rtlwifi/rtl8192sefw.bin


I have loaded various flavors of Ubuntu, (currently Lubuntu 17.10), all have the same result. 

Is this a driver / firmware issue?  Sorry to dredge up an old PC compatibility issue, but I am trying to get it working to donate it.

---

### Post by ajgreeny on 2017-09-05
See Wireless-Info in my signature below and follow the info there to run the script and show us the report you get from it.
Someone who is more expert than I with wifi will no doubt be able to help you sort this out.

---

### Post by dvboom on 2017-09-05
Thank you, here is the result of the wireless-info script: [http://paste.ubuntu.com/25474798/](http://paste.ubuntu.com/25474798/)

Also, if I run modprobe -rv rtl8192se; modprobe -v rtl8192se the network manager enables wifi, and connects to my access point, then after about 5 seconds, goes back to "hard blocked" / disabled state.   During the 5 seconds the wireless is available, I can see a list of access points, then it all goes back to disabled. 

Thank you for any help.  I have tried just about everything I could find after weeks of googling.

Here is the result of my modprobe experiment: 

rmmod rtl8192se
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
insmod /lib/modules/4.10.0-33-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.10.0-33-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
insmod /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko 
insmod /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192se/rtl8192se.ko

---


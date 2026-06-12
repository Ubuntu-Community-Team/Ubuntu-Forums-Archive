---
title: "Broadcom Woes"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by htmlguy716 on 2006-07-27
I recently installed Ubuntu 6.06 LTS on my PowerBook G4. After I installed the OS, I updated all the software, and started setting up my (dare I say it?) Broadcom bcm43xx AirPort card. I installed the firmware using bcm43xx-fwcutter, then I installed network-manager-gnome. My wireless card can scan for nearly networks, but when I attempt to connect to an open network using NetworkManager, it will say "Attempting to join the wireless network 'my network'..." for about 30 seconds, then fail. Any ideas?

---

### Post by philippe_carlo on 2006-07-27
```
sudo apt-get install wifi-radar
```

Application->Internet->WiFi radar

Once I set up a profile, it connect automatically when I log on.

---

### Post by htmlguy716 on 2006-07-27
Thank you very much for the pointer. Unfortunately, when I try to connect using wifi-radar, it will find and connect to the network, but not obtain an IP address. I know this is wrong because the gateway already provides DHCP to several computers.

I am aiming for getting my WiFi connection to work with WPA 2.0 eventually, but I am leaving my wireless network unsecured until everything is set up.

---


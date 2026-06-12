---
title: "MadWifi Drivers on VAIO VGN-NR140E"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by D1SoveR on 2008-11-15
After installing Ubuntu on my laptop for the first time, I've discovered a problem.
While wired network device is functional out-of-the-box, wireless LAN, even with some
restricted drivers, didn't seem to work (no network devices came up with iwconfig).

After doing some research, I've stumbled into [**_this_**]("http://admc.com/confluence/display/tech/OpenSUSE+11.0+on+the+Sony+VAIO+VGN-NR310E?forum=9") tutorial. Although written
for different laptop and different Linux distribution, NR310E has very similar WLAN chipset.
I've downloaded MadWifi drivers, compiled them and installed them. After activating newly
compiled kernel module (with "modprobe ath_pci"), iwconfig showed two additional devices,
wifi0 (dummy interface) and ath0 (functional wireless device). It seems to be working,
as returned ESSID is "PENTAGRAM P6331-4A" (one of networks available under Windows XP),
but two problems arise. First, how can I expose ath0 interface to Ubuntu 8.10 Network Configuration Manager?
It doesn't seem to show up after activating the module. Second, is there any way to avoid modprobing
manually everytime I reboot the system?

---

### Post by buccaneere on 2008-11-15
Network - restart-at-boot script here:

[http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---


---
title: "Ourlink 1200mbps adapter need help"
date: 2019-06-09
forum: Networking &amp; Wireless
---

### Post by Rumbl3 on 2019-06-09
Been a long time since I've been on linux. Made the jump back the other day. Anyway trying to get this internet adapter working and finding a lot of mixed info on the web about it and some seems outdated. Like a noob all over again here! 

Anyway this is what turns up in lsusb

Bus 002 Device 004: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter

How do i get this installed and working currently running the latest LTS 18.04 

Any help would be greatly appreciated!

---

### Post by jeremy31 on 2019-06-09
In terminal
```
sudo apt install git build-essential dkms
git clone https://github.com/jeremyb31/rtl8812au-1.git
cd rtl8812au-1
sudo ./dkms-install.sh
```
Reboot and see if Secure Boot is disabled in UEFI/BIOS settings, don't delete any Secure Boot keys

---

### Post by Rumbl3 on 2019-06-09
Update think it might be the system itself. Have to run some diagnostics old tower from the basement. Freezing up and bsod on windows also. 

thanks started working then seems to possibly go out after a few minutes and cant find any networks. Going to mess with it see what i can find on google. Thanks farther then i made it on my own :)

---


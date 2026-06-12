---
title: "ndiswrapper problem"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by thescholar on 2008-03-03
I just built myself my first pc and threw ubuntu in it because i wanted to try it out. I bought a Rosewill Wireless PCI card and installed ndiswrapper from the boot cd. I went threw the steps someone laid out on newegg for the card and he said it worked perfectly, these were his steps...

Linux Ubuntu tips: - This what the 'lspci' will show: Ethernet controller Marvell 88w8335 [Libertas] 802.11b/g Wireless (rev 03). 'lspci -n': 11ab:1faa (rev 03). - Install ndiswrapper (I used version 1.50). Use Xp drivers on disk provided: Netmw126.inf for Linux 64bit, Netmw125.inf for 32bit. However, I found another driver for 32bit that works well: Mrv8335.INF - Then type the following to install "driver": sudo ndiswrapper -i "driver".inf ...sudo ndiswrapper -m ...sudo depmod -a... sudo modprobe ndiswrapper - You need to restart after the depmod.

alright i followed those steps. it says that driver is installed, i must have did the sudo ndiswrapper -m last nite because it says, module configuration already contains alias directive. then i put sudo depmod -a and nothing happens which i think is supposed to happen. i restart then put in sudo modprobe ndiswrapper and get something with FATAL error- and a whole bunch of stuff after it. i would have put the stuff but when i put sudo modprobe ndiswrapper in now nothing happens. i am obviously new here and have no idea how to use this yet. i have no internet connection to that pc right now. any help would be appreciated.

---


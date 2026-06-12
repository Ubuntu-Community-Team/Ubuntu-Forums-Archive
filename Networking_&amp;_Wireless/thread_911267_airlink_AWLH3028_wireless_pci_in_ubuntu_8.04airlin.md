---
title: "airlink AWLH3028 wireless pci in ubuntu 8.04
	
airlink AWLH3028 wireless pci"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by sso71 on 2008-09-05
I installed ubuntu 8.04. I have an airlink AWLH3028 wireless pci card with Realtek 8185. It works under windows. The [document]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#PCI") said it should be "Supported in installed system" and Works "out of the box" with ndiswrapper. I have the following question:
1. where to see if my card is properly installed and how to start the wireless connection?
2. do I still need to manually install ndiswrapper and the windows driver even though it says "work out of the box"?
Thanks!

---

### Post by eacore on 2008-09-22
run in terminal ifconfig to see if your card is installed there you should see an interface like wlan0 or wlan1, then run in terminal iwlist scan "interface" the inteface should be the one you got from de ifconfig command. this will help you know if the card is properlly installed.

---


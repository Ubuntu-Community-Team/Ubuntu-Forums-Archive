---
title: "ndiswrapper driver vs linux driver"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by AndyPopely on 2007-05-28
On my laptop I have Feisty Fawn as the only operating system on it and use a netgear wpn511 wireless adapter card to connect to my netgear wpn824 router.

I installed the latest version (1.44) of ndiswrapper in order to use the latest windows xp driver for the 
wpn511 adapter and confirmed that ndiswrapper was starting on system startup.

There were 2 issues with network connectivity.

1) The signal strength of the wpn511 shown by Ubuntu NetworkManager was no more than 70% when the laptop was about 2 feet from the router.   When the laptop was about 60 feet from the router the signal strength was no more than 30%.
2) With SSID broadcast diabled on the router and using WPA security the adapter card would never automatically connect to the router.  I would always have to select it from the list and then it would connect.

I discovered that the linux driver ATH_PCI for the Atheros AR5112 chipset for the wpn511 adapter card was being installed instead on the ndiswrapper driver.

I found this out by going to the Device Manager (System -> Preferences -> Hardware Information) then in the "Devices" column selecting the entry above the "WLAN interface" so for me it was "AR5212 802.11abg NIC".  In the right hand column I selected the Advanced tab and the "Info.Linux.Driver" value should have said "ndiswrapper" but instead it showed "ATH_PCI".

To stop the "ATH_PCI" driver from being loaded I added the following entries to the  "/etc/modprobe.d/blacklist" file
blacklist ath_hal
blacklist ath_pci
blacklist ath_rate_sample

After rebooting the "Info.Linux.Driver" value in the Device Manager showed "ndiswarpper".

The signal strength is now 100% when the laptop is next to the router and 50% when 60 feet away from the router.

With SSID broadcast disabled the Ubuntu NetworkManager always automatically connects to the router using WPA security without any intervention from me.

I know from this forum that others are having similar problems in this area and I hope this may help.

---


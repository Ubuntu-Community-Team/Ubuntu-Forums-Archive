---
title: "Cannot connect to some wifi networks"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by betazoid26 on 2016-11-26
Hi,

I can connect to the wireless hotspot of my mobile phone but I cannot connect to my wifi router.
NetworkManager says "wrong key" which is not the case - the wifi password is 100% correct.
If i try to establish a connection with the help of the terminal dhclient seems to crash or so - the cursor goes to the next line and nothing happens then. Authentication appears to work (the step right before dhclient, i. e. iwconfig wlan0 etc.) though.

My wifi device is a Qualcomm Atheros QCA6174A. I am using Ubuntu 16.10 on a usb flash drive. My router is rather old, it uses WPA1 with AES for encryption (this is necessary because of other devices in the network). My laptop is an Acer Aspire V3-372.

Under Windows, everything works just fine.

I have tried to install newer/different firmware (among other things) for wifi, no change. I have also tried to switch the router off and on, since all dhcp-clients are deleted then - no success (at least with NetworkManager). 

Thanks in advance for the help

Anna

---


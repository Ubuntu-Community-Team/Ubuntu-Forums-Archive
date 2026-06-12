---
title: "TP-Link TL-WN725N wireless usb"
date: 2015-02-25
forum: Networking &amp; Wireless
---

### Post by mikitz on 2015-02-25
The internal wireless card isn't working anymore, so we purchased a TL-WN725N usb wifi. But I can't get the new card to work..

Here is what I've done so far (based on a couple online blogs about getting the TL-WN725N working):

- I got the rtl8188eu driver, I was able to generate 8188eu.ko and put it in /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/
- ran depmod -a and modprobe modprobe 8188eu with no errors.
- However ifconfig doesn't show anything for wlan...

Here are the last two lines of lspci
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

The RTL8101E/RTL8102E is the old wireless, the RTL8188CE is the new wireless we are trying to get working..

I found that RTL8192 was being blacklisted so I removed that..

Any suggestions? I am not sure what else to check..

---


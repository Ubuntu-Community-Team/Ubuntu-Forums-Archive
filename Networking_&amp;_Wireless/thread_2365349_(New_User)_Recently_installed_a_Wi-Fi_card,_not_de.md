---
title: "(New User) Recently installed a Wi-Fi card, not detecting wireless networks?"
date: 2017-07-05
forum: Networking &amp; Wireless
---

### Post by lightbeard on 2017-07-05
Hey there! I've been having issues trying to get my device to connect to Wi-Fi ever since I installed an internal Wi-Fi card in it. 

So I'm using an Intel NUC D34010WYK mini PC running ubuntu 16.04 LTS and the card I recently put in is an Intel Dual Band Wireless-AC 7260 + Bluetooth. As of right now, it's acting like before when no card was installed, and unable to connect to any network unless I use an Ethernet cable.

---

### Post by chili555 on 2017-07-05
Let's have a look at some diagnostics. Please open a terminal and run and then post:```
sudo modprobe iwlwifi && dmesg | grep iwl
rfkill list all
iwconfig
```PS - I love love love my NUC!

---

### Post by johndough2 on 2017-07-06
Hi

There is some Intel info

[https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)

Intel® Dual Band Wireless-AC 7260,  4.2+	iwlwifi-7260-ucode-25.30.14.0.tgz	
Intel® Dual Band Wireless-N 7260,  4.2+	


Intel® Wireless-N 7260,  4.1+		
Intel® Dual Band Wireless-AC 7260 for Desktop	4.1+	iwlwifi-7260-ucode-25.30.13.0.tgz

and drivers potentially exist.  So there is hope.

---

### Post by chili555 on 2017-07-06
> **johndough2 said:**
> Hi

There is some Intel info

[https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)

Intel® Dual Band Wireless-AC 7260,  4.2+	iwlwifi-7260-ucode-25.30.14.0.tgz	
Intel® Dual Band Wireless-N 7260,  4.2+	


Intel® Wireless-N 7260,  4.1+		
Intel® Dual Band Wireless-AC 7260 for Desktop	4.1+	iwlwifi-7260-ucode-25.30.13.0.tgz

and drivers potentially exist.  So there is hope.The driver *iwlwifi* has been in-kernel for many years. As well, the needed firmware has been in the package linux-firmware for many years. In fact, the current version is the -17 firmware; the -13 and -14 you link are not needed.

From my machine:```
[    3.236424] iwlwifi 0000:03:00.0: loaded firmware version [COLOR="#FF0000"]17[/COLOR].459231.0 op_mode iwlmvm
[    3.269296] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144

```And:```
$ ls /lib/firmware | grep 7260
iwlwifi-7260-10.ucode
iwlwifi-7260-12.ucode
iwlwifi-7260-13.ucode
iwlwifi-7260-16.ucode
[COLOR="#FF0000"]iwlwifi-7260-17.ucode[/COLOR]
iwlwifi-7260-18.ucode
iwlwifi-7260-19.ucode
iwlwifi-7260-20.ucode
iwlwifi-7260-21.ucode
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode

```If the wireless is not recognized and started automagically, I highly doubt the firmware files are missing or at fault.

My NUC doesn't have wireless, so I can't tell for sure, but I'd suggest that @lightbeard have a look around the Visual BIOS to be certain that there are no settings that enable/disable particular PCI slots and especially wireless.

---


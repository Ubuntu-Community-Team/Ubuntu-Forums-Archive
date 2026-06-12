---
title: "BCM4318 Wi-Fi Issue with Ubuntu 20.04 LTS"
date: 2020-06-13
forum: Networking &amp; Wireless
---

### Post by jamie583 on 2020-06-13
Good Evening

New to Ubuntu so please forgive any stupidity on my part. Got the latest version installed today but can't seem to get my Wi-Fi to work / not showing?

0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
0b:03.0 Network controller: Broadcom Inc. and subsidiaries BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I have tried numerous methods from other posts that date back a little while, but nothing seems to have fixed the issue here. Any assistance anyone can offer with this would be most appreciated, thank you kindly.

---

### Post by CelticWarrior on 2020-06-13
Welcome.
[URL="https://ubuntuforums.org/showthread.php?t=2214110"]
How to install a driver for the Broadcom series of PCI wriless cards[/URL] is the stick thread for all things Broadcom related.
That said yours is so old that even with the driver and the hardware in proper working condition it may not be able to connect to many hotspots.

---

### Post by grahammechanical on 2020-06-13
Not knowing what you have tried, we risk suggesting what you have already tried. With that in mind ... 

1) Is this a laptop?
2) Does it have Windows installed?

It sometimes happens that if WiFi is turned off in Windows it cannot be switched on in Linux.

3) Is the WiFi switched off in the BIOS/UEFI settings utility?

4) When you installed Ubuntu did you tick a box to install non-free/proprietary software? If you did then a proprietary WiFi driver might have been installed. If you did not then open the Software & Updates utility and go to the Additional Drivers tab. Allow time for the utility to search for alternative drivers and you may get a driver for your Broadcom WiFi.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I am not sure if the above link is still relevant as Broadcom were a problem in the past but I am not sure if they still are.

Regards.

---

### Post by jamie583 on 2020-06-13
Yes. Using an old HP Pavilion zd8000 laptop that I had lying around and wanted to use for work.

Windows was installed, but did a Nuke of the hard drive to clear all before formatting when installing Ubuntu.

Wi-Fi is enabled in the BIOS. Also there is a switch on the laptop to turn the Wi-Fi on and off. Nothing happens when on and is not lit up like the rest (it used to light up when working). However when I press it to switch off it puts Ubuntu into Airplane mode.

I did tick that box when I installed Ubuntu and checked since to make sure. Nothing pops up in Alternate Drivers tab.

---

### Post by jamie583 on 2020-06-13
Figured it out. Some posts mention about Blacklisting. I did that when didn't need to. Removed them and now works fine.

---

### Post by leflea on 2020-06-17
Would you be able to tell me what you did that helped?

My laptop is basically useless atm since it can't access the internet, and I really need to for work :/

I've been searching around for hours now and nothing that I've tried has helped and it's starting to get quite upsetting. Glad to hear your problem got solved though, this is tedious.

---


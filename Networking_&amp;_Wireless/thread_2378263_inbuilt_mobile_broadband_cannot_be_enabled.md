---
title: "inbuilt mobile broadband cannot be enabled"
date: 2017-11-21
forum: Networking &amp; Wireless
---

### Post by bennitos on 2017-11-21
Hi,
I've dug up my old Eee pc 1000HG, and installed Xubuntu. I'm very pleased with it, and hoping to take the netbook with me when I go traveling to Mexico soon. However, I'd really like to get mobile broadband working for that. My eee PC 1000HG has a built in card for mobile broadband - model is 'Huawei EM770' I think. l'm running Unbuntu 16.04.3 LTS and xfce.

My Problem: Network Manager shows Mobile Broadband and 'Not Enabled' below that, both greyed out, and I can't seem to get much further than that :(

Most of the posts I've found on this are about usb dongles and usb mode switcher to recognise them. As I've got an inbuilt GSM modem, I don't think that would apply... I've checked in the BIOS, and its definitely enabled there. I know eee pc's have a built in control panel for enabling and disabling bluetooth, mobile broadband and wifi, so I wonder if it could be disabled through that somehow? Or is it an issue of not having the right drivers? (however, I definitely saw Mobile Broadband enabled when i loaded antergos on live usb before I opted for Xubuntu, so it seems there may be drivers out there?)

Any help very appreciated! 
Bennitos


**some maybe useful info**:
*cat /var/lib/NetworkManager/NetworkManager.state* returns:
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

*lsusb *returns:
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem
Bus 001 Device 005: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by gordintoronto on 2017-11-22
It appears to use USB to connect to the computer, just like the webcam.

Does it have a SIM?

There may be a key combo to turn the modem on and off, perhaps Fn-hyphen.

[https://forums.linuxmint.com/viewtopic.php?t=126395](https://forums.linuxmint.com/viewtopic.php?t=126395)

---

### Post by bennitos on 2017-11-27
Thanks for the tip!

I tried pretty much all keys with fn and no luck :( 

Then I downloaded the eee pc 1000HG manual, and appears there may not be a hotkey for it.... it describes hotkeys for wifi, but nothing for 3g - simply says use the 'mobile partner' app that would have been be pre-installed with windows.

Any other ideas?

Benny

---

### Post by jeremy31 on 2017-11-27
Is modemmanager installed?  It might be needed to turn the device on.

---

### Post by bennitos on 2017-11-28
I have Modem Manager version 1.4.12 installed.

However, I imagine this linux programme with the name Modem Manager may not be the same one as the 'modem manager' referred to in the eee pc manual, which would be a windows program? 

As I wiped my hard drive to install linux, I imagine that I don't have the 'Modem Manager' that shipped with the eee pc windows distro. Which were you referring to? 

B

Oh, and in answer to your other question re SIM cards - I have been taking the SIM from my phone and putting it in, to try it out. My SIM is GiffGaff, and includes a data package

This is a bit fiddly as the SIM goes in under the battery, and taking it out require shutting down the computer (though not if I keep the charger plugged in)

I haven't been leaving my SIM in as its also needed for my phone

---


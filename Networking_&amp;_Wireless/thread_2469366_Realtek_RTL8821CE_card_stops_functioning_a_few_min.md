---
title: "Realtek RTL8821CE card stops functioning a few minutes after boot"
date: 2021-11-26
forum: Networking &amp; Wireless
---

### Post by johnfrith1 on 2021-11-26
I have a new HP Laptop 15s-fq4553na that came with Windows 11. 
I installed Ubuntu 20.04 as a dual boot.
WiFi works fine under Windows, but consistently fails shortly after boot into Ubuntu, after which I'm able to click on the WiFi in Settings, but it doesn't find any signals. 
If I boot to Windows and switch airplain mode on and off usind the dedicated button, and then reboot to Ubuntu I get WiFi back, but after 5 minutes it drops again. Doing the same thing whilst booted go Ubuntu doesn't help at all.

Software & Updates lists "Additional Drivers" as:

 Realtek Semiconductor Co., Ltd,:RTL8821CE 802.11ac PCIe Wireless Network Adapter
 This device is not working.
 
 
 Do not use this device.

wireless-info.txt = [https://pastebin.com/BU2DP12j](https://pastebin.com/BU2DP12j)

I tried 

if=wlo1
sudo ip link set $if up

but nothing happened.

I don't have anything left to try.

---

### Post by johnfrith1 on 2021-11-28
I now suspect this has something to do with me not doing the MOK management correctly? 

On two occasions during the setup of my new laptop I came across the MOK management blue screen, and on both occasions I tried to duck the issue by selecting "continue to boot", because I didn't know what option to take.

I don't really understand enough to know how to recover. Any help would be appreciated.

---

### Post by johnfrith1 on 2021-11-28
I've come across this, but I'm reluctant to do it, as I don't know what I'm doing, and I might make things worse!

"Resetting MOK keys 
[LIST=1]
[*]Run 'sudo mokutil --reset'. 
[*]Reboot. 
[*]Validate that the [MokManager]("https://wiki.kubuntu.org/MokManager") prompt happens and displays a menu of tasks that could be done in [MokManager]("https://wiki.kubuntu.org/MokManager"). 

[LIST]
[*]This should include the "Reset MOK" task. 
[/LIST]

[*]Complete the "Reset MOK" task in [MokManager]("https://wiki.kubuntu.org/MokManager"). 

[*]Pick 'Reboot'. 
[*]After the system has booted, verify that the keys only include the Canonical certificate embedded in shim. 
[LIST]
[*]Use 'sudo mokutil --list-enrolled' to validate the keys that are available.
[/LIST]
[/LIST]

---

### Post by jeremy31 on 2021-11-28
It might be wifi power management, try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by johnfrith1 on 2021-11-28
> **jeremy31 said:**
> It might be wifi power management, try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

Bingo! Right first time. Respect to you for sharing your knowledge free of charge, demonstrating that your a human being. I'll try and pass the favour on myself in some way.

---

### Post by johnfrith1 on 2021-11-28
jeremy31 has given me a fix so that my WiFi is now stable, but I still have:

Software & Updates lists "Additional Drivers" as:

 Realtek Semiconductor Co., Ltd,:RTL8821CE 802.11ac PCIe Wireless Network Adapter
 This device is not working.
 Do not use this device.

Even though I don't have any symptoms, as the network card is still marked as not working it bugs me, so I'd like to leave the thread as "unsolved".

---

### Post by jeremy31 on 2021-11-28
That is a glitch left from whoever maintains the rtl8821ce-dkms package as this is in the packages list
> Package: rtl8821ce-dkms
Architecture: all
Version: 5.5.2.1-0ubuntu4~20.04.4
Priority: optional
Section: universe/kernel
Source: rtl8821ce
Origin: Ubuntu
Maintainer: Canonical HWE Team <canonical-hwe@lists.canonical.com>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 24638
Depends: dkms (>= 2.1.0.0), bc
Filename: pool/universe/r/rtl8821ce/rtl8821ce-dkms_5.5.2.1-0ubuntu4~20.04.4_all.deb
Size: 2196916
MD5sum: 8f4f850695006f8af66da9ad369f724f
SHA1: 99883d4cb73f6325cf28746b4390408c577b07c3
SHA256: 8d8d669cef4d05eed3f0c0304e852582772f3fb9b87b1f353323be2902b1136c
SHA512: 1421e2bdf2c9a57b93e49d86920ae5ff14f4c002c056962949d06dfc4894c409fe817310cc0983415ad80a232e5f0f5f72428a93581982719d142668708e8032
Description: DKMS source for the Realtek 8821C PCIe WiFi driver
Modaliases: rtl8821ce(pci:v000010ECd0000C82Bsv*sd*bc*sc*i*, pci:v000010ECd0000C82Asv*sd*bc*sc*i*, pci:v000010ECd0000C821sv*sd*bc*sc*i*)
The Additional Drivers program matches a device listed to one you have and then it sits there telling you the device is not working just because this package isn't installed, even though it has support from the Ubuntu kernel

---

### Post by johnfrith1 on 2021-11-28
Thanks again jeremy31. Two for two.

---


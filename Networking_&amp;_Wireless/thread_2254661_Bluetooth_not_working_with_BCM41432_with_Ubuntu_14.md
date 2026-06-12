---
title: "Bluetooth not working with BCM41432 with Ubuntu 14.10 on Dell Vostro 3560"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by nukeblitz on 2014-11-29
[COLOR=#333333][FONT=UbuntuRegular]I have an issue on a Dell Vostro 3560 with a BCM43142 where the Bluetooth doesn't work even with the proprietary drivers installed. The WiFi works just fine. I'm running a fresh installation of Ubuntu 14.10. The only time it worked was when I had Dell preinstalled Ubuntu 12.04.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]dmesg | grep Bluetooth gives [ 4967.683179] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-0a5c-21d7.hcd not found[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I don't have a Windows installation I can get files from[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]From lsusb Bus 002 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]apt-get shows bcmwl-kernel-source is already the newest version.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This should have fixed my problem but it did not
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400) Why?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any solution?[/FONT][/COLOR]

---

### Post by jeremy31 on 2014-11-29
```
wget http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb
```
```
dpkg-deb -x bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb bt-bcm43142
```
```
sudo cp bt-bcm43142/lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd /lib/firmware/
```
```
sudo rmmod btusb
```
```
sudo modprobe btusb
```
hopefully this works, it should at least get you the firmware

---

### Post by jeremy31 on 2015-01-01
Found the answer that should work as there are quite a few different firmware files for this model Broadcom bluetooth
```
git clone git://github.com/jessesung/hex2hcd.git
cd hex2hcd
make
```
Then you need to get BCM43142A0_001.001.011.0049.0054.hex from [http://www.iogear.com/support/driver/GBU521_Windows_XP_Driver_v5.6.0.7700.zip](http://www.iogear.com/support/driver/GBU521_Windows_XP_Driver_v5.6.0.7700.zip) and copy it into the hex2hcd folder, it is in /GBU521_Windows_XP_Driver_v5.6.0.7700/Win64/drivers/
```
./hex2hcd BCM43142A0_001.001.011.0049.0054.hex BCM43142A0-0a5c-21d7.hcd
sudo cp BCM43142A0-0a5c-21d7.hcd /lib/firmware/brcm/
sudo modprobe -r btusb
sudo modprobe btusb
```

---

### Post by toinemeijvis-msn on 2015-01-19
> **jeremy31 said:**
> Found the answer that should work as there are quite a few different firmware files for this model Broadcom bluetooth
[COLOR=#333333][FONT=Ubuntu]```
git clone git://github.com/jessesung/hex2hcd.git
cd hex2hcd
make
```
Then you need to get BCM43142A0_001.001.011.0049.0054.hex from [http://www.iogear.com/support/driver/GBU521_Windows_XP_Driver_v5.6.0.7700.zip](http://www.iogear.com/support/driver/GBU521_Windows_XP_Driver_v5.6.0.7700.zip) and copy it into the hex2hcd folder, it is in [/FONT][/COLOR]/GBU521_Windows_XP_Driver_v5.6.0.7700/Win64/drivers/
[COLOR=#333333][FONT=Ubuntu]```
./hex2hcd BCM43142A0_001.001.011.0049.0054.hex [FONT=UbuntuRegular]/BCM43142A0-0a5c-21d7.hcd[/FONT]
sudo cp [FONT=UbuntuRegular]/BCM43142A0-0a5c-21d7.hcd[/FONT] /lib/firmware/brcm/
sudo modprobe -r btusb
sudo modprobe btusb
```[/FONT][/COLOR]

Hi Jeremy, thanks for you answer! The reality is that i am utmost inexperienced with ubuntu and i tryed to follow your advice but it seems not to work. Can you write me a step by step instruction?
for instance,      I can not find this folder: [COLOR=#333333][FONT=Ubuntu] hex2hcd folder, it is in [/FONT][/COLOR]/GBU521_Windows_XP_Driver_v5.6.0.7700/Win64/drivers/  (i run a win 7 / ubuntu 14.04 dual boot)  But also other steps are not clear to me...
Would you be so kind to make me a step by step instruction?

Would be realy helpfull!

Thanks in advance!
Toine

---

### Post by jeremy31 on 2015-01-19
> **toinemeijvis-msn said:**
> Hi Jeremy, thanks for you answer! The reality is that i am utmost inexperienced with ubuntu and i tryed to follow your advice but it seems not to work. Can you write me a step by step instruction?
for instance,      I can not find this folder: [COLOR=#333333][FONT=Ubuntu] hex2hcd folder, it is in [/FONT][/COLOR]/GBU521_Windows_XP_Driver_v5.6.0.7700/Win64/drivers/  (i run a win 7 / ubuntu 14.04 dual boot)  But also other steps are not clear to me...
Would you be so kind to make me a step by step instruction?

Would be realy helpfull!

Thanks in advance!
Toine

The hex2hcd folder should be in /home or you can find its location with ```
locate hex2hcd
``` and you might need to download some packages```
sudo apt-get install build-essential git
``` to be able to download and install the hex2hcd program

---

### Post by nirflysher on 2015-01-23
Same problem for me...
Still couldn't find a solution..

---

### Post by jeremy31 on 2015-01-23
> **nirflysher said:**
> Same problem for me...
Still couldn't find a solution..

Same errors in dmesg?  With the 0a5c:21d7 as the bluetooth device in lsusb?  I might have some time later to look into it again

---


---
title: "WiFi Not Working in Lenovo G50-80 on Ubuntu 14.04"
date: 2016-07-16
forum: Networking &amp; Wireless
---

### Post by karthdz on 2016-07-16
HI,

I use Lenovo G50-80 laptop with dual boot to Ubuntu 14.04. The Wifi was not working until I tried below steps to solve it. BUT now after a recent update it is again not working. I repeated the below steps still doesnt work. Really appreciate if someone helps me out here.

[FONT=arial]Step 1:

[/FONT]
[FONT=arial][COLOR=#333333][FONT=monospace]installing the firmware using[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]git clone [https://github.com/atondwal/ath10k-firmware.git](https://github.com/atondwal/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Reboot

[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Step 2:
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]you also need[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz)
tar -zxvf backports-20150903.tar.gz
cd backports-20150903[COLOR=#500050]
make defconfig-ath10k
make
sudo make install[/COLOR][/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Then reboot[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Thanks,[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Kartik Shrikant Hegde[/FONT][/COLOR]
[/FONT]

---

### Post by jeremy31 on 2016-07-17
If you install 16.04 and update over ethernet, the wifi should work.  Trying 16.04 without installing doesn't work because the ISO doesn't have the update to linux-firmware.  I believe the installer has linux-firmware version 157 and the current version is 157.2

The [changelog for linux-firmware](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-firmware/linux-firmware_1.157.2/changelog) shows the recent changes to the package and they involve firmware for ath10k

---


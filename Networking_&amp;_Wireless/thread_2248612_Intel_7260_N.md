---
title: "Intel 7260 N"
date: 2014-10-15
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2014-10-15
I bought a new wireless N card (Intel 7260 N) and installed it today. When I run lspci, it is listed, but it is not active. When I click on the Indicator Applet, it is not listed and iwconfig is not listed. Previously I was using a Qualcomm Atheros AR9287. I don't remember what I had to do to get it working, but it did not work out of the box either.
I thought the Intel would work out of the box??
Ubuntu Forums help me. Your my only hope :)

---

### Post by chili555 on 2014-10-15
Chili, one of Obi Wan's helpers, is here to help you. 

The 7260 is a relatively new device and Ubuntu 12.04 is a relatively older Ubuntu version.  Let's see where we are so far. Please run and post the results of:```
lspci -nn | grep 0280
```When you find the pci.id, something like 8086:4567, or some such, see if the driver version in 12.04 covers it:```
modinfo iwlwifi | grep [COLOR="#FF0000"]4567[/COLOR]
```Of course, substitute the number you found for your device. 

Post the results and we'll proceed.

---

### Post by lsutiger on 2014-10-15
Thank you for your help! Sorry for the late response Had to find my eth cable for the living room, bad knee, etc, etc..lol
lspci lists the controller > 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2x]
modinfo does not
> modinfo iwlwifi | grep 08b2x

---

### Post by chili555 on 2014-10-15
How about this?```
modinfo iwlwifi | grep 08B2
```Can you please check again? I never saw anything like this:> 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:[COLOR="#FF0000"]08b2x[/COLOR]]Thanks.

---

### Post by lsutiger on 2014-10-15
You are correct. Not sure what happened there.copypasta
> Intel Corporation Wireless 7260 [8086:08b2] (rev 73)

Same with the modinfo.

---

### Post by chili555 on 2014-10-15
So the newer device is not covered in the older version of the driver. My 1979 Chevy won't get 35 mpg on E85, sort of!

You could compile a newer version of the driver *iwlwifi* or install a newer kernel altogether or simply upgrade to 14.04. Do you have a preference? I will be happy to assist in any case.

---

### Post by lsutiger on 2014-10-15
In my research I did find a couple of posts on other forums on compiling the driver from the Debian source. Want to step me though it?
 May the Schwartz be with you -- Yogurt

---

### Post by chili555 on 2014-10-15
> compiling the driver from the Debian source. Want to step me though it?No.

The smarty answer is that like Sinatra, I do it my way. The correct answer is that I'm not familiar with the Debian source and I could not vouchsafe it.

I suggest you download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.gz) Right-click it and select 'Extract Here.' Now open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.13-2/
make defconfig-iwlwifi
make
sudo make install
```Now download the required firmware here: [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode) Now open a terminal and do:

```
sudo cp ~/Desktop/iwlwifi-7260-7.ucode /lib/firmware/  <--or wherever you downloaded it
sudo modprobe -r iwldvm  <--If it is not loaded, OK, please proceed
sudo modprobe -r iwlwifi <--If it is not loaded, OK, please proceed
sudo modprobe iwlwifi
```
Your wireless should now be working.

Off for the evening; please let me hear a good report tomorrow.

---

### Post by lsutiger on 2014-10-15
Bad news...heres what I received towrd the end of the instructions:> sudo modprobe -r iwlwifi
FATAL: Module iwlwifi is in use.


---

### Post by Hadaka on 2014-10-15
Its showing its in use...because it is...thats your wirless card,
you should have beem loading this from a wired connection,
*** If and only if you made it past the "make" part and now the
next command is.to sudo modprobe -r (remove). You can safely
connect your wired and continue from there.,.,again the fist line
will be the modeprobe -r....if not...dont...just leave it and have
chili555 get you through it,
good luck...

you will be starting from here...if you switch to the wired connection

```

sudo cp ~/Desktop/iwlwifi-7260-7.ucode /lib/firmware/  <--or wherever you downloaded it
sudo modprobe -r iwldvm  #<--If it is not loaded, OK, please proceed
sudo modprobe -r iwlwifi #<--If it is not loaded, OK, please proceed
sudo modprobe iwlwifi
```

---

### Post by jeremy31 on 2014-10-16
Poster will likely need to use backports as these cards weren't supported until kernel 3.10 and 12.04 doesn't have the /etc/modprobe.d/iwlwifi.conf  so it is back to ```
sudo modprobe -r iwlmvm
``````
sudo modprobe -r iwlwifi
``` That is the way it has to be done for my 8086:08b1

[FONT=courier new]On to backports: [COLOR=#000000]download this file to your desktop: [/COLOR][https://www.kernel.org/pub/linux/ker...-3.16-1.tar.xz]("https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.16/backports-3.16-1.tar.xz") right click and select 'extract here'
Run the following one line at a time
[/FONT][FONT=courier new]```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.16-1
make defconfig-iwlwifi
make
sudo make install
```

Check for firmware ```
ls /lib/firmware | grep 7260
If not found it should be in package linux-firmware [code]sudo apt-get install linux-firmware
```[/FONT]

---

### Post by chili555 on 2014-10-16
@lsutiger Please reboot and tell us if the wireless is working. If not, look for and post any clues from:```
dmesg | grep iwl
```

@jeremy31> Poster will likely need to use backports as these cards weren't supported until kernel 3.10Isn't that exactly what I already recommended?

---

### Post by jeremy31 on 2014-10-16
> **chili555 said:**
> @lsutiger Please reboot and tell us if the wireless is working. If not, look for and post any clues from:```
dmesg | grep iwl
```

@jeremy31Isn't that exactly what I already recommended?

I must be going blind

---

### Post by lsutiger on 2014-10-16
OK. Back
result of ls /lib/firmware | grep 7260
iwlwifi-7260-7.ucode

result of dmesg | grep iwl
[   13.272321] iwlwifi 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.272352] iwlwifi 0000:02:00.0: setting latency timer to 64
[   13.272471] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[   13.593926] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-7260-9.ucode' failed.
[   13.606831] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-7260-8.ucode' failed.
[   13.606839] iwlwifi 0000:02:00.0: no suitable firmware found!
[   13.606958] iwlwifi 0000:02:00.0: PCI INT A disabled

---

### Post by jeremy31 on 2014-10-16
You can get iwlwifi-7260-8.ucode here [http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.24.8.0.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.24.8.0.tgz) 
Click on it an extract it to home then
```
cd iwlwifi-7260-ucode-22.24.8.0
```
```
sudo cp iwlwifi-7260-8.ucode /lib/firmware/
```

---

### Post by lsutiger on 2014-10-16
OK. Got the new firmware, but still not active. Network Manager Applet states that the wireless is disabled by a hardware switch. I do not have a physical switch for wireless on the computer. I do have a FN key, but that doesn't do anything. 

result of dmesg | grep iwl
[   13.887078] iwlwifi 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.887134] iwlwifi 0000:02:00.0: setting latency timer to 64
[   13.887327] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[   14.034184] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-7260-9.ucode' failed.
[   14.073587] iwlwifi 0000:02:00.0: Firmware has old API version, expected v9, got v8.
[   14.073594] iwlwifi 0000:02:00.0: New firmware can be obtained from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/).
[   14.074013] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   14.114162] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   14.114260] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   14.115039] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   14.148285] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'

---

### Post by jeremy31 on 2014-10-16
Lets see the full result of ```
lsmod
```

---

### Post by lsutiger on 2014-10-16
I d/l the .9 firmware and copied. No I get this:
dmesg | grep iwlcomplexity@complexity-linux:~$ dmesg | grep iwl
[   12.788277] iwlwifi 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.788293] iwlwifi 0000:02:00.0: setting latency timer to 64
[   12.788382] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[   13.018545] iwlwifi 0000:02:00.0: loaded firmware version 25.222.9.0 op_mode iwlmvm
[   13.128891] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   13.128984] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   13.129244] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[   13.129939] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   13.204558] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'

How do I toggle to RF_KILL to enable?

---

### Post by lsutiger on 2014-10-16
Attempted :
sudo rfkill unblock all
did not work

---

### Post by jeremy31 on 2014-10-16
Please follow instructions found here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) to download and run the wifi script and hopefully there is a way to solve the hardware switch issue.  Check ```
rfkill list
``` If it is a soft block on the wifi ```
rfkill unblock all
``` should work and check network manager to make sure wifi is enabled, otherwise post the result of the wireless script

---

### Post by lsutiger on 2014-10-16
Attached is the output fro the script.
It is hard blocked:
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Thank you for all of your help!

---

### Post by jeremy31 on 2014-10-16
Unplug ethernet cable ```
sudo modprobe -r acer_wmi[code] [code]sudo rfkill unblock all
```
Has the result of ```
rfkill list
``` changed?

Is there a BIOS update available for this PC?

I

---

### Post by lsutiger on 2014-10-16
rfkill list did not change. BIOS update for this? IDK if I want to try that

---

### Post by lsutiger on 2014-10-16
OK. I put in my old wireless card and now it doesn't work. Could someone assist me getting that one working?
from lspci:
Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by chili555 on 2014-10-16
> **lsutiger said:**
> OK. I put in my old wireless card and now it doesn't work. Could someone assist me getting that one working?
from lspci:
Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)Does it also report hard blocked?```
rfkill list all
```I doubt changing the card will have much effect on rfkill.

---

### Post by lsutiger on 2014-10-16
No it isn't
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2014-10-16
Is the driver loaded?```
lsmod | grep ath
```If not, load it:```
sudo modprobe ath9k
```Is an interface created?```
iwconfig
```When you click the Network Manager icon, do you see your network?

---

### Post by lsutiger on 2014-10-16
The driver is not loaded. When I try to load it, many errors
```
sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting ath9k_hw (/lib/modules/3.2.0-70-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Invalid argument
WARNING: Error inserting ath9k_common (/lib/modules/3.2.0-70-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Invalid argument
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-70-generic/updates/net/mac80211/mac80211.ko): Invalid argument
FATAL: Error inserting ath9k (/lib/modules/3.2.0-70-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument

```
I checked to see if the files were there:
/lib/modules/3.2.0-70-generic/kernel/drivers/net/wireless/ath/ath9k$ ls
ath9k_common.ko  ath9k_htc.ko  ath9k_hw.ko  ath9k.ko

---

### Post by chili555 on 2014-10-16
Yoywill probably have to uninstall the, in some ways conflicting backports:```
cd ~/Desktop/backports-3.13-2/
sudo make uninstall
```Reboot and try again.

---

### Post by lsutiger on 2014-10-16
That worked. Thanks so much for your help!
I will try the new wireless card when I have time to upgrade.

---

### Post by lsutiger on 2014-10-18
OK I upgraded to 14.04 with the same results (Hard blocked). Any ideas?

---

### Post by chili555 on 2014-10-18
> **lsutiger said:**
> OK I upgraded to 14.04 with the same results (Hard blocked). Any ideas?How about letting us see:```
lsmod
```

---

### Post by weatherman2 on 2014-10-18
Where did you get this wireless card?  In my experience, there may be several versions of the same model wireless card.  For example, there is an HP/Lenovo version of many of these Intel wireless cards that may not work well or at all in a non-HP/Lenovo laptop.  But the marketing name of the card may be exactly he same for different versions of the same card.

I've had Intel wireless cards that didn't work properly or at all even though supposedly "new."  Install another card of the same model and it would work perfectly in the same laptop.  My worst experience was with cards from Asia.  I've had the best experience with used cards (eBay) pulled from scrap laptops.

In other words: there's some small chance this card isn't compatible with your laptop.  It may not even be a working card.  Just in case these other troubleshooting tips don't lead anywhere...

---

### Post by lsutiger on 2014-10-19
> **weatherman2 said:**
> Where did you get this wireless card?  In my experience, there may be several versions of the same model wireless card.  For example, there is an HP/Lenovo version of many of these Intel wireless cards that may not work well or at all in a non-HP/Lenovo laptop.  But the marketing name of the card may be exactly he same for different versions of the same card.

I've had Intel wireless cards that didn't work properly or at all even though supposedly "new."  Install another card of the same model and it would work perfectly in the same laptop.  My worst experience was with cards from Asia.  I've had the best experience with used cards (eBay) pulled from scrap laptops.

In other words: there's some small chance this card isn't compatible with your laptop.  It may not even be a working card.  Just in case these other troubleshooting tips don't lead anywhere...
This may be it. Got this one off of eBay, but it was pulled from a Lenovo. Thanks for your help!

---


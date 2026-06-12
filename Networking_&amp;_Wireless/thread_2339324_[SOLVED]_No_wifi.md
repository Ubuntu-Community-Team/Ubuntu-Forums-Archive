---
title: "[SOLVED] No wifi"
date: 2016-10-07
forum: Networking &amp; Wireless
---

### Post by prettypixel on 2016-10-07
I have installed Ubuntu 16.04.1 successfully. However, I have no wifi at all. Before installation, when I booted from the Live USB I also had no wifi. My laptop is a Lenovo Yoga 2 11 and I believe I have a Broadcom wifi card installed.
I have looked in System Settings - Software and Updates - Additional Drivers and see a listing for Broadcom Corporation. It reports the device is not working. And "Do not use the device" is selected. If I select "Using Broadcom 802.11 Linux STA wireless driver source..." and click on Apply Changes, "Do not use this device is still selected.

I do not know how to resolve this issue. For information, my laptop does not have an Ethernet port either. Some help would be appreciated. Thank you.

---

### Post by howefield on 2016-10-07
Thread moved to the "*Networking & Wireless*" forum.

Please read the [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") in this forum and provide the wireless script info as described.

---

### Post by prettypixel on 2016-10-07
Thanks for the reply, but I have no wifi/internet connection at all.

---

### Post by howefield on 2016-10-07
> **prettypixel said:**
> Thanks for the reply, but I have no wifi/internet connection at all.

Sure, but running the wireless information script will give those who can assist some more information that will help them to help you.

---

### Post by prettypixel on 2016-10-07
There is a web address in the commands of the script. Therefore, will the script work?

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

---

### Post by kurt18947 on 2016-10-07
You need a means to get the Broadcom firmware/drivers on your machine. There is a way to do so using a USB drive but I don't have a Broadcom device so am not experienced with it. If it were me, I'd probably get [one of these]("https://www.amazon.com/Plugable-Gigabit-Ethernet-Network-Adapter/dp/B00AQM8586/ref=sr_1_2?s=pc&ie=UTF8&qid=1475851071&sr=1-2&keywords=usb+ethernet+adapter+linux") to put in my bag of tricks or maybe an inexpensive USB wifi adapter known to work out of the box with Linux. I believe this would be a candidate that works out of the box:

[https://www.amazon.com/Tenda-W311M-150Mbps-Wireless-Adapter/dp/B006GCYAOS/ref=sr_1_fkmr0_3?s=pc&ie=UTF8&qid=1475851170&sr=1-3-fkmr0&keywords=tenda+mi311](https://www.amazon.com/Tenda-W311M-150Mbps-Wireless-Adapter/dp/B006GCYAOS/ref=sr_1_fkmr0_3?s=pc&ie=UTF8&qid=1475851170&sr=1-3-fkmr0&keywords=tenda+mi311) 

Once you have a network connection by any means you can install the Broadcom driver then remove the alternative network connection. There may be another option with which I am not familiar - tether to a phone and use the phone's network connection to install the Broadcom stuff.

---

### Post by howefield on 2016-10-07
I missed you didn't have wired internet either. Please find attached a copy of the wireless script.

---

### Post by prettypixel on 2016-10-07
Thank you for the reply. I will see if I can tether my phone to my laptop and use its network connection to get the driver.

---

### Post by prettypixel on 2016-10-07
Thanks. How do I run the script? I don't recognise the file format.

---

### Post by howefield on 2016-10-07
> **prettypixel said:**
> Thanks. How do I run the script? I don't recognise the file format.

The file is compressed, so double click it and extract to a convenient folder.. let's say you Documents folder. Then open a terminal and run the command..

```
cd Documents && chmod +x wireless-info && ./wireless-info
```

That should put a file into your Documents folder called "*wireless-info.txt*" - post that file back here.

---

### Post by prettypixel on 2016-10-07
Hi - thanks for explaining :) I have copied the file contents below, as requested.

```
########## wireless info START ##########


Report from: 07 Oct 2016 16:51 BST +0100


Booted last: 07 Oct 2016 00:00 BST +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
	Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 03eb:8858 Atmel Corp. 
Bus 001 Device 007: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 006: ID 1bcf:2c66 Sunplus Innovation Technology Inc. 
Bus 001 Device 012: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
bcma                   53248  0
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2398     1  0 14:44 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[bcma]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


##### module parameters #################


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 2804.032516] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 2804.032521] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found


########## wireless info END ############
```

---

### Post by Hadaka on 2016-10-08
Hi, please open a terminal ctrl/alt/t then Copy and paste one line at a time.
*Clear blocks.
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
*Set correct country code.
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
*Remove incorrect wifi driver
```
sudo modprobe -r bcma
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
*Insert correct wifi driver.
*Since you have no internet,use the offline/no internet method.
[https://ubuntuforums.org/showthread.php?t=2316986](https://ubuntuforums.org/showthread.php?t=2316986)
*Insert the USB you used to load Ubuntu.....then do.
```
cp /media/*/pool/main/d/dkms/*.deb dk.deb
cp /media/*/pool/restricted/b/bcmwl/*.deb wl.deb
sudo dpkg -i *.deb
sudo modprobe -v wl
```
Boot and test wireless
Thanks

---

### Post by prettypixel on 2016-10-08
Thank you very much for your help. I now have wifi :)

---

### Post by Hadaka on 2016-10-08
Glad that worked for you and thanks
for marking your thread solved.
Enjoy !

---


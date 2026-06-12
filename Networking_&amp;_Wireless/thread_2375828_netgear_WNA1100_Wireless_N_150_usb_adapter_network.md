---
title: "netgear WNA1100 Wireless N 150 usb adapter network state down"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by rubinglen-b on 2017-10-27
I am running Ubuntu 17.10 and trying to use a usb wireless adapter netgear WNA1100 Wireless N 150 usb, which works out of the box on another Linux distro (puppy), but alas not on my unbunt desktop.

It shows up in lsusb and iwconfig, but when I try connecting to network using GUI no networks come up and the network activity light on the usb itself never lights up.  If I check the status on commandline using** ip link show wlxe091f54daf32**, then the interface shows up as being in state DOWN.  

If I try bringing it up by typing,** iplink set wlxe091f54daf32 up** then nothing happens if I recheck to see if it is up it still says it is DOWN

I can scan networks using command line but am unable to connect to any.

The driver for this adapter is supposed to be ath9k_htc, which shows up as being there when I type lsmod.  If I try connecting using wpa_supplicant as follows:

sudo wpa_supplicant -B -D ath9k_htc -I wlxe091f54daf32

It returns the following:

*wlxe091f54daf32: Unsupported driver ath9k_htc*

appreciate any suggestions how to get this thing working.  I swear I once used it on this machine at an earlier date.

---

### Post by chili555 on 2017-10-27
Please run and post:```
lsusb
dmesg | grep ath
rfkill list all
```Thanks.

---

### Post by rubinglen-b on 2017-10-27
output from those commands as follows:

Bus 002 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 005: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 040b:2000 Weltrend Semiconductor 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:0941 Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[  728.036313] usb 2-1: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[  728.036404] usbcore: registered new interface driver ath9k_htc
[  728.342271] usb 2-1: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[  728.594361] ath9k_htc 2-1:1.0: ath9k_htc: HTC initialized with 33 credits
[  728.868004] ath9k_htc 2-1:1.0: ath9k_htc: FW Version: 1.4
[  728.868011] ath9k_htc 2-1:1.0: FW RMW support: On
[  728.868014] ath: EEPROM regdomain: 0x60
[  728.868016] ath: EEPROM indicates we should expect a direct regpair map
[  728.868021] ath: Country alpha2 being used: 00
[  728.868022] ath: Regpair used: 0x60
[  728.902810] ath9k_htc 2-1:1.0 wlxe091f54daf32: renamed from wlan0
[18086.976793] usbcore: deregistering interface driver ath9k_htc
[18087.309097] usb 2-1: ath9k_htc: USB layer deinitialized
[18087.309204] ath9k_htc: Driver unloaded
[18187.635239] usb 2-1: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[18187.635371] usbcore: registered new interface driver ath9k_htc
[18187.935413] usb 2-1: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[18188.186733] ath9k_htc 2-1:1.0: ath9k_htc: HTC initialized with 33 credits
[18188.432127] ath9k_htc 2-1:1.0: ath9k_htc: FW Version: 1.4
[18188.432134] ath9k_htc 2-1:1.0: FW RMW support: On
[18188.432137] ath: EEPROM regdomain: 0x60
[18188.432139] ath: EEPROM indicates we should expect a direct regpair map
[18188.432144] ath: Country alpha2 being used: 00
[18188.432146] ath: Regpair used: 0x60
[18188.456752] ath9k_htc 2-1:1.0 wlxe091f54daf32: renamed from wlan0

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2017-10-28
Please run

```
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9khtc.conf
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
and reboot

---

### Post by rubinglen-b on 2017-10-28
I entered the above three commands and am not seeing any change.  State is still listed as down and no blinking light on the adapter itself. If I try to configure using the network GUI I get a blank list that says no networks and a loading spinner icon.

---

### Post by chili555 on 2017-10-28
> **rubinglen-b said:**
> I entered the above three commands and am not seeing any change.  State is still listed as down and no blinking light on the adapter itself. If I try to configure using the network GUI I get a blank list that says no networks and a loading spinner icon.Please run and post:
```
dmesg | grep ath
rfkill list all
cat /etc/NetworkManager/NetworkManager.conf
```
Thanks.

---

### Post by rubinglen-b on 2017-10-28
A couple of interesting developments: Before going to run the above commands I noticed that the blue light on the wifi adapter was on!  I tried configuring network with GUI as well as CLI, but again neither worked.  I then ran your commands sending all std error and output to a file and when I went to plug my usb memory drive in to transfer the file (located next to the usb wifi), I noticed that made the lights on the wifi stick actually go out....strange.  Anyways, here is the output from the commands you gave me:

[    8.265492] audit: type=1400 audit(1509184221.262:138): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=928 comm="apparmor_parser"
[    8.265504] audit: type=1400 audit(1509184221.262:139): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=928 comm="apparmor_parser"
[    8.265512] audit: type=1400 audit(1509184221.262:140): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=928 comm="apparmor_parser"
[    8.265520] audit: type=1400 audit(1509184221.262:141): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=928 comm="apparmor_parser"
[    8.265527] audit: type=1400 audit(1509184221.262:142): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/usr/lib/telepathy/telepathy-ofono" pid=928 comm="apparmor_parser"
[  157.184581] usb 1-1: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[  157.184758] usbcore: registered new interface driver ath9k_htc
[  157.477515] usb 1-1: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[  157.728346] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[  157.967721] ath9k_htc 1-1:1.0: ath9k_htc: FW Version: 1.4
[  157.967724] ath9k_htc 1-1:1.0: FW RMW support: On
[  157.967726] ath: EEPROM regdomain: 0x60
[  157.967726] ath: EEPROM indicates we should expect a direct regpair map
[  157.967728] ath: Country alpha2 being used: 00
[  157.967729] ath: Regpair used: 0x60
[  157.986782] ath9k_htc 1-1:1.0 wlxe091f54daf32: renamed from wlan0
[ 2512.559366] usb 1-1: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[ 2512.811240] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false




[keyfile]
unmanaged-devices=interface-name:ap0;interface-name:wlxe091f54daf32


[device]
wifi.scan-rand-mac-address=no

---

### Post by chili555 on 2017-10-28
> [keyfile]
unmanaged-devices=interface-name:ap0;interface-name:wlxe091f54daf32
You have asked Network Manager to *ignore* your wireless! Is it managed elsewhere?```
cat /etc/network/interfaces
```If wlxe091f54daf32 isn't declared there, then NM is mis-configured.

If, and ONLY IF wlxe091f54daf32 isn't listed in /etc/network/interfaces, then let's change the file:```
sudo nano /etc/NetworkManager/NetworkManager.conf
```Remove the lines I quoted above. After doing so, the file should read:```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

```Proofread carefully, save (write out, followed by Enter) and close (Exit) the text editor. Restart NM:```
sudo service network-manager restart
```Any improvement?

---

### Post by rubinglen-b on 2017-10-28
Improvement?  Yes it works!!!!  Thank you guys so much!!

---


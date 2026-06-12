---
title: "Wifi not working on Lenovo Y700,Intel wireless AC 3165"
date: 2016-01-01
forum: Networking &amp; Wireless
---

### Post by tal1234 on 2016-01-01
Hi everyone, happy new years!

Unfortunately I can't manage to make my new laptops(Lenovo Y700, intel wireless AC 3165) wifi work with Ubuntu(15.10). I've tried searching on these forums and it seems like it always comes back to these two solutions:
a. update the kernel to 4.2+.
b. download the newest driver files and move them to libs/framework

I've tried both of them:
as for part a- my kernel version is currently 4.4.0-040400rc7-generic, up from 3.9 I think, still no luck.
as for part b- I've tried doing that with no success as well(as was advised here: [http://askubuntu.com/questions/672700/linux-noob-trying-to-install-intel-dual-band-wireless-ac-3165](http://askubuntu.com/questions/672700/linux-noob-trying-to-install-intel-dual-band-wireless-ac-3165) ),however I'm not sure I did it right, as everyone that did this step got his wifi working. maybe I messed up the rename files step? no sure.

this is what I get from the wifi script :
-edited after issue was resolved
```

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
mac80211              724992  1 iwlmvm
iwlwifi               196608  1 iwlmvm
cfg80211              557056  3 iwlwifi,mac80211,iwlmvm
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-040400rc7-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     24870DBAE3C8C7D578FC4F1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-040400rc7-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-040400rc7-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0C052180BDE62D941BA49E7
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-040400rc7-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-040400rc7-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     298DAB8A7B46DFEF9D37E48
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-040400rc7-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-040400rc7-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     512CEC08D825E0BE23341B3
depends:        
intree:         Y
vermagic:       4.4.0-040400rc7-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 5852.554914] iwlwifi 0000:08:00.0: RF_KILL bit toggled to enable radio.
[ 5852.569651] r8169 0000:09:00.0 enp9s0: link down
[ 5853.337304] rndis_host 1-1:1.0 [FONT=Ubuntubeta]enx020e0d3863[/FONT][FONT=Ubuntubeta]: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device[/FONT]
[ 5853.346351] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[ 5853.505426] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 5855.924173] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[ 5855.924914] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[ 5855.940099] r8169 0000:09:00.0 enp9s0: link down
[ 5855.940208] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[ 5862.130651] rndis_host 1-1:1.0 enx020e0b0d3863: renamed from usb0
[ 5862.163621] IPv6: ADDRCONF(NETDEV_UP): enx020e0d3863: link is not ready
```
and this is the output I get for [FONT=Consolas][COLOR=#111111]dmesg | prep iwi:
[/COLOR][/FONT]```

[FONT=arial][    9.900243] iwlwifi 0000:08:00.0: Unsupported splx structure[/FONT]
[FONT=arial][   10.167637] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2[/FONT]
[FONT=arial][   10.167678] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2[/FONT]
[FONT=arial][   10.167701] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2[/FONT]
[FONT=arial][   10.203434] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7265D-16.ucode failed with error -2[/FONT]
[FONT=arial][   10.203476] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2[/FONT]
[FONT=arial][   10.203498] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7265D-14.ucode failed with error -2[/FONT]
[FONT=arial][   10.554529] iwlwifi 0000:08:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm[/FONT]
[FONT=arial][   10.875750] iwlwifi 0000:08:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210[/FONT]
[FONT=arial][   10.876235] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled[/FONT]
[FONT=arial][   10.876674] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled[/FONT]
[FONT=arial][   10.975324] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'[/FONT]
[FONT=arial][   11.033008] iwlwifi 0000:08:00.0 wlp8s0: renamed from wlan0[/FONT]
[FONT=arial][ 5112.902910] iwlwifi 0000:08:00.0: RF_KILL bit toggled to enable radio.[/FONT]

```
 Right now I'm using an ethernet cabal to get internet on the laptop.

It's been about a week and I still didn't get my wifi to work, hopefully someone here will be able to assist with this annoying issue :)

Thanks!

---

### Post by jeremy31 on 2016-01-01
This should work ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad.conf
```
Reboot

---

### Post by tal1234 on 2016-01-01
> **jeremy31 said:**
> This should work ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad.conf
```
Reboot
wow! it worked!!
thanks :)
*SOLVED*

---

### Post by jeremy31 on 2016-01-01
What is the result of ```
sudo dmidecode | grep -i version
```  I might be able to make a DKMS file so that you can remove the blacklist as removing that module might cause some FN combos/multimedia keys to quit functioning

---

### Post by tal1234 on 2016-01-02
> **jeremy31 said:**
> What is the result of ```
sudo dmidecode | grep -i version
```  I might be able to make a DKMS file so that you can remove the blacklist as removing that module might cause some FN combos/multimedia keys to quit functioning
Thanks for the continued support. this is the result:
```

	Version: CDCN25WW
	Version: Lenovo ideapad Y700-15ISK
	Version: SDK0J40709 WIN
	Version: Lenovo ideapad Y700-15ISK
	Version: Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz
	Name: Firmware Version Info
		uCode Version
		TXT ACM version
		MEBx version
		ME Firmware Version
		SKL PCH H Bx Hsio Version
		SKL PCH H Dx Hsio Version
		SKL PCH LP Bx Hsio Version
		SKL PCH LP Cx Hsio Version
		SA - PCIe Version

```

---

### Post by jeremy31 on 2016-01-02
```
mkdir source
cd source
wget https://www.dropbox.com/s/agbaam65i5t1a7e/ideapad-laptop.c
wget https://www.dropbox.com/s/g6xvfl6qzrs42kz/Makefile
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
sudo apt-get install build-essential
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```

Hopefully that works without any errors and it should if the headers were installed with the kernel and it should have created a file named ideapad-laptop.ko and we will copy that to where it needs to be
```
sudo cp ideapad-laptop.ko /lib/modules/$(uname -r)/kernel/drivers/platform/x86/
```

Then we can remove the blacklist
```
sudo rm /etc/modprobe.d/ideapad.conf
```

Reboot and see if it works

---

### Post by tal1234 on 2016-01-02
hi,
after:
```

make -C /lib/modules/$(uname -r)/build M=$(pwd) modules

```
I got:
```

make: Entering directory '/usr/src/linux-headers-4.4.0-040400rc7-generic'
make[1]: *** No rule to make target '/home/qm/source/asus-laptop.c', needed by '/home/qm/source/asus-laptop.o'.  Stop.
Makefile:1384: recipe for target '_module_/home/qm/source' failed
make: *** [_module_/home/qm/source] Error 2
make: Leaving directory '/usr/src/linux-headers-4.4.0-040400rc7-generic'

```

and after 
[COLOR=#000000]sudo cp ideapad-laptop.ko /lib/modules/$(uname -r)/kernel/drivers/platform/x86/[/COLOR]
[COLOR=#000000][/COLOR]I got
```

cp: cannot stat &#8216;ideapad-laptop.ko&#8217;: No such file or directory

```


didn't made the third one to remove the blacklist as I was guessing what we did didn't work?

---

### Post by jeremy31 on 2016-01-02
Open the Makefile, delete everything and copy this
```


obj-m += ideapad-laptop.o
 
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
 
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

Save and exit editor
Then you should be able to ```
cd ~/source
 make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
[COLOR=#000000]sudo cp ideapad-laptop.ko /lib/modules/$(uname -r)/kernel/drivers/platform/x86/
```[/COLOR]

---

### Post by tal1234 on 2016-01-02
> **jeremy31 said:**
> Open the Makefile, delete everything and copy this
```


obj-m += ideapad-laptop.o
 
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
 
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

Save and exit editor
Then you should be able to ```
cd ~/source
 make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
[COLOR=#000000]sudo cp ideapad-laptop.ko /lib/modules/$(uname -r)/kernel/drivers/platform/x86/[/COLOR]
```

did that, than 
[COLOR=#000000]sudo rm /etc/modprobe.d/ideapad.conf[/COLOR]
rebooted, and wifi still working! :)
if we're done then thank you so much!

---

### Post by johnholbrook on 2016-01-02
THANK YOU VERY MUCH!!!!! Ran into same problem with my Y700. Your fix worked.

As a side note I had lots of problems with the wifi card (Intel 8260) being really flakey. Submitted a bug report to Intel and I've been working with them over the last week to fix the issues. Looks like we''ve figured out the issues and there should be an update for the firmware soon.

---

### Post by Atools on 2016-02-23
I've got this output when trying to make the Makefile if anyone can help

[http://paste.ubuntu.com/15178196/](http://paste.ubuntu.com/15178196/)

---

### Post by jeremy31 on 2016-02-23
Post ```
sudo dmidecode | grep -i version; uname -a
```
Error seems to mean that your kernel is different than the source code

---

### Post by Atools on 2016-02-24
[Http://Paste.Ubuntu.com/15186602](Http://Paste.Ubuntu.com/15186602)

---

### Post by jeremy31 on 2016-02-24
The kernel version didn't show in the pastebin. ```
uname -a
```

---

### Post by Arif_Qodari on 2016-04-10
> **jeremy31 said:**
> The kernel version didn't show in the pastebin. ```
uname -a
```

I got the same problem and my kernel version is 3.13.0-24-generic
Any idea to solve the issue?

Thanks

---

### Post by jeremy31 on 2016-04-11
Try Ubuntu 15.10 or wait for 16.04 as there is no support for the 3165 with the 3.13 kernel.  You could use backports with that kernel
```
sudo apt-get install build-essential linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-wifi
make 
sudo make install
cd /lib/firmware
sudo wget http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-7265D-16.ucode
```

Reboot

If you get a kernel update you will lose wireless again and need to
```
cd backports-4.4.2-1
make clean
make defconfig-wifi
make
sudo make install
```

And reboot

---


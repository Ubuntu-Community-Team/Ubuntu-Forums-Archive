---
title: "Lenovo Yoga 3 14&quot; - Changing to supported wireless card"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by Rish_Bhatia on 2015-10-07
Hi I have a Lenovo Yoga 3 14" that has the Atheros QCA61x4 wireless card that I understand isn't supported (or at least I haven't stumbled upon a method for getting it to work). I'm planning on changing the wireless card so I can get Ubuntu to work. I was wondering if anyone has changed the wireless card on this laptop or knows of what wireless card I can buy so that it will work with Ubuntu out of the box?

I don't have an ethernet adapter so the Ubuntu installation won't have Internet access if the new wireless card doesn't work on a fresh installation? I could download the drivers on my other laptop and port them over using a USB but I won't be able to wget/git clone or anything of the sort when I install Ubuntu if the wireless doesn't work immediately.

Thanks a lot

---

### Post by jeremy31 on 2015-10-07
Post the result of ```
lspci -nnk | grep -iA2 net
```

It might be supported now

---

### Post by Rish_Bhatia on 2015-10-07
It isn't. I checked the bug report thread.

---

### Post by jeremy31 on 2015-10-07
You must have the 0042 card.  Call Lenovo and ask them about a wifi card as you just can't put any card in because of the whitelist in the BIOS.  They won't even boot

---

### Post by Rish_Bhatia on 2015-10-07
So my card is actually the Qualcomm Aterhos Device [168c:0041] (rev 20) Subsystem: Lenovo Device [17aa:3545]

---

### Post by jeremy31 on 2015-10-08
There is a way to get that card working
See my answer [http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244)

You just need to run the two commands and reboot
```
[COLOR=#333333][FONT=monospace]wget [/FONT][/COLOR]https://www.dropbox.com/s/nmgb5li6sd6i7ij/backath10k-dkms_2.0_all.deb
[COLOR=#333333][FONT=monospace]dpkg -i backath10k-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dkms_2.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0_all.deb[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace]

The firmware will be installed with the driver[/FONT][/COLOR]

---

### Post by Rish_Bhatia on 2015-10-08
I tried that. It gave an error saying that the package dkms is not installed. I don't have the ethernet adapter for my lenovo so I have been downloading the files on another computer and transferring them over. I'm not sure how to resolve the dkms dependency since I can't wget/apt-get on my lenovo.

I got the dkms issue fixed and I ran the code you provided but it still is giving issues. When I run rfkill list I get the following:

0: ideapad_waln: Wireless LAN
   Soft blocked: no
   Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
   Soft blocked: yes
   Hard blocked: yes
2: hci0: Bluetooth
   Soft blocked: yes
   Hard blocked: no
3: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked no

I wasn't getting the phy0 wireless LAN when I first installed Ubuntu 14.04 but I tried some of the commands you had posted in another thread on these forums (involving downloading firmware from kvalo and other git repositories) and it showed up. Not sure if that is interfering with your solution or how to remove it.

The instructions I followed were in this thread: [http://ubuntuforums.org/showthread.php?t=2296057](http://ubuntuforums.org/showthread.php?t=2296057)

---

### Post by jeremy31 on 2015-10-08
Edit: for now ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad.conf
```

Reboot

---

### Post by Rish_Bhatia on 2015-10-08
I installed dkms and ran the code you provided. The wireless is still isn't working.

---

### Post by jeremy31 on 2015-10-08
Look at ```
dmesg | grep -i qca6174
``` If you see ```
[COLOR=#000000][FONT=Ubuntu Mono]fw WLAN.RM.1.1-00141
``` in the results it means the firmware is wrong[/FONT][/COLOR]

---

### Post by Rish_Bhatia on 2015-10-08
I don't see it.

[ 2.309473] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[ 3.508460] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features

---

### Post by jeremy31 on 2015-10-08
Still have the block in ```
rfkll list all
``` and post result from ```
rfkill list all; lsmod | grep ideapad
```

---

### Post by Rish_Bhatia on 2015-10-08
The result is:

[COLOR=#000000]0: ideapad_wlan: Wireless LAN[/COLOR]
[COLOR=#000000]   Soft blocked: no[/COLOR]
[COLOR=#000000]   Hard blocked: yes[/COLOR]
[COLOR=#000000]1: ideapad_bluetooth: Bluetooth[/COLOR]
[COLOR=#000000]   Soft blocked: yes[/COLOR]
[COLOR=#000000]   Hard blocked: yes[/COLOR]
[COLOR=#000000]3: phy0: Wireless LAN[/COLOR]
[COLOR=#000000]   Soft blocked: no[/COLOR]
[COLOR=#000000]   Hard blocked no
[/COLOR][COLOR=#000000]5: hci0: Bluetooth[/COLOR]
[COLOR=#000000]   Soft blocked: yes[/COLOR]
[COLOR=#000000]   Hard blocked: no

[/COLOR]ideapad laptop     20480  0
sparse_keymap    16384  1 ideapad_laptop

---

### Post by jeremy31 on 2015-10-08
got the name wrong on the module
```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad.conf
```

Reboot and I think it will work, post ```
uname -a
``` as you should be able to delete the blacklist after Ubuntu updates the kernel

---

### Post by Rish_Bhatia on 2015-10-08
It works. Thanks a lot.

uname -a:

Lenovo-Yoga-3-14 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Is there anything I should know for the future to keep the wifi working?

---

### Post by jeremy31 on 2015-10-08
It should stay working in the 3.19 kernels, if it doesn't, just post a message.  If you install updates check ```
uname -a
``` to see if the kernel has changed as once you are at 3.19.0-26 or higher you should be able to remove the blacklist and still have wifi.
You can remove the blacklist with ```
sudo rm /etc/modprobe.d/ideapad.conf
```

---

### Post by Rish_Bhatia on 2015-10-09
I shutdown my computer and restarted it today but the wifi stopped working. I ran uname -a and nothing has changed.

When I run rfkill list all, only the bluetooth shows up.

---

### Post by jeremy31 on 2015-10-10
See what happens with
```
sudo dpkg -r backath10k-dkms_2.0_all.deb
sudo dpkg -i backath10k-dkms_2.0_all.deb
```
Reboot

---

### Post by Rish_Bhatia on 2015-10-10
It didn't work. Also, I tried to see if removing and adding "blacklist ideapad_laptop" from ideapad.conf would make a difference. It didn't work, but it did affect the output of rfkill (when blacklist is there, I only see the bluetooth).

---

### Post by jeremy31 on 2015-10-10
Does ```
lspci -nnk | grep -iA2 net
``` Show kernel driver in use: ath10k_pci for the wireless?

---

### Post by Rish_Bhatia on 2015-10-10
Whether I run it with or without the ideapad blacklist in /etc/modprobe.d then ath10k_pci does not show up.

The result is:

Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20) Subsystem: Lenovo Device [17aa:3545]

---

### Post by jeremy31 on 2015-10-11
Lets remove the dkms version and see if the backports will work.
```
dpkg -r backath10k-dkms_2.0_all.deb
cd backports-20150903
make clean
make defconfig-ath10k
make
sudo make install
```

Reboot

---

### Post by Rish_Bhatia on 2015-10-11
So, when I run sudo make install I get "Cant read private key" for each of the 6 modules it tries to install. And it ends with:
 
make[1]: execvp: ./scripts/blacklist.sh: Permission denied
make[1]:: *** [install] Error 127
make: *** [install] Error 2

---

### Post by jeremy31 on 2015-10-12
The can't read private key is normal but something isn't right with backports files
```
rm -r backports-20150903
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz
tar -zxvf backports-20150903.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
```

---

### Post by Rish_Bhatia on 2015-10-13
I did it and it installed properly this time. But wireless still not working after reboot.

---

### Post by jeremy31 on 2015-10-13
Follow the instructions to run the wireless script and post results [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Rish_Bhatia on 2015-10-13
I can't connect to the internet on that laptop (don't have access to a wired adapter). How can I go about doing sudo apt-get upgrade etc.?

---

### Post by jeremy31 on 2015-10-13
On a computer with internet access, download [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Put it on a USB drive CD/DVD and  copy it into the home folder in Ubuntu, then
```
chmod +x wireless-info && ./wireless-info
```

Then copy the wireless-info.**txt** back to the computer with internet access and post the contents

---

### Post by Rish_Bhatia on 2015-10-13
########## wireless info START ##########


Report from: 13 Oct 2015 06:05 EDT -0400


Booted last: 13 Oct 2015 06:03 EDT -0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 006: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 002: ID 5986:0535 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


ath                    32768  0 
mac80211              638976  0 
cfg80211              532480  2 ath,mac80211
compat                 28672  2 cfg80211,mac80211
wmi                    20480  0 
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop


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


root       734     1  0 06:03 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Arbor blu]] (600 root)
[connection] id=Arbor blu | type=802-11-wireless
[802-11-wireless] ssid=Arbor blu | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[ath]
filename:       /lib/modules/3.19.0-25-generic/updates/dkms/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     728F9FA9D17C407477851D2
depends:        cfg80211
vermagic:       3.19.0-25-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-25-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/ath10k_pci.conf]
options ath10k_pci irqmode=1


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:0x0041 (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    2.108755] ath10k_core: disagrees about version of symbol ieee80211_start_rx_ba_session_offl
[    2.108759] ath10k_core: Unknown symbol ieee80211_start_rx_ba_session_offl (err -22)
[    2.108763] ath10k_core: disagrees about version of symbol ieee80211_radar_detected
[    2.108764] ath10k_core: Unknown symbol ieee80211_radar_detected (err -22)
[    2.108771] ath10k_core: disagrees about version of symbol ieee80211_csa_is_complete
[    2.108772] ath10k_core: Unknown symbol ieee80211_csa_is_complete (err -22)
[    2.108779] ath10k_core: disagrees about version of symbol ieee80211_queue_work
[    2.108781] ath10k_core: Unknown symbol ieee80211_queue_work (err -22)
[    2.108796] ath10k_core: disagrees about version of symbol ieee80211_csa_finish
[    2.108797] ath10k_core: Unknown symbol ieee80211_csa_finish (err -22)
[    2.775572] Bluetooth: hci0: don't support firmware rome 0x200


########## wireless info END ############

---

### Post by jeremy31 on 2015-10-13
You will still need ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad.conf
```
Reboot

See what happens, if wifi doesn't function use ```
sudo modprobe -v ath10k_pci
```
See if any errors show

---

### Post by Rish_Bhatia on 2015-10-13
Didnt work.

Error messages:

insmod /lib/modules/3.19.0-25-generic/updates/dkms/ath10k_core.ko skip_otp=y
modprobe: ERROR: cpi;d mpt omsert 'ath10k_pci': Invalid argument

---

### Post by jeremy31 on 2015-10-13
Double post

---

### Post by jeremy31 on 2015-10-13
```
sudo rm /etc/modprobe.d/ath10k_pci.conf
sudo modprobe -v ath10k_pci
modinfo -p ath10k_pci
```

---

### Post by Rish_Bhatia on 2015-10-13
Got the couldnt insert ath10k_pci error from the second command.

---

### Post by jeremy31 on 2015-10-14
```
ls /etc/modprobe.d/ | grep -i ath
```

---

### Post by Rish_Bhatia on 2015-10-19
ath10k.conf
ath10k.conf~
blacklist-ath_pci.conf

---

### Post by jeremy31 on 2015-10-19
I wonder if dmesg shows the reason for ath10k_pci not wanting to load. ```
sudo modprobe -v ath10k_pci
dmesg | tail -20
```

---

### Post by Rish_Bhatia on 2015-11-14
Sorry for the late reply. Been really busy. Here is the output:

[   30.677041] ath10k_core: disagrees about version of symbol ieee80211_scan_completed
[   30.677042] ath10k_core: Unknown symbol ieee80211_scan_completed (err -22)
[   30.677046] ath10k_core: disagrees about version of symbol ieee80211_iterate_active_interfaces_atomic
[   30.677047] ath10k_core: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err -22)
[   30.677060] ath10k_core: disagrees about version of symbol ieee80211_unregister_hw
[   30.677061] ath10k_core: Unknown symbol ieee80211_unregister_hw (err -22)
[   30.677071] ath10k_core: disagrees about version of symbol ieee80211_csa_update_counter
[   30.677072] ath10k_core: Unknown symbol ieee80211_csa_update_counter (err -22)
[   30.677076] ath10k_core: disagrees about version of symbol ieee80211_beacon_get_tim
[   30.677077] ath10k_core: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   30.677086] ath10k_core: disagrees about version of symbol ieee80211_start_rx_ba_session_offl
[   30.677087] ath10k_core: Unknown symbol ieee80211_start_rx_ba_session_offl (err -22)
[   30.677092] ath10k_core: disagrees about version of symbol ieee80211_radar_detected
[   30.677093] ath10k_core: Unknown symbol ieee80211_radar_detected (err -22)
[   30.677098] ath10k_core: disagrees about version of symbol ieee80211_csa_is_complete
[   30.677099] ath10k_core: Unknown symbol ieee80211_csa_is_complete (err -22)
[   30.677105] ath10k_core: disagrees about version of symbol ieee80211_queue_work
[   30.677106] ath10k_core: Unknown symbol ieee80211_queue_work (err -22)
[   30.677118] ath10k_core: disagrees about version of symbol ieee80211_csa_finish
[   30.677119] ath10k_core: Unknown symbol ieee80211_csa_finish (err -22)

---

### Post by jeremy31 on 2015-11-14
It seems that the dkms version wasn't totally removed when the deb was uninstalled
```
sudo dkms remove -m backath10k -v 2.0 --all
```
Reboot

Then see what ```
modinfo ath10k_pci | grep filename
``` shows

---

### Post by Rish_Bhatia on 2015-11-14
The first command results in an error saying there are no instances of module backath10k 2.0 located in the DKMS tree.

The second command prints:

filename: /lib/modules/3.19.0-25-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko

---

### Post by jeremy31 on 2015-11-14
What about ```
modinfo ath10k_core | grep filename
```

---

### Post by Rish_Bhatia on 2015-11-14
/lib/modules/3.19.0-25-generic/updates/dkms/ath10k_core.ko

---

### Post by jeremy31 on 2015-11-14
Ok, what about ```
ls [COLOR=#000000]/lib/modules/3.19.0-25-generic/updates/drivers/net/wireless/ath/ath10k/
```[/COLOR]

---

### Post by Rish_Bhatia on 2015-11-14
ath10k_core.ko
ath10k_pci.ko

---

### Post by jeremy31 on 2015-11-14
Ok, what about ```
ls [COLOR=#000000]/lib/modules/3.19.0-25-generic/updates/drivers/net/wireless/ath/ath10k/
```[/COLOR]

---

### Post by Rish_Bhatia on 2015-11-14
Isn't that the exact same thing as the previous one?

---

### Post by jeremy31 on 2015-11-15
Download [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/10/13/backports-20151013.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/10/13/backports-20151013.tar.gz)

Extract the files to Desktop
```
cd Desktop/backports-20151013/
make defconfig-ath10k
make
sudo make install
```
Reboot

---

### Post by wentao on 2015-11-15
Hi I was following your thread and I got it worked on my machine. I'm using Lenovo 3 14 as well.

I used manual setup option in the post [http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in)

After that I was following the instructions in tread until #25. Then I ran 
modprobe -r ideapad-laptop
The wifi is wokring now. 

I'm using Ubuntu Gnome 14.04.

---

### Post by jeremy31 on 2015-11-15
> **wentao said:**
> Hi I was following your thread and I got it worked on my machine. I'm using Lenovo 3 14 as well.

I used manual setup option in the post [http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in)

After that I was following the instructions in tread until #25. Then I ran 
modprobe -r ideapad-laptop
The wifi is wokring now. 

I'm using Ubuntu Gnome 14.04.

Good to hear my answer there worked for you, the ideapad-laptop fix is in updated kernels, I think I posted the kernel it is fixed in in this thread somewhere.  For some reason here uninstalling the dkms version didn't uninstall the modules properly where it has worked properly on my laptop.  The strange thing is, it seems there is some error between the dkms installed module and the backports when my dkms was based on the same backports.  So I am hoping a newer backports version will fix this

---

### Post by Rish_Bhatia on 2015-11-15
Didn't work.

---

### Post by jeremy31 on 2015-11-16
Lets see ```
ls /var/lib/dkms
ls /usr/src/ | grep back
```

---

### Post by Rish_Bhatia on 2015-11-16
ath10k dkms_dbversion

no output for second command

---

### Post by jeremy31 on 2015-11-17
```
dkms status
```

---

### Post by Rish_Bhatia on 2015-11-17
ath10k, 1.1, 3.19.0-25-generic, x86_64: installed (WARNING! Diff between built and installed module!)

---

### Post by jeremy31 on 2015-11-17
```
sudo dkms remove -m ath10k -v 1.1 --all
```

Reboot, then
```
cd backports-20150903
make clean
make defconfig-ath10k
make
sudo make install
```

Reboot

---

### Post by Rish_Bhatia on 2015-11-23
Awesome - it worked. 

Thanks a lot!

---

### Post by Arnaud22 on 2016-04-05
hi everyone!

i happen to have the exact same wireless card as Rish_Bhatia on my yoga 3 14 (ubuntu 15.10) but im just missing something.

lspci -nnk | grep -iA2 net  ==>

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci

According to this thread i have the wrong firmware installed since i see "fw WLAN.RM.1.1-00141" when

dmesg | grep -i qca6174 ==>

[    2.564482] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    3.767434] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw WLAN.RM.1.1-00141 api 5 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad

so i went and followed  that (from [http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244))
wget [https://www.dropbox.com/s/nmgb5li6sd6i7ij/backath10k-dkms_2.0_all.deb](https://www.dropbox.com/s/nmgb5li6sd6i7ij/backath10k-dkms_2.0_all.deb)
dpkg -i backath10k-dkms_2.0_all.deb

without results since its still using the old firmware. i think im almost there, missing few steps...

Could anyone help?

if needed, i could post (but its quite long)

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info


also, it only gives me only bluetooth results when i type the following for some reason

rfkill list all; lsmod | grep ideapad ==>

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


thanks in advance for your help!
Arnaud

---

### Post by jeremy31 on 2016-04-06
For some reason the wrong firmware didn't get removed
```
sudo rm /lib/firmware/ath10k/QCA6174/hw2.1/*.bin
sudo cp /usr/src/backath10k-2.0/QCA6174/hw2.1/*.bin /lib/firmware/ath10k/QCA6174/hw2.1/
```

I know the backath10k-dkms doesn't work with the 4.2 kernel but the firmware files should be on your computer.  If you get an error about something does not exist
```
sudo cp /var/lib/dkms/backath10k/2.0/build/QCA6174/hw2.1/*.bin  /lib/firmware/ath10k/QCA6174/hw2.1/
```

Reboot and when wifi works again ```
sudo dkms remove backath10k/2.0 --all
```

---

### Post by Arnaud22 on 2016-04-08
thanks for your reply!

so i did the 1st 2 commands, didnt get any error but didnt get wireless card to work. here's the result of that (if any help)

dmesg | grep -i qca6174 ==>
[    2.632409] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2

---

### Post by jeremy31 on 2016-04-08
Post ```
dmesg | grep ath10k
```

---

### Post by Arnaud22 on 2016-04-08
dmesg | grep ath10k ==>
[    2.313314] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.553900] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    2.554682] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    2.554697] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[    2.639989] ath10k_pci 0000:02:00.0: otp calibration failed: 3
[    2.639996] ath10k_pci 0000:02:00.0: failed to run otp: -22
[    2.640000] ath10k_pci 0000:02:00.0: could not init core (-22)
[    2.640033] ath10k_pci 0000:02:00.0: could not probe fw (-22)

---

### Post by Arnaud22 on 2016-04-08
any hint thru [https://bbs.archlinux.org/viewtopic.php?id=196519](https://bbs.archlinux.org/viewtopic.php?id=196519) u think?

---

### Post by jeremy31 on 2016-04-11
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
sudo rm -r/lib/firmware/ath10k/QCA6174/
git clone [https://github.com/atondwal/ath10k-firmware.git](https://github.com/atondwal/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/
```

Reboot

---

### Post by Arnaud22 on 2016-04-11
respect!
man, thanks a lot for your help and time, proper success!!
u part of the many reasons i use linux! thks again
Arnaud

---


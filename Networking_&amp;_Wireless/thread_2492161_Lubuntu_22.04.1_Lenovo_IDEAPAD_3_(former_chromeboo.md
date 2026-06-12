---
title: "Lubuntu 22.04.1 Lenovo IDEAPAD 3 (former chromebook) wifi not working"
date: 2023-11-01
forum: Networking &amp; Wireless
---

### Post by ensto on 2023-11-01
Lubuntu 22.04.1 Lenovo IDEAPAD 3 (former chromebook) wifi not working. Everything worked when I was running Chromeos
Ive done lots of google-searching and ended up nowhere, I really appreciate any help!

wireless-info script result
```


########## wireless info START ##########


Report from: 01 Nov 2023 15:13 -03 -0300


Booted last: 01 Nov 2023 00:00 -03 -0300


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy


##### kernel ############################


Linux 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


00:0c.0 Network controller [0280]: Intel Corporation Gemini Lake PCH CNVi WiFi [8086:31dc] (rev 06)
	Subsystem: Intel Corporation Gemini Lake PCH CNVi WiFi [8086:0234]
	Kernel modules: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0aaa Intel Corp. Bluetooth 9460/9560 Jefferson Peak (JfP)
Bus 001 Device 002: ID 30c9:001c Luxvisions Innotech Limited EasyCamera 1M
Bus 001 Device 005: ID 346d:5678 USB Disk 2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


This system doesn't support Secure Boot


##### lsmod #############################


iwlwifi               569344  0
cfg80211             1241088  1 iwlwifi
wmi                    40960  1 video


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad
search .


##### network managers ##################


Installed:


	NetworkManager


Running:


root         460       1  0 14:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HomeWifi.nmconnection]] (600 root)
[connection] id=HomeWifi | type=wifi
[wifi] ssid=MYLUGER
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[iwlwifi]
filename:       /lib/modules/6.2.0-26-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
description:    Intel(R) Wireless WiFi driver for Linux
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for AX210 devices, 4K for other devices 1:4K 2:8K 3:12K (16K buffers) 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:0:disable, 1-15:FW_DBG_PRESET Values, 16:enabled without preset value defined,Debug INI TLV FW debug infrastructure (default: 16)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)
parm:           disable_11be:Disable EHT capabilities (default: false) (bool)


[cfg80211]
filename:       /lib/modules/6.2.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


grep: /sys/module/iwlwifi/parameters/enable_ini: Operation not permitted
[iwlwifi]
11n_disable: 0
amsdu_size: 0
bt_coex_active: Y
disable_11ac: N
disable_11ax: N
disable_11be: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    6.609434] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    6.609811] Bluetooth: hci0: Failed to load Intel firmware file intel/ibt-17-16-1.sfi (-2)
[    8.907823] sof-audio-pci-intel-apl 0000:00:0e.0: Direct firmware load for intel/sof/community/sof-glk.ri failed with error -2
[    8.907832] sof-audio-pci-intel-apl 0000:00:0e.0: error: sof firmware file is missing, you might need to
[    8.907839] sof-audio-pci-intel-apl 0000:00:0e.0: error: failed to load DSP firmware -2


########## wireless info END ############



```
More info
```

lspci -nnk | grep 0280 -A3
00:0c.0 Network controller [0280]: Intel Corporation Gemini Lake PCH CNVi WiFi [8086:31dc] (rev 06)
        Subsystem: Intel Corporation Gemini Lake PCH CNVi WiFi [8086:0234]
        Kernel modules: iwlwifi
00:0e.0 Multimedia audio controller [0401]: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio [8086:3198] (rev 06)




sudo dmesg | grep iwl
[    6.520095] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-46.ucode failed with error -2
[    6.520146] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-45.ucode failed with error -2
[    6.520410] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-44.ucode failed with error -2
[    6.520656] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-43.ucode failed with error -2
[    6.520698] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-42.ucode failed with error -2
[    6.520735] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-41.ucode failed with error -2
[    6.520771] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-40.ucode failed with error -2
[    6.520807] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-39.ucode failed with error -2
[    6.520845] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-38.ucode failed with error -2
[    6.520881] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-37.ucode failed with error -2
[    6.520921] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-36.ucode failed with error -2
[    6.520957] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-35.ucode failed with error -2
[    6.521012] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-34.ucode failed with error -2
[    6.521051] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-33.ucode failed with error -2
[    6.521086] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-32.ucode failed with error -2
[    6.521123] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-31.ucode failed with error -2
[    6.521158] iwlwifi 0000:00:0c.0: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-30.ucode failed with error -2
[    6.521161] iwlwifi 0000:00:0c.0: no suitable firmware found!
[    6.521166] iwlwifi 0000:00:0c.0: minimum version required: iwlwifi-9000-pu-b0-jf-b0-30
[    6.521169] iwlwifi 0000:00:0c.0: maximum version supported: iwlwifi-9000-pu-b0-jf-b0-46
[    6.521171] iwlwifi 0000:00:0c.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git


uname -r
6.2.0-26-generic



```

---

### Post by readableauthor on 2023-11-02
Do you have linux-firmware package installed?

---

### Post by ensto on 2023-11-02
dpkg says that it's installed, and working fine

---

### Post by ensto on 2023-11-02
Gentlmen! I apologize for wasting everyone's time! I managed to get access to a phone with usb tethering, ran apt update and apt upgrade, restarted my laptop, and everything works perfectly. 

But in case someone else has this issue, and is not so fortunate as to be able to access the internet, I had a pretty good lead. I was going to download the file referenced in 'sudo dmesg | grep iwl' from the linux-firmware github repo, transfer it by flash drive, and install it manually.

---


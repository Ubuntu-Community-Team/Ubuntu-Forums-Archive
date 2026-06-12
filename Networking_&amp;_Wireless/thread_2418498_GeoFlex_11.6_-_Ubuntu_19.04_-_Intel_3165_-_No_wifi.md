---
title: "GeoFlex 11.6 - Ubuntu 19.04 - Intel 3165 - No wifi"
date: 2019-05-07
forum: Networking &amp; Wireless
---

### Post by ricknic on 2019-05-07
I'm new to Ubuntu, recently upgraded my win10 GeoFlex 11.6 notebook to Ubuntu 19.04. Everything appears to be working correctly except no WiFi. I have run the wireless-info script. It looks like the WiFi hardware is detected, but in the WiFi settings it says "No Wi-Fi Adaptor found". Not sure where to start looking for information, can someone point me in the right direction.

Wireless-info Output below.

Cheers 

Rick


```
########## wireless info START ##########

Report from: 07 May 2019 12:23 BST +0100

Booted last: 07 May 2019 00:00 BST +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

##### kernel ############################

Linux 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 79)
    Subsystem: Intel Corporation Wireless 3165 [8086:8110]
    Kernel modules: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0585:3841 FlashPoint Technology, Inc. 
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

iwlwifi               311296  0
cfg80211              671744  1 iwlwifi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

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
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       671     1  0 11:51 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlwifi]
filename:       /lib/modules/5.0.0-13-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-43.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-43.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-43.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-43.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-43.ucode
firmware:       iwlwifi-Qu-b0-jf-b0-43.ucode
firmware:       iwlwifi-su-z0-43.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-43.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-43.ucode
firmware:       iwlwifi-QuQnj-b0-hr-b0-43.ucode
firmware:       iwlwifi-Qu-b0-hr-b0-43.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-43.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-43.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-43.ucode
srcversion:     B08FFD869CC51FDDC48BCCC
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.0.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:31:2B:78:
        92:2C:C0:87:DF:0A:5A:AF:C6:A9:A5:5F:50:00:31:4E:F2:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:68:B8:51:65:50:15:23:9A:83:B6:1F:
        0A:21:70:E4:77:7E:D6:B8:D8:01:CA:09:66:49:9E:18:D9:5C:AD:2D:
        DE:8B:85:B9:BB:78:F2:E9:8E:BE:EC:19:51:B1:61:42:01:94:C5:0E:
        7D:7B:46:DE:32:14:CB:D8:DD:A9:39:05:B1:27:AB:7E:96:6D:A0:65:
        D3:2D:83:E6:0A:93:57:E0:B7:1D:A9:11:C5:67:E8:42:EC:B8:55:16:
        1A:CE:B8:A2:DC:4E:6C:B2:BA:21:E2:03:34:B2:78:90:CA:DA:F3:06:
        B2:54:92:9E:7D:DA:FE:0D:DE:12:99:1D:17:78:55:C2:2C:4F:67:A6:
        2F:4E:B6:ED:72:5C:48:1E:B7:CA:44:9C:8C:B3:EF:54:E7:FC:30:93:
        54:57:B8:81:02:1D:45:CD:86:AD:7C:5A:CE:A4:BD:DE:DF:61:D7:8F:
        06:43:98:12:F5:CE:80:C2:6F:1D:7B:52:7A:5E:2C:CE:6A:A8:FA:87:
        C4:92:12:6F:93:4C:B4:31:37:D9:FB:4D:B3:3D:98:3A:D9:FB:BF:3B:
        9E:6B:57:AE:77:84:D4:81:8E:C7:92:AD:0D:84:43:EF:7E:79:4B:3A:
        68:2A:8E:D1:8C:05:C5:24:48:76:A3:EC:9C:39:C5:40:CB:8F:82:D7:
        00:7D:DE:18:B5:1B:FD:21:07:F0:F3:C3:8D:A8:03:0D:93:78:78:91:
        48:3B:EA:BD:BF:5C:B2:02:7A:9D:28:A5:7E:8D:0D:35:E5:FA:E0:8E:
        A8:AD:27:37:08:AA:83:DD:4E:0F:59:BF:AE:66:D8:DC:07:66:D1:F0:
        4D:16:38:E9:BC:7F:3A:54:DB:E1:F3:41:E6:B3:27:53:A3:8B:B9:95:
        46:66:9E:CB:8E:92:21:EC:40:5D:1B:EF:AB:E7:0C:D0:B4:33:A8:FB:
        CC:59:9B:B9:9F:C8:D5:1A:5E:F7:B2:78:03:D2:FE:42:02:43:72:91:
        B7:0B:B2:77:F9:25:15:1B:0C:BD:5E:37:DF:C0:EF:66:0E:65:48:E3:
        3A:71:4A:0B:1D:29:9A:28:25:94:13:CE:3E:F0:3F:5D:08:C3:77:9E:
        E1:88:AB:3B:46:19:51:A7:E7:0D:ED:7D:60:4D:15:30:AA:1C:25:64:
        1C:CD:BC:F7:40:75:8C:71:87:E3:12:CE:08:DD:05:F2:4F:53:C4:C1:
        80:8F:87:38:8F:7E:EA:49:73:78:3D:7B:E9:15:66:72:E7:CA:B2:F7:
        EB:9F:F2:14:1F:19:E4:29:A8:E2:B8:0B:81:D4:86:64:5A:C7:2F:7E:
        2F:55:E2:3A:73:D2:7E:8F:CA:0C:35:8B:70:8F:38:D9:FA:2E:AA:46:
        25
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for 22560 devices, 4K for other devices 1:4K 2:8K 3:12K 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: 0 (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/5.0.0-13-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2BD3ED72B421276E6C2918E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:31:2B:78:
        92:2C:C0:87:DF:0A:5A:AF:C6:A9:A5:5F:50:00:31:4E:F2:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:40:17:56:1C:64:E1:0D:28:ED:51:46:
        9E:0E:CF:D6:DB:31:52:B8:53:96:A9:2B:85:DB:E1:0F:34:9E:7A:3E:
        BB:31:FA:1F:6E:C6:94:0A:A7:97:67:DA:48:49:AB:9D:9C:70:27:9B:
        87:4A:CA:80:AC:53:40:30:EF:D3:7D:07:19:01:88:B1:A3:BB:12:55:
        6B:06:B6:66:EB:7B:B6:02:4B:FD:D5:4D:80:4E:A8:DA:38:B4:B2:C3:
        37:3A:03:85:7E:5C:67:CB:5B:1C:EB:23:C7:6C:C5:14:19:9B:FB:BF:
        18:EE:4B:D6:DB:8F:3A:71:1E:9E:91:64:6D:7E:74:9B:68:B5:4F:0F:
        D1:A2:EB:D3:C9:11:8C:2C:F9:6B:BB:3A:4A:AB:D8:94:01:34:6C:97:
        9E:95:D1:DE:70:F4:80:36:F0:74:62:87:57:27:87:2E:37:4C:D9:55:
        3B:CF:CD:0B:B3:16:95:73:B4:2E:EC:BA:8A:22:3E:9A:9E:C1:6E:58:
        2F:C3:C0:1D:CD:8A:6C:8A:C2:18:CE:DF:EB:57:B4:CC:A9:7A:60:BF:
        85:D9:8D:83:48:91:78:2C:AF:A5:D6:F1:5F:22:27:53:54:EF:9A:45:
        8B:89:6B:02:8D:9C:69:8A:F7:0B:93:AA:D5:3E:F2:17:76:C4:EC:88:
        88:03:46:4F:4C:7D:26:A5:6E:04:39:77:FE:80:F7:74:31:38:3D:29:
        85:4B:8C:1E:7D:3C:1F:AE:67:20:C6:FC:84:48:C8:FD:47:25:76:1E:
        0E:84:23:5E:42:C6:63:FF:35:3F:20:8D:7F:14:91:D0:15:A8:C7:EE:
        DE:08:05:D3:CC:72:5D:25:D2:15:9A:01:4C:E6:54:E3:9E:B2:63:DF:
        DE:5C:71:15:C0:20:5D:B5:B7:57:11:2F:B8:B3:EE:82:C7:5B:F0:F1:
        AD:39:26:1B:B6:D0:13:8D:27:AE:AF:57:9C:5E:59:95:DF:9E:B8:42:
        D2:29:8C:4C:5B:FA:F4:28:D7:73:05:46:C4:80:59:C0:38:47:D3:91:
        B9:D7:8E:A9:D2:5E:5A:D8:8C:F9:4B:33:8E:70:A1:F4:D2:F4:41:08:
        E7:5B:39:3D:74:E5:B5:D9:46:78:81:26:DD:CB:E9:FE:8B:FE:5A:D7:
        5F:A7:C1:11:50:E4:FC:3B:EC:7B:21:19:23:60:F4:84:81:78:DA:AE:
        0C:FF:E5:DB:7C:CE:01:9D:6D:71:46:0B:6A:8B:48:C3:82:DB:FC:95:
        12:78:A5:A1:A9:38:FE:39:C3:0C:97:81:0D:F4:8F:7A:27:DB:30:E2:
        1E:AB:96:E7:80:E3:7C:CB:F0:34:09:41:87:22:D1:0D:55:21:30:39:
        D1
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
disable_11ax: N
enable_ini: N
fw_monitor: N
fw_restart: Y
lar_disable: N
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

########## wireless info END ############
```

---


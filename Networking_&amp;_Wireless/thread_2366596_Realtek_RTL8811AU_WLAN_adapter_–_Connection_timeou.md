---
title: "Realtek RTL8811AU WLAN adapter – Connection timeout"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by redyah on 2017-07-19
Hello forum,

 
[LIST]
[*] **Specs** 
[/LIST]
 I run Xubuntu 17.04 (uname -r: 4.10.0-28-generic) on a Samsung NP275E5E laptop. Since its integrated WLAN adapter is broken I bought an external 802.11ac USB WLAN adapter, the DMG-19 by Inter-Tech.
It uses the Realtek RTL8811AU chipset according to spec sheet (manufacturers website: [https://www.inter-tech.de/en/products/networking/wlan-adapter/dmg-19](https://www.inter-tech.de/en/products/networking/wlan-adapter/dmg-19)).

 
[LIST]
[*] **Community driver** 
[/LIST]
 Since the adapter didn’t work out of the box I compiled and installed a community driver from github as described in this tutorial: [URL="https://medium.com/@at15/ubuntu-16-04-8811au-wireless-driver-d29d6929a50c"]https://medium.com/@at15/ubuntu-16-04-8811au-wireless-driver-d29d6929a50c
[/URL]
 ```

 sudo apt-get update
 sudo apt-get install linux-headers-generic build-essential git
 git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
 cd rtl8812AU_8821AU_linux
 make
 sudo make install
 sudo modprobe rtl8812au
 
```

 It compiled and installed without error, the adapter is recognized and detecting Wi-Fi networks in my area.
 
 
[LIST]
[*] **Connection problem** 
[/LIST]
 It also detects my home network, however, when I try to connect to it by clicking its name in the drop down list of the Network Indicator Plugin in the taskbar nothing happens. After a few seconds a pop-up window appears telling me (see attached screenshot): Failed to add/activate connection, (24) Timeout was reached.
 
 I’ve tried multiple networks both 2.4 and 5 Ghz non of which I could connect to. My router broadcasts both 2.4 and 5 Ghz, visible SSID and WPA2-PSK with AES encryption and no MAC filtering or similar enabled. Other devices have never had a problem connection to my network.
 
 In the Xfce indicator applet it also shows 2 distinct WLAN adapters (2.4 and 5 Ghz maybe?). I’ve tried both.
 
 I also tested the WLAN adapter on my Windows 10 PC on which it works flawlessly.
 
 Thank you for your time,
 Redyah

---

### Post by BenginM on 2017-07-19
Salutations! and welcome to the forums .

please check the stick thread , install and run the wierless info script and paste it here under a [CODE} tag 



the error message in the image related to a problem with login and display manager , which login manager does xfce uses , you might want to try gdm or lightdm or even a lightweight login manager..*SLiM , SDDM , XDM .. and see if the problem persists , if not then it's another problem.. *

---

### Post by redyah on 2017-07-19
Thank you for your answer!

Here is the pastebin link for the output of the wireless script: [https://pastebin.com/36Hb43QQ](https://pastebin.com/36Hb43QQ)

The script would run for a long time and only stopped when I  disconnected the WLAN adapter. I assume this is caused by the "dmesg" errors at the bottom of the document.

I will try a different login manager tomorrow, thanks for the suggestion.

Wireless script output:

```

########## wireless info START ##########

Report from: 19 Jul 2017 23:05 CEST +0200

Booted last: 19 Jul 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-28-generic #32-Ubuntu SMP Fri Jun 30 05:32:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Samsung Electronics Co Ltd RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [144d:c680]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 004: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: phy5: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8812au            1380352  0
cfg80211              602112  1 rtl8812au
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 0.0.0.0  netmask 255.255.255.0  broadcast 0.0.0.0
        inet6 fe80::74c2:bf82:5bac:b33a  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 3869  bytes 4250118 (4.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2568  bytes 308317 (308.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 334  bytes 24762 (24.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 334  bytes 24762 (24.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp0s22f2u2: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 8  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx40a5efd7efaa: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 8  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp6s0    no wireless extensions.

lo        no wireless extensions.

wlx40a5efd7efaa  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlp0s22f2u2  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0      0.0.0.0         UG    100    0        0 enp6s0
0.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp6s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       801     1  4 22:59 ?        00:00:15 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

Timeout was reached

Error: nmcli terminated by signal Interrupt (2)

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=user:user:;
[wifi] mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp6s0    no frequency information.

lo        no frequency information.

wlx40a5efd7efaa  32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency=2.412 GHz (Channel 1)

wlp0s22f2u2  32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

enp6s0    Interface doesn't support scanning.

wlp0s22f2u2  Failed to read scan data : No such device

lo        Interface doesn't support scanning.

wlx40a5efd7efaa  No scan results

##### module infos ######################

[rtl8812au]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/net/wireless/rtl8812au.ko
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     E122F10E461515FFF1AC954
depends:        cfg80211
vermagic:       4.10.0-28-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_led_enable:Enable status LED (int)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask vaule:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse vaule:0 (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

[cfg80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8812au]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_adaptivity_dml: 0
rtw_adaptivity_en: 0
rtw_adaptivity_mode: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_amplifier_type_2g: 0
rtw_amplifier_type_5g: 0
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_bw_mode: 33
rtw_channel: 1
rtw_channel_plan: 89
rtw_chip_version: 0
rtw_decrypt_phy_file: 0
rtw_enusbss: 0
rtw_FileMaskEfuse: 0
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_led_enable: 1
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_OffEfuseMask: 0
rtw_power_mgnt: 1
rtw_qos_opt_enable: 0
rtw_rf_config: 5
rtw_RFE_type: 64
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_special_rf_path: 0
rtw_TxBBSwing_2G: 255
rtw_TxBBSwing_5G: 255
rtw_tx_pwr_by_rate: 0
rtw_tx_pwr_lmt_enable: 0
rtw_usb_rxagg_mode: 2
rtw_vcs_type: 1
rtw_vht_enable: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[cfg80211]
bss_entries_limit: 1000
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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  447.200442] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  447.322943] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  447.659844] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  447.782020] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  448.110711] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  448.233172] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  448.564545] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  448.692679] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  449.020651] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  449.142612] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  449.473208] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  449.597007] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  449.930358] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  450.051543] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  450.391387] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  450.505363] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  450.842039] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  450.962469] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  451.291160] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  451.418924] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  451.750910] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  451.872768] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  452.203009] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  452.346214] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  452.677104] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  452.810261] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  453.138309] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  453.260893] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  453.599861] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  453.720636] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  454.050387] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  454.173113] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  454.515098] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  454.640005] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  454.974901] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  455.097659] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  455.429133] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  455.561294] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  455.914215] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  456.035637] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  456.375983] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  456.489896] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  456.827100] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  456.947419] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  457.287359] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  457.399048] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  457.731272] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  457.861634] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  458.195155] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  458.326182] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  458.660496] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  458.794831] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  459.125069] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  459.243838] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  459.579338] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  459.708221] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  460.034751] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  460.162930] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  460.490624] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  460.612381] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  460.926204] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  461.048011] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  461.375422] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  461.497274] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  461.836335] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  461.963193] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  462.295340] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  462.424237] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  462.756059] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  462.883371] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  463.213846] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  463.337745] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  463.673049] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  463.803712] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  464.147608] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  464.267955] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  464.599207] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  464.721538] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  465.052093] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  465.173656] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  465.502962] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  465.630930] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  465.963232] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  466.090561] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  466.421099] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  466.541705] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  466.875699] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  467.001521] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  467.333880] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  467.458789] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  467.788808] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  467.913945] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  468.239787] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  468.361136] IPv6: ADDRCONF(NETDEV_UP): wlx40a5efd7efaa: link is not ready
[  468.694791] IPv6: ADDRCONF(NETDEV_UP): wlp0s22f2u2: link is not ready
[  468.761257] RTL871X: rtw_ndev_uninit(wlx40a5efd7efaa)
[  469.037315] RTL871X: rtw_ndev_uninit(wlp0s22f2u2)

########## wireless info END ############

```

---

### Post by chili555 on 2017-07-19
Please open a terminal and do:```
cd rtl8812AU_8821AU_linux
gedit Makefile
```

Find the line that contains EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE and insert a # symbol at the beginning of that line. It is about line 873. This comments that line and disables concurrent mode. Proofread carefully, save and close the text editor. Next, continue:
 ```
make clean
make
sudo make install

```Next, do:```
cd
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```Reboot and let us hear the result. If the wireless is not working, we'll need a new wireless script report.

---

### Post by redyah on 2017-07-20
Thanks for your answer!

Your solution fixed my problem; Wi-Fi works now!

One last question: After a kernel update I have to recompile and reinstall the driver, right?

Thanks again for your time,
Redyah

---

### Post by chili555 on 2017-07-20
> **redyah said:**
> Thanks for your answer!

Your solution fixed my problem; Wi-Fi works now!

One last question: After a kernel update I have to recompile and reinstall the driver, right?

Thanks again for your time,
Redyah
Correct. Please retain the file for that time.

You needn't redo the Makefile edit nor the printf.

Glad it's working.

---

### Post by SeijiSensei on 2017-07-21
I'm using a different driver for my rtl8812AU from here:  [https://github.com/diederikdehaas/rtl8812AU/tree/driver-4.3.14](https://github.com/diederikdehaas/rtl8812AU/tree/driver-4.3.14)

It supports dkms so you can set it up to automatically rebuild the driver if the kernel changes.

---


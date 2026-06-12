---
title: "wifi nightmare with TP-Link Archer T4U // rtl8812au driver"
date: 2017-06-12
forum: Networking &amp; Wireless
---

### Post by odorono2 on 2017-06-12
Hello

hope somebody can help me trouble-shoot this and eventually solve the problem. It's been giving me headaches since I upgraded to Ubuntu 16.04. Wireless adapter is a USB TP-Link Archer T4U , which is supposed to use the Realtek RTL8812AU chipset.

More on the wireless adapter here: [https://wikidevi.com/wiki/TP-LINK_Archer_T4U](https://wikidevi.com/wiki/TP-LINK_Archer_T4U)

Using the rtl8812au driver through dkms, over the repositories. 

Problem is that 90% of the times wifi won't work after start-up. Sometimes, unplugging and plugging in the USB adapter is enough to get it working. But lately, that doesn't do the trick, neither restarting the network interface, but it will just work if I remove the driver and install it again whilst connected over the wired connection.

Even if it works, connection drops after some time -- sometimes hours, sometimes in a matter of minutes. 

Sometimes the device is listed in the network interfaces, but network manager doesn't show any networks, and sometimes it shows the networks but it fails to connect. 

Some additional stuff I noticed: 
-- why does the device have such a weird name (starting with enxe......) instead of the usual wlan1 or similar? 
-- why is there no device information in the output of lsusb? Although device ID is correct...

Hope someone can help! Will be forever grateful. Here's the output of the wireless info script: 

```

########## wireless info START ##########

Report from: 13 Jun 2017 01:01 CEST +0200

Booted last: 13 Jun 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-79-generic #100-Ubuntu SMP Wed May 17 19:58:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b]
    DeviceName:  Onboard LAN
    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection I217-V [1458:e000]

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 016: ID 2357:0101  
Bus 003 Device 004: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 003 Device 002: ID 0424:a700 Standard Microsystems Corp. 2 Port Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              565248  0
8812au                905216  0
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  11 snd_ice1712,snd_soc_rt5640,snd_usb_audio,snd_ac97_codec,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

auto enx<IF from MAC [IF2]>
iface enx<IF from MAC [IF2]> inet dhcp
    wireless-essid pizzaiolo
    wireless-ap <MAC address>

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:261237 errors:0 dropped:1 overruns:0 frame:0
          TX packets:212954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218746904 (218.7 MB)  TX bytes:50322965 (50.3 MB)
          Interrupt:20 Memory:f7100000-f7120000 

enx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF2]>' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27213 errors:0 dropped:66 overruns:0 frame:0
          TX packets:22220 errors:0 dropped:9 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22579531 (22.5 MB)  TX bytes:4573812 (4.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:120112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:10442313 (10.4 MB)  TX bytes:10442313 (10.4 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

enx<IF from MAC [IF2]>  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=5.18 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root     14237     1  0 Jun12 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         rtl8812au
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5.3/3-5.3:1.0/net/enx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/pizzaiolo 3]] (600 root)
[connection] id=pizzaiolo 3 | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pizzaiolo 6]] (600 root)
[connection] id=pizzaiolo 6 | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pizzaiolo 4]] (600 root)
[connection] id=pizzaiolo 4 | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KRAFTBOX]] (600 root)
[connection] id=KRAFTBOX | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=KRAFTBOX
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pizzaiolo 5]] (600 root)
[connection] id=pizzaiolo 5 | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pizzaiolo 1]] (600 root)
[connection] id=pizzaiolo 1 | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pizzaiolo 2]] (600 root)
[connection] id=pizzaiolo 2 | type=wifi | permissions=user:guest-iwskmu:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pizzaiolo]] (600 root)
[connection] id=pizzaiolo | type=wifi | permissions=user:sergi:;
[wifi] mac-address=<MAC 'enx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=pizzaiolo
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

enx<IF from MAC [IF2]>  32 channels in total; available frequencies :
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
          Current Frequency:5.18 GHz (Channel 36)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

enx<IF from MAC [IF2]>  No scan results

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-79-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     48C96882CCDC964173BE1D1
depends:        
intree:         Y
vermagic:       4.4.0-79-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[8812au]
filename:       /lib/modules/4.4.0-79-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5E9D12706FAF7E2BB4F284E
depends:        
vermagic:       4.4.0-79-generic SMP mod_unload modversions 
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
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_nhm_en:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[8812au]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
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
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 0
rtw_lbkmode: 0
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_nhm_en: 0
rtw_notch_filter: 0
rtw_power_mgnt: 0
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

##### /etc/modules ######################

coretemp
it87

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

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[24607.565299] RTL871X: rtw_ndev_uninit(enx<IF from MAC [IF2]>)
[24641.997975] RTL871X: rtw_ndev_init(wlan0)
[24643.006834] rtl8812au 3-5.3:1.0 enx<IF from MAC [IF2]>: renamed from wlan0
[24643.047700] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[24647.556398] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready
[25990.651868] e1000e: eno1 NIC Link is Down
[27414.592602] RTL871X: linked_status_chk(enx<IF from MAC [IF2]>) disconnect or roaming
[27438.030191] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF2]>: link is not ready (repeated 4 times)
[49434.291479] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[49518.660389] e1000e: eno1 NIC Link is Down

########## wireless info END ############


```

---

### Post by chili555 on 2017-06-12
> -- why does the device have such a weird name (starting with enxe......) instead of the usual wlan1 or similar? Because of persistent naming: [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) 

Before you undertake epic measures to overcome it, I suggest that you acclimate to it. There is nothing more logical about enx-whatever than wlan0 or eth1 or wifi0. The only thing sure about Linux is change.

> -- why is there no device information in the output of lsusb? Although device ID is correct...That's what Realtek codes or doesn't code into the chip. It doesn't hurt anything once we Google the usb.id and understand it.> but network manager doesn't show any networks, That's what you asked for by populating /etc/network/interfaces. You told Network Manager that you will manage connections; not NM.```
auto lo
iface lo inet loopback

auto enx<IF from MAC [IF2]>
iface enx<IF from MAC [IF2]> inet dhcp
    wireless-essid pizzaiolo
    wireless-ap <MAC address>
```This implies *NO* encryption. Can that possibly be correct? I hope not.

I suggest that you try loading the driver automagically on boot to see if it helps:```
sudo -i
echo 8812au  >>  /etc/modules
exit
```Reboot and let us know if it helps.

---

### Post by odorono2 on 2017-06-13
Hello again
Chili, many thanks for your answer. 

I reverted to the original interfaces file, and I added your suggestion to /etc/modules

the first time I rebooted the wifi network was working, so some progress there, however it dropped after 10 minutes or so. Network manager wouldn't show any network whatsoever. 
Here's the output of wireless-info when this happened: [https://paste.ubuntu.com/24846781/](https://paste.ubuntu.com/24846781/)

Second time I rebooted, it wasn't working. Network manager would show the networks available and kept trying to connect to the desired one, but it didn't manage. 
Here's the output of wireless-info at this stage: [https://paste.ubuntu.com/24846773/](https://paste.ubuntu.com/24846773/)


Any more suggestions maybe? 
Thanks again

---

### Post by Hadaka on 2017-06-13
Hi, the 2.4 and 5 GHz connections have the same ssid
so it is flopping bewteen the two
```
pizzaiolo  <MAC 'pizzaiolo' [AC1]>  Infra  36    5180 MHz  35 Mbit/s  93  &#9602;&#9604;&#9606;&#9608;  WPA2  no        
pizzaiolo  <MAC 'pizzaiolo' [AC13]>  Infra  5     2432 MHz  54 Mbit/s  77 &#9602;&#9604;&#9606;_  WPA2 no
```
and in an attempt to connect you have added more. pizzaiol 1,  pizzaiol 2.....3....4
Click the wifi icon..then >> Edit connections >> wireless and delete them all.
add back in as something like... pizzaiol   pizzaiol-5G
then do..
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
remove wired connection...boot and test wireless
Thanks.

---

### Post by chili555 on 2017-06-13
In addition to Hadaka's excellent suggestions, I also recommend that the SSIDs in the router be renamed to something like pizzaiolo2.4 and pizzaiolo5 or some such. As well, we note that there are 5  APs on Frequency:5.18 GHz (Channel 36), including pizzaiolo. I'd suggest that you change the router to another channel, perhaps 48 where there is no other AP. 

Whether this USB wireless will do 802.11N and AC reliably remains to be seen. Once you have the two SSIDs renamed, connect to the 2.4 GHz segment and see if it's reliable and fast. Do the same with the 5 GHz segment and please post back to tell us the result.

---


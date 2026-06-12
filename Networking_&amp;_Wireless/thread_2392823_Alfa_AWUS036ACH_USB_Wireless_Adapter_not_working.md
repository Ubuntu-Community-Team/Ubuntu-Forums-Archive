---
title: "Alfa AWUS036ACH USB Wireless Adapter not working"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by ashwinjmathew on 2018-05-25
I've been trying to get my new Alfa USB WiFi adapter to work for the last 2 days with no success. I tried with both the default rtl8812au-dkms package from the 18.04 repositories, and the updated driver from [https://github.com/kimocoder/rtl8812au](https://github.com/kimocoder/rtl8812au). In both cases, I am able to see my wireless network in network-manager, and connect to it - but my gateway is unreachable. Here's the output from @jeremy31's wireless-info script:
[http://paste.ubuntu.com/p/z4XyjsRbp2/](http://paste.ubuntu.com/p/z4XyjsRbp2/)

---

### Post by praseodym on 2018-05-26
> ```
[    4.698464] 8812au: loading out-of-tree module taints kernel.
[    4.699013] 8812au: module verification failed: signature and/or required key missing - tainting kernel
```
Deactivate SecureBoot

---

### Post by ashwinjmathew on 2018-05-27
Thanks for the help! But secure boot is disabled on my system. 
```

> mokutil --sb-state
SecureBoot disabled

```

Any idea what else might be causing my problem?

---

### Post by praseodym on 2018-05-27
Please show```

modinfo 8812au
locate *8812au*.ko | grep lib
dkms status
```

---

### Post by ashwinjmathew on 2018-05-27
Here we go. Thanks for your help!

```

> modinfo 8812au
filename:       /lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/8812au.ko
version:        v5.1.5_19247.20160830
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     530C1A1BBFD888A96719878
alias:          usb:v056Ep4007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p029Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0242d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep400Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep400Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0823d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp0820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2604p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p025Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0122d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p010Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p010Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p010Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       4.15.0-22-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
parm:           rtw_excl_chs:exclusive channel array (array of uint)
parm:           rtw_force_igi_lb:force IGI low-bound, 0:no specified (int)
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_pwrtrim_enable:int
parm:           rtw_initmac:charp
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
parm:           rtw_beamform_cap:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_check_hw_status:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
parm:           rtw_adaptivity_th_l2h_ini:TH_L2H_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:TH_EDCCA_HL_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_powertracking_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gh:uint
parm:           rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
parm:           rtw_led_ctrl:Led Control: 0=Always off, 1=Normal blink, 2=Always on (int)

```

```

> locate *8812au*.ko | grep lib
/lib/modules/4.15.0-22-generic/kernel/drivers/net/wireless/8812au.ko

```

```

> dkms status
rtl8812au, 5.1.5, 4.15.0-22-generic, x86_64: installed (WARNING! Diff between built and installed module!)

```

---

### Post by praseodym on 2018-05-28
Lets try the other one
```

sudo modprobe -rfv 8812au
sudo modprobe -v rtl8812au
```

---

### Post by ashwinjmathew on 2018-05-28
Looks like I'm missing something?

```

> sudo modprobe -rfv 8812au 
rmmod 8812au
rmmod cfg80211

> sudo modprobe -v rtl8812au
modprobe: FATAL: Module rtl8812au not found in directory /lib/modules/4.15.0-22-generic

```

---

### Post by praseodym on 2018-05-29
Lets check
```

sudo dkms autoinstall
```

---

### Post by ashwinjmathew on 2018-05-31
I get no response when I try that command.

---

### Post by ashwinjmathew on 2018-05-31
Ok, this is weird... everything seems to be working now. I ran:
```

> sudo modprobe -v 8812au

```
... and my adapter connected. Hopefully this configuration stays stable, but it would be nice to know how it started working.

Thanks for your help. I'll file this in the category of "it wasn't working before, but now it is".

---

### Post by ashwinjmathew on 2019-02-06
After many months of working fine, the adapter has suddenly stopped working again. lsusb shows it connected. I've tried rebuilding and reinstalling the driver, but no luck.

I'd appreciate any guidance on how to go about diagnosing and fixing this problem...

---

### Post by jeremy31 on 2019-02-06
See the wireless script link in my signature and post results

---

### Post by ashwinjmathew on 2019-02-06
Thanks! Here's the output:
```


########## wireless info START ##########

Report from: 06 Feb 2019 16:34 PST -0800

Booted last: 06 Feb 2019 00:00 PST -0800

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic

##### kernel ############################

Linux 4.18.0-14-generic #15-Ubuntu SMP Mon Jan 14 09:01:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7851]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              663552  0
mxm_wmi                16384  0
wmi                    24576  1 mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp2s0
iface enp2s0 inet dhcp

##### ifconfig ##########################

enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.1.85  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4ecc:6aff:febb:eeb3  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1700:9751:1b30:4ecc:6aff:febb:eeb3  prefixlen 64  scopeid 0x0<global>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 75235  bytes 111803557 (111.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 36757  bytes 2485974 (2.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 394  bytes 35172 (35.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 394  bytes 35172 (35.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.0.53
search attlocal.net
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1309     1  0 16:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
IP4.ADDRESS[1]:                         192.168.1.85/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 0
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.1.254, mt = 0
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         2600:1700:9751:1b30:4ecc:6aff:febb:eeb3/64
IP6.ADDRESS[2]:                         fe80::4ecc:6aff:febb:eeb3/64
IP6.GATEWAY:                            fe80::4e12:65ff:fe60:eba0
IP6.ROUTE[1]:                           dst = 2600:1700:9751:1b30::/64, nh = ::, mt = 256
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = ::/0, nh = fe80::4e12:65ff:fe60:eba0, mt = 1024
IP6.ROUTE[4]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/aloash 1]] (600 root)
[connection] id=aloash 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=aloash
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/aloash]] (600 root)
[connection] id=aloash | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=aloash
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.18.0-14-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-14-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:38:62:B4:
        4E:30:0F:6C:34:1C:EE:DA:8B:AA:32:90:DE:27:BD:05:A9:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:B4:20:8E:F4:66:EA:54:78:60:F1:DE:
        12:9F:02:74:9C:A3:A1:B3:D4:2E:F3:47:85:CE:86:2F:C4:8C:15:86:
        5C:29:3E:F0:4A:59:52:FA:B7:91:1E:FA:D7:44:BE:A1:D4:03:44:F5:
        5E:20:CF:C1:15:AC:18:B8:86:C5:05:8A:3E:ED:4E:E6:55:16:7E:03:
        FC:16:6E:33:5D:5C:B8:3F:86:82:F5:A3:CB:E9:F7:81:69:22:32:D3:
        AF:B0:9D:0C:6F:A1:12:63:AC:A6:5F:80:77:E1:E2:11:99:AB:12:06:
        0C:09:AD:BC:36:AB:7F:C1:FB:23:EC:A8:F4:66:6D:51:9C:C8:DD:AF:
        D2:10:00:4D:D8:12:95:7D:64:FF:76:B9:C5:A1:01:6C:0A:FF:D9:81:
        C4:11:0E:0A:C7:C9:AA:ED:85:D8:CF:5C:0D:22:14:2F:A7:92:24:75:
        7B:4F:B7:81:19:07:BF:79:68:93:2A:76:19:9C:69:E9:83:38:9F:70:
        01:A2:93:76:AD:3C:8E:6A:CB:78:F1:C2:FE:E0:8C:D2:6E:99:C7:D9:
        B5:5A:39:5C:4A:74:A2:4A:DC:7D:C1:15:D6:04:C6:01:63:64:9B:5C:
        50:E0:A7:6D:E0:7E:82:0D:37:28:CF:6B:82:43:54:B8:3D:B3:A8:64:
        7A:DE:BA:F7:10:F1:7A:76:05:A5:E6:1E:03:E4:3E:2D:7A:26:79:26:
        27:8D:DF:8B:D2:76:23:33:4C:98:6D:52:93:8C:40:35:9A:32:96:18:
        12:69:86:7C:74:79:35:A5:7B:BE:88:50:5E:AF:F0:05:B3:23:28:DA:
        8E:F1:EB:A3:47:8B:1A:92:78:F9:83:76:F9:9E:E4:44:98:2A:EE:C2:
        1A:7B:D6:E4:77:90:47:82:6D:41:4E:A3:12:7F:55:4B:81:E9:31:C2:
        E2:19:3B:0F:34:18:9C:4C:CC:C1:2E:18:04:B3:7E:F9:4D:F3:DE:E0:
        28:FF:39:EF:0B:09:63:66:98:70:13:7D:E7:44:7A:64:3D:D4:A1:B8:
        34:A6:94:E8:38:37:7F:26:BA:AA:AA:F8:B5:A8:F8:1C:38:70:03:75:
        6E:5B:4C:EE:9D:B3:A2:69:1A:5C:D7:AD:CE:EB:1C:5D:70:1D:57:91:
        15:4D:5E:83:1C:02:F3:69:14:06:19:1C:ED:A9:69:3A:1B:8B:63:47:
        2A:71:7E:8D:8E:29:77:65:BD:BF:27:24:AC:0A:33:4F:CB:D6:29:61:
        F7:91:D1:92:47:EE:E6:B0:68:31:E7:B3:3B:CA:AF:CB:22:A4:F4:0C:
        EB:B3:32:B7:1E:0E:02:41:E9:76:E8:57:0E:E6:B1:33:CD:3E:6B:95:
        F5
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

coretemp
nct6775

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

[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   86.195813] IPv6: ADDRCONF(NETDEV_UP): wlx00c0ca967b5c: link is not ready
[  213.330804] 8812au 6-2:1.0 wlx00c0ca967b5c: renamed from wlan0
[  213.355695] IPv6: ADDRCONF(NETDEV_UP): wlx00c0ca967b5c: link is not ready (repeated 2 times)
[  214.811826] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00c0ca967b5c: link becomes ready
[  214.869312] IPv6: ADDRCONF(NETDEV_UP): wlx00c0ca967b5c: link is not ready
[  223.776307] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00c0ca967b5c: link becomes ready
[  429.823270] rtl8812au 6-2:1.0 enx00c0ca967b5c: renamed from wlan0
[  462.172987] UpdateHalRAMask8812A => mac_id:0, networkType:0x44, mask:0xfffffff0 (repeated 2 times)

########## wireless info END ############


```

---


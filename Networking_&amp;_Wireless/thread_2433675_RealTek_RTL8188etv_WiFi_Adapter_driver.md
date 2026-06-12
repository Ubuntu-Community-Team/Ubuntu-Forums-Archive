---
title: "RealTek RTL8188etv WiFi Adapter driver"
date: 2019-12-23
forum: Networking &amp; Wireless
---

### Post by jacqpret on 2019-12-23
[SIZE=2]Hi

I purchased a RealteK 502.11N RTL8188etv USB Network Adapter [COLOR=#24292E][FONT=-apple-system]with monitor mode & frame injection support[/FONT][/COLOR], it works like a charm in Windows 10 but the drivers supplied with it for LInix were outdated and not compatible with the Kernel: 5.3.0-26-generic of Ubuntu 19.10. I installed the driver from [https://github.com/aircrack-ng/rtl8188eus](https://github.com/aircrack-ng/rtl8188eus) without any errors. When I reboot my laptop  and run **lsusb** I get the following output:

```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. Bluetooth Radio 
Bus 002 Device 005: ID 04f2:b572 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
**Bus 002 Device 003: ID 0bda:f179 Realtek Semiconductor Corp. 802.11n**
Bus 002 Device 002: ID 0e8f:00a7 GreenAsia Inc. 2.4G RX
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

```
**usb-devices**:
[/SIZE]```
IFT: Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0bda ProdID=f179 Rev=00.00
S: Manufacturer=Realtek
S: Product=802.11n
S: SerialNumber=00E0232CA8F6
C: #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:[SIZE=2]#=0x0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
[/SIZE]
```[SIZE=2]
 **ifconfig: (only reflects my internal Realtek adapter)**
```
enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether c8:5b:76:c7:93:c8  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 8524  bytes 481936 (481.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8524  bytes 481936 (481.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

```
wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.56  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::14bd:4d53:6200:43a7  prefixlen 64  scopeid 0x20<link>
        ether c8:3d:d4:74:9f:a1  txqueuelen 1000  (Ethernet)
        RX packets 21588  bytes 15509222 (15.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 19960  bytes 3862224 (3.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

```[/SIZE]
[SIZE=3]
[SIZE=2]Where am I going wrong?

Thank You[/SIZE]
[/SIZE]

---

### Post by praseodym on 2019-12-23
[https://github.com/kelebek333/rtl8188fu](https://github.com/kelebek333/rtl8188fu)

Here you go :)

---

### Post by jacqpret on 2019-12-23
Thank you praseodym, installed and connecting 100%, driver doesn't allow for monitor mode & frame injection which the network adapter was purchased for, will use it for my internet connection and use internal card for Kali.

---

### Post by praseodym on 2019-12-23
Lets check

```
modinfo rtl8188fu
```

---

### Post by jacqpret on 2019-12-23
```
root@kali &#57520; &#61461; ~ &#57520; modinfo rtl8188fu                         &#57522; &#61452; &#57523; &#58900;  &#57522; 604 &#57522; 22:59:48 &#61463; 
filename:       /lib/modules/5.3.0-kali3-amd64/kernel/drivers/net/wireless/rtl8188fu.ko
version:        v4.3.23.6_20964.20170110
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
firmware:       rtlwifi/rtl8188fufw.bin
srcversion:     0D9521C515203BE4620DC67
alias:          usb:v0BDApF179d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211,usbcore
retpoline:      Y
name:           rtl8188fu
vermagic:       5.3.0-kali3-amd64 SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
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
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_switch_usb3:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
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
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
```

---


---
title: "Driver for RTL8811 Wireless Adapter for Ubuntu 18.04"
date: 2018-12-06
forum: Networking &amp; Wireless
---

### Post by varunkalia on 2018-12-06
Does anyone have an experience of installing the drivers for RTL8811 Wireless Adapter for Ubuntu 18.04 ?

---

### Post by chili555 on 2018-12-06
Is it a USB adapter? Please run and post:```
lsusb
```Thanks.

---

### Post by varunkalia on 2018-12-06
Hello,
Output is :
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:64ad Microdia 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 003 Device 003: ID 0bda:c811 Realtek Semiconductor Corp**. 
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2018-12-06
Please get a working internet connection by ethernet, tethering or whatever means possible. Open a terminal and do:

```
sudo apt update
sudo apt install build-essential git dkms
git clone https://github.com/whitebatman2/rtl8821CU.git
DRV_NAME=rtl8821CU
DRV_VERSION=5.2.5.3
sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
git archive master | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
```Post back any errors, warnings, etc.

---

### Post by varunkalia on 2018-12-07
Man ! I cannot describe how grateful I am . I have been looking for a solution for days now. Your solution worked perfectly ! You are the man . Thanks a lot !
I just added one step. Everything else was smooth.

sudo apt update
sudo apt install build-essential git dkms
git clone [https://github.com/whitebatman2/rtl8821CU.git](https://github.com/whitebatman2/rtl8821CU.git)
DRV_NAME=rtl8821CU
DRV_VERSION=5.2.5.3
sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
**cd $DRV_NAME**
git archive master | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}

---

### Post by chili555 on 2018-12-07
> **varunkalia said:**
> Man ! I cannot describe how grateful I am . I have been looking for a solution for days now. Your solution worked perfectly ! You are the man . Thanks a lot !
I just added one step. Everything else was smooth.

sudo apt update
sudo apt install build-essential git dkms
git clone [https://github.com/whitebatman2/rtl8821CU.git](https://github.com/whitebatman2/rtl8821CU.git)
DRV_NAME=rtl8821CU
DRV_VERSION=5.2.5.3
sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
**cd $DRV_NAME**
git archive master | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}Ah! Yes! Good catch and thanks for pointing it out.

Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by andrew.g7mns on 2018-12-24
Thank you Chili555, worked well for me

Regards

Andrew

---

### Post by praseodym on 2018-12-24
Bookmarked, thx Chili.

modinfo 8821cu
```
filename:       /lib/modules/4.4.0-141-generic/updates/dkms/8821cu.ko
version:        v5.2.5.3_24795.20171031_COEX20170310-1212
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     BF889E8A2C9CD0439BD79BA
alias:          usb:v0BDAp8811d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApC811d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApC82Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApC82Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApC820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApC821d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB82Bd*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
retpoline:      Y
vermagic:       4.4.0-141-generic SMP mod_unload modversions retpoline 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_lps_level:The default LPS level (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_dynamic_agg_enable:int
parm:           rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
parm:           rtw_rx_ampdu_sz_limit_1ss:RX AMPDU size limit for 1SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_2ss:RX AMPDU size limit for 2SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_3ss:RX AMPDU size limit for 3SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_4ss:RX AMPDU size limit for 4SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_vht_enable:int
parm:           rtw_vht_rx_mcs_map:VHT RX MCS map (uint)
parm:           rtw_rf_config:int
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
parm:           rtw_excl_chs:exclusive channel array (array of uint)
parm:           rtw_btcoex_enable:BT co-existence on/off, 0:off, 1:on, 2:by efuse (int)
parm:           rtw_ant_num:Antenna number setting, 0:by efuse (int)
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
parm:           rtw_rx_ampdu_amsdu:int
parm:           rtw_tx_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_single_ant_path:int
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
parm:           rtw_adaptivity_th_l2h_ini:th_l2h_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:th_edcca_hl_diff for Adaptivity (int)
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
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
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
parm:           rtw_en_napi:int
parm:           rtw_en_gro:int
```

---

### Post by dsavlin on 2019-01-18
This totally worked for me. I'd been struggling a few days with this until happening on this post.

I'm on Lubuntu 18.10 with 4.18.0-10-generic (out of the box).

Thanks Chili for spelling it out! I'm not a total newbie but more of an advanced end user, and was working on a computer I built for about $40 not including the $5 junk motherboard my 12 year old bought me at a flea market. I built the computer to show him how to build computers. Pentium 4, 2 GB RAM, and an AGP Radeon card. How old school is that? :)

---

### Post by sdgadsdgdfasd on 2019-05-09
Hey guys,

This seems like a perfect guide for an issue that took me whole day to work out. Unfortunately, my struggle is not quite done - I followed the steps here and got no errors, however I still can't actually connect to any wifi.

My networkctl displays:

```
IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  2 enp1s0           ether              routable    configured
  3 wlx000f00dbbe5f  wlan               no-carrier  configuring
  4 docker0          ether              no-carrier  unmanaged

```
even though lshw -class network seems OK:
```
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 00:25:b3:c8:53:43
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5764m-v3.35 ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:e3000000-e300ffff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlx000f00dbbe5f
       serial: 00:0f:00:db:be:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821cu multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: docker0
       serial: 02:42:87:b4:0c:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes

```
Finally, the relevan lsusb entry is:
```
Bus 002 Device 002: ID 0bda:c811 Realtek Semiconductor Corp.

```
I thought the issue might be in netplan config: so here is my 50-cloud-init.yaml:
```
network:
    ethernets:
        enp1s0:
            addresses:
            - 192.168.0.2/24
            gateway4: 192.168.0.1
            nameservers:
                addresses:
                - 192.168.0.1
    version: 2
    wifis:
        wlx000f00dbbe5f:
            dhcp4: true
            access-points:
                "ak":
                  password: "ak123456"

```

Any ideas what else I can try?

---

### Post by rolfrenne on 2019-07-29
Thank you very much for your helpful post chili, 
it **has been working** for me a long time. **But** with the kernel update to **4.15.0-55-generic-x86-64 it stopped working**, I tried to reinstall (after removing) using your instruction again, but failed. 
Now I'm running 4.15.0-54 again, with no problems.
Hoping either the next kernel will work with rtl8821CU-5.2.5.3 or an other solution will be posted.

---

### Post by chili555 on 2019-07-29
> **rolfrenne said:**
> Thank you very much for your helpful post chili, 
it **has been working** for me a long time. **But** with the kernel update to **4.15.0-55-generic-x86-64 it stopped working**, I tried to reinstall (after removing) using your instruction again, but failed. 
Now I'm running 4.15.0-54 again, with no problems.
Hoping either the next kernel will work with rtl8821CU-5.2.5.3 or an other solution will be posted.Please run and post:```
sudo dkms status
```Usually, when the build fails for a particular kernel version, details can be found in the make.log. I suspect it will be in /var/lib/dkms/rtl8821CU/5.2.5.3/4.15.0-55-generic/x86_64/log/make.log. Please show us:

```
cat  /var/lib/dkms/rtl8821CU/5.2.5.3/4.15.0-55-generic/x86_64/log/make.log

```

---

### Post by rolfrenne on 2019-07-30
Thank you very much for the quick response, but I'm sorry, I've purged 4.15.0-55, and there is no /var/lib/dkms/rtl8821CU/5.2.5.3/4.15.0-55-generic/ any more, but I'll report results with the next kernel update.

---

### Post by bastian2001 on 2019-08-01
I've been struggling to get this to work for a couple of days now and I still do.
lsusb gives:
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046a:b103 Cherry GmbH 
Bus 001 Device 002: ID 0bda:c811 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
So the device is found.

I'm using Linux Mint 19.1 so I apologize if this is the wrong forum. I tried different kernels versions: 5.2.5-050205-generic (x86_64) and 4.20.17-042017-generic (x86_64)

Everything mentioned works except ```
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
```.
I get ```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' KVER=4.20.17-042017-generic..........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821CU: 5.2.5.3 not found
Error! Bad return status for module build on kernel: 4.20.17-042017-generic (x86_64)
Consult /var/lib/dkms/rtl8821CU/5.2.5.3/build/make.log for more information.
```
as the output (same output on both versions except the kernel version listed).

In the make.log file it says ```
cc1: some warnings being treated as errors
scripts/Makefile.build:291: recipe for target '/var/lib/dkms/rtl8821CU/5.2.5.3/build/os_dep/linux/ioctl_cfg80211.o' failed
make[2]: *** [/var/lib/dkms/rtl8821CU/5.2.5.3/build/os_dep/linux/ioctl_cfg80211.o] Error 1
Makefile:1562: recipe for target '_module_/var/lib/dkms/rtl8821CU/5.2.5.3/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8821CU/5.2.5.3/build] Error 2
make[1]: Verzeichnis „/usr/src/linux-headers-4.20.17-042017-generic“ wird verlassen
Makefile:1923: recipe for target 'modules' failed
make: *** [modules] Error 2
```
in addition to a lot of -Werrors.

Any idea?

---

### Post by chili555 on 2019-08-01
> **bastian2001 said:**
> I've been struggling to get this to work for a couple of days now and I still do.
<snip>
in addition to a lot of -Werrors.

Any idea?We don't know much about Mint or the 4.20 kernel here. I recommend that you ask here: [https://forums.linuxmint.com/viewforum.php?f=53](https://forums.linuxmint.com/viewforum.php?f=53)

---

### Post by fuul2 on 2019-08-14
Hi, i have a problem i received this Errors:

```
xx@xx:~/rtl8821CU$ sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' KVER=5.0.0-25-generic.........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821CU: 5.2.5.3 not found
Error! Bad return status for module build on kernel: 5.0.0-25-generic (x86_64)
Consult /var/lib/dkms/rtl8821CU/5.2.5.3/build/make.log for more information.
xx@xx:~/rtl8821CU$ sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' KVER=5.0.0-25-generic.........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821CU: 5.2.5.3 not found
Error! Bad return status for module build on kernel: 5.0.0-25-generic (x86_64)
Consult /var/lib/dkms/rtl8821CU/5.2.5.3/build/make.log for more information.

```

Thx for help

---

### Post by chili555 on 2019-08-14
> **fuul2 said:**
> Hi, i have a problem i received this Errors:

```
xx@xx:~/rtl8821CU$ sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}

<snip>
Consult /var/lib/dkms/rtl8821CU/5.2.5.3/build/make.log for more information.

```

Thx for helpPlease try this method instead: [https://askubuntu.com/questions/1164356/ubuntu-18-04-dlink-dwa171-revc-shows-as-a-memory-stick/1164982#1164982](https://askubuntu.com/questions/1164356/ubuntu-18-04-dlink-dwa171-revc-shows-as-a-memory-stick/1164982#1164982)

---

### Post by fuul2 on 2019-08-15
Yeah thx very much,

```
sudo apt update
sudo apt install build-essential git dkms
git clone https://github.com/brektrou/rtl8821CU.git
cd rtl8821CU
chmod +x dkms-install.sh
sudo ./dkms-install.sh
sudo modprobe 8821cu 
```

Now it works.

---

### Post by pazystamas2 on 2019-10-09
Hello,
How to disable usb wifi adapter auto mount? After boot, nautilus auto mounts wifi as usb disk (with windows drivers) and wifi only works after unmounting disk. I don't want to disable all flash disk mounting, only this wifi adapter. Ubuntu 19.04

---

### Post by chili555 on 2019-10-09
> **pazystamas2 said:**
> Hello,
How to disable usb wifi adapter auto mount? After boot, nautilus auto mounts wifi as usb disk (with windows drivers) and wifi only works after unmounting disk. I don't want to disable all flash disk mounting, only this wifi adapter. Ubuntu 19.04Please start your own new thread and include the results of these terminal commands:```
lsusb
sudo dpkg -s usb-modeswitch | grep Status
```

---


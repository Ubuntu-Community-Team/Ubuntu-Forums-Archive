---
title: "HP 17-bs011dx with Realtek RTL8723DE will not connect to wifi"
date: 2017-07-29
forum: Networking &amp; Wireless
---

### Post by jsquared712 on 2017-07-29
I have a HP 17-bs011dx with what Windows 10 identifies as a Realtek RTL8723DE wifi chip that will not connect to wifi. Any help will be appreciated.

Below is the results of the network script.

```

########## wireless info START ##########

Report from: 29 Jul 2017 18:07 EDT -0400

Booted last: 29 Jul 2017 00:00 EDT -0400

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

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8339]

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b5db Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 154b:005b PNY Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  3 intel_hid,intel_vbtn,hp_wmi
wmi                    16384  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.1.19/24 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 85943sec preferred_lft 85943sec
    inet6 fe80::a519:5d67:a7e:b493/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eno1 proto static metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.19 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       849     1  0 17:58 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c8f7ac3b-91ef-3429-8b59-4ad6de5fcd12
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c8f7ac3b-91ef-3429-8b59-4ad6de5fcd12 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.19/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1501451979
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.19
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::a519:5d67:a7e:b493/64
IP6.GATEWAY:                            

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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N swenc=Y msi=1. With options rtl8723be msi=1 ips=0

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   16.029743] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   16.029744] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   16.089313] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   16.089316] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   16.089319] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   21.749203] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   21.827801] r8169 0000:01:00.0 eno1: link down
[   21.827880] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  100.064643] r8169 0000:01:00.0 eno1: link up
[  100.064657] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############


```

---

### Post by johndough2 on 2017-07-30
Hi

Look here...[https://zach-adams](https://zach-adams)  dot  com    /2014/06/fixing-rtl8723ae-driver-ubuntu-linux/

and he basically says

sudo apt-get install linux-firmware-nonfree
sudo apt-get install wicd wicd-gtk wicd-daemon wicd-cli wicd-curses

and a reboot.

The nonfree part worked for me with Debian, I have a  HP 17-XXXXXX with a Realtek RTL8723BE.

---

### Post by chili555 on 2017-07-30
> **johndough2 said:**
> Hi

Look here...[https://zach-adams](https://zach-adams)  dot  com    /2014/06/fixing-rtl8723ae-driver-ubuntu-linux/

and he basically says

sudo apt-get install linux-firmware-nonfree
sudo apt-get install wicd wicd-gtk wicd-daemon wicd-cli wicd-curses

and a reboot.

The nonfree part worked for me with Debian, I have a  HP 17-XXXXXX with a Realtek RTL8723BE.There is no package linux-firmware-nonfree in Ubuntu 17.04. Also, if his device lacks a proper driver, using Wicd instead of Network Manager will be ineffective.

I am unable to find *any *proper driver for this new rtl8723de device.

---

### Post by praseodym on 2017-07-30
So far, there is only a Windows driver available which you could try with Ndiswrapper:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=62&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=62&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by jsquared712 on 2017-07-30
It doesn't appear as though I can use Ndiswrapper because there is no Windows XP driver.

---

### Post by praseodym on 2017-07-30
Try Win7

---

### Post by jsquared712 on 2017-07-30
I tried the Windows 7 driver using these instructions found here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). Ndiswrapper does not seem to work properly. The device does not appear.

---

### Post by bizyaev-game on 2017-08-16
Same problem here! An HP laptop as well. Do you have any progress troubleshooting?

---

### Post by jsquared712 on 2017-08-16
No luck so far. I either use an external Netgear 6210A USB adapter, or a connected wired. However, I keep hoping a Linux driver for the built-in wifi will be released soon.

---

### Post by praseodym on 2017-08-16
Ok, so far there is no Realtek driver available. Maybe contacting Larry Finger?

[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

---

### Post by jeremy31 on 2017-08-16
Last I heard, Larry was still waiting on Realtek to get him the source code.  I don't know why he just doesn't fix up [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next)

---

### Post by windowsconvert09 on 2017-08-26
Hello Fellow HP-ers!

I am in the same boat. With both Debian 9 and Lubuntu 17.04. Major bummer.

---

### Post by ashoktodawata on 2017-09-03
Same problem is here.. in my HP 15-bs576tx laptop..
RTL8723DE is not detected in Ubuntu 17.04 and no drivers for it..

---

### Post by user_of_ubuntu on 2017-09-06
May as well add me to the list. Same issue as you guys.

---

### Post by Nicolas_Castro on 2017-09-08
Can't believe it! I'm on the waiting list too... cheers

---

### Post by Kanfused on 2017-10-12
I too has a new HP Notebook (HP 15-BS576TX India origin) which has this new wireless module RTL8723DE. If Realtek (wlanfae@realtek.com) provides even a beta Linux driver (source is enough) at this time, we are all grateful.  May be, affected should email to [email]wlanfae@realtek.com[/email] for a beta driver at least!

Anyone tried their luck with Ndiswrapper for this module? Does it compiles?

---

### Post by dFlyer on 2017-10-29
Add me to the list. Unable to connect with RTL8723DE on a 17" HP laptop. According to a link posted above it should be some time within the next 3 months RTL will post a driver for Linux. Very sad as I would like to get rid of windows 10.

Gary

---

### Post by praseodym on 2017-11-06
[https://github.com/lwfinger/rtlwifi_new/issues/270](https://github.com/lwfinger/rtlwifi_new/issues/270)

There is hope for Q4/2017

---

### Post by jeremy31 on 2017-12-22
A chance that a new github might work [https://askubuntu.com/a/988778/300665](https://askubuntu.com/a/988778/300665)
To install the module for the RTL8723DE chipset, first determine your kernel using ```
uname -r
``` if your kernel is lower than 4.11, do
```
sudo apt-get install build-essential dkms
git clone -b 4.10-down https://github.com/smlinux/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot

If you have kernel 4.11 and newer do
```
sudo apt-get install build-essential dkms
git clone https://github.com/smlinux/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot

---

### Post by praseodym on 2017-12-23
Hi Jeremy,

please show
```

modinfo rtl8723de
```if that is the module name

---

### Post by jeremy31 on 2017-12-23
Just tried the dkms and it is broken but the module builds using make
```
ilename:       /home/jeremy/rtl8723de/8723de.ko
version:        v5.1.1.8_21285.20171026
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     386921E2115A11C13BC0F64
alias:          pci:v000010ECd0000D723sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       4.4.0-101-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
parm:           rtw_mp_customer_str:Whether or not to enable customer str support on MP mode (uint)
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
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
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_check_hw_status:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
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
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
parm:           rtw_en_napi:int
parm:           rtw_en_gro:int

```

I found issues in the dkms.conf so I forked the github and made changes
 if your kernel is lower than 4.11, do
```
sudo apt-get install build-essential dkms git
git clone -b 4.10-down https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot

If you have kernel 4.11 and newer do
```
sudo apt-get install build-essential dkms git
git clone https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot

---

### Post by praseodym on 2017-12-23
Awesome!

---

### Post by praseodym on 2017-12-23
Translated the installation for the German Forum here, referring to this post:

[https://forum.ubuntuusers.de/topic/ubuntu-findet-keine-drahtlosnetzwerke/2/#post-8917818](https://forum.ubuntuusers.de/topic/ubuntu-findet-keine-drahtlosnetzwerke/2/#post-8917818)

---

### Post by jeremy31 on 2017-12-23
Fix works [https://github.com/smlinux/rtl8723de/issues/5](https://github.com/smlinux/rtl8723de/issues/5)

---

### Post by chili555 on 2017-12-23
> **jeremy31 said:**
> Fix works [https://github.com/smlinux/rtl8723de/issues/5](https://github.com/smlinux/rtl8723de/issues/5)Awesome! Any time a driver is released for a new device, it's always great to hear from a user that it works correctly.

Great news.

---

### Post by praseodym on 2017-12-23
@ Jeremy, will you still host the driver? Otherwise I will amend the instruction in the German forum.

Another question: 5 GHz seems **not** to work. Can you please confirm?

```
iwlist chan
```

---

### Post by jeremy31 on 2017-12-23
It is 2.4G only, [http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=21&PFid=59&Level=5&Conn=4&ProdID=377](http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=21&PFid=59&Level=5&Conn=4&ProdID=377)
I may not update the driver very often but it can stay there, now that the original is fixed, it is up to posters to decide what they want to post

---

### Post by praseodym on 2017-12-23
P.S.: Is the code from smlinux for both kernel versions, up to and higher than 4.11?

---

### Post by jeremy31 on 2017-12-23
smlinux was the version I forked, it needs the same commands, you could replace jeremyb31 with smlinux in the git clone command and they will work

---

### Post by praseodym on 2017-12-23
So, it is only one installation instruction, not 2 anymore?

---

### Post by jeremy31 on 2017-12-23
It is still 2 procedures, one for 4.11 and higher and another for 4.10 and older. [https://github.com/smlinux/rtl8723de](https://github.com/smlinux/rtl8723de)
They just posted instructions for 4.11 and newer

---

### Post by praseodym on 2017-12-23
Ok, THX

---

### Post by fuzzywuzzybear on 2017-12-27
Hi, uber new linux user here. Just bought my Dad a HP laptop for Christmas and put Mint on it. The wifi didn't work at first, but this was the fix. Thank you soo much Jeremy31!!!!

---

### Post by jeremy31 on 2017-12-27
Glad to hear that fuzzywuzzybear, can you check ```
dmesg | grep rtl
```
To see how many messages are there as I made a recent change that I hope reduces the dmesg log file

---

### Post by fuzzywuzzybear on 2017-12-27
I just wrapped it up...but I can on Saturday when he open its, if no one else has yet. :)

---

### Post by praseodym on 2017-12-28
Hi Jeremy,

so, for > 4.11 kernels the generic installation instruction could be

```
git clone -b [COLOR="#FF0000"]4.11-up[/COLOR] https://github.com/smlinux/rtl8723de.git
```
Maybe the branch changes later?!

Edit: smlinux already changed the instructions there accordingly, also with dkms. All fine

---

### Post by raphlyn on 2017-12-28
Hi, just try for a HP 17-bs083nf... with Kernel 4.4.0-104 ubuntu 16.04

What I did : 

[COLOR=#000000]I followed instructions for kernel lower than 4.11 :
[/COLOR]
[COLOR=#000000]Code:
sudo apt-get install build-essential dkms git
git clone -b 4.10-down [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414[/COLOR]
[COLOR=#000000]
Then reboot[/COLOR]

Ok... Now have the activation function for wifi but can't activate it... nothing happens

**Return for : dmesg | grep rtl**

[    8.710238] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[    8.710244] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   10.325151] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   10.325158] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   10.380942] rtl8723de 0000:02:00.0 wlo1: renamed from wlan0


**Return for : iwlist chan**

lo        no frequency information.

wlo1      13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


eno1      no frequency information.

**return for : lspci**


00:00.0 Host bridge: Intel Corporation Device 2280 (rev 35)
00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 35)
00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 35)
00:13.0 SATA controller: Intel Corporation Device 22a3 (rev 35)
00:14.0 USB controller: Intel Corporation Device 22b5 (rev 35)
00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 35)
00:1b.0 Audio device: Intel Corporation Device 2284 (rev 35)
00:1c.0 PCI bridge: Intel Corporation Device 22c8 (rev 35)
00:1c.2 PCI bridge: Intel Corporation Device 22cc (rev 35)
00:1c.3 PCI bridge: Intel Corporation Device 22ce (rev 35)
00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 35)
00:1f.3 SMBus: Intel Corporation Device 2292 (rev 35)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)



Need some help dudes :)

---

### Post by jeremy31 on 2017-12-28
raphlyn please post results for
```
history | grep rtl8723de
```

---

### Post by raphlyn on 2017-12-28
history | grep rtl8723de



    9  git clone -b 4.10-down [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
   10  sudo dkms add ./rtl8723de
   11  sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
   20  git clone -b 4.10-down [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
   21  sudo dkms add ./rtl8723de
   22  sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
   30  history | grep rtl8723de

---

### Post by jeremy31 on 2017-12-28
Please see the wireless script link in my signature and post results

---

### Post by raphlyn on 2017-12-28
This done...

[https://paste.ubuntu.com/26272793/](https://paste.ubuntu.com/26272793/) 

which give : 

```
#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
#
##############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

SCRIPTDATE="2017-12-05 04:13 +0100"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"

MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|8(188|189|192|723|812)[acde][esu]|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
IFACEMATCHES="(wlan[0-9]|eth[0-9])"
DMESGMATCHES="(firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"

DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"

NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")
DEC2BI=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
DEC2HEX=($(printf "%02x " {0..255}))

export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"

if [ -t 0 ]; then
    DIALOGAPP="terminal"
    DIALOGBREAK=" "
    TERMOUT="yes"
elif [ -x /usr/bin/zenity ]; then
    DIALOGAPP="zenity"
    DIALOGBREAK="\n"
elif [ -x /usr/bin/kdialog ]; then
    DIALOGAPP="kdialog"
    DIALOGBREAK="\n"
else
    exit 1
fi

if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
    GKSUDO="yes"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
    KDESUDO="yes"
    KDESUDOCMT=" needs administrative privileges. Please enter your password."
fi

dialog_info () {
    case $DIALOGAPP in
	terminal)
	    printf "%b\n" "$1"
	    ;;
	zenity)
	    zenity --info --text="$1"
	    ;;
	kdialog)
	    kdialog --msgbox "$1"
	    ;;
    esac
}

dialog_error () {
    case $DIALOGAPP in
	terminal)
	    printf "%b\n" "$1" >&2
	    ;;
	zenity)
	    zenity --error --text="$1"
	    ;;
	kdialog)
	    kdialog --error "$1"
	    ;;
    esac
}

dialog_question () {
    case $DIALOGAPP in
	terminal)
	    local INPUT
	    read -r -p "$1 [Y/n]: " INPUT
	    echo "${INPUT,,}"
	    ;;
	zenity)
	    zenity --question --text="$1" || echo "no"
	    ;;
	kdialog)
	    kdialog --yesno "$1" || echo "no"
	    ;;
    esac
}

ip6-mac () {
    for MAC in "$@"; do
	OCT1BI=${DEC2BI[0x${MAC:0:2}]}
	OCT1BI7=$((${OCT1BI:6:1} - 1))
	OCT1BIM="${OCT1BI:0:6}${OCT1BI7#-}${OCT1BI:7}"
	IP6S+=${IP6S:+$'\n'}"${DEC2HEX[2#$OCT1BIM]}${MAC:3:2}:${MAC:6:2}ff:fe${MAC:9:2}:${MAC:12:2}${MAC:15:2}"
    done
    sed 's/\(^\|:\)0\+\([[:alnum:]]\)/\1\2/g;s/^\([0:]\+\)/\\(::\\|\1\\)/' <<< "$IP6S"
}

exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead.${TERMOUT+\n}"
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
	dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
	exit 1
    }
}
exec 2>&1

printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*/\1/p')
LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Booted last: %s\n\n" "$LASTBOOTDT"
printf "Script from: %s\n" "$SCRIPTDATE"

printf "\n##### release ###########################\n\n"
lsb_release -idrc

printf "\n##### kernel ############################\n\n"
uname -srvmpio
echo
sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline

printf "\n##### desktop ###########################\n\n"
if [ -n "$DESKTOP_SESSION" ]; then
    DESKTOP="$DESKTOP_SESSION"
else
    DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
	DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    printf "\nCould not be determined.\n"
fi

printf "\n##### lspci #############################\n\n"
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

printf "\n##### lsusb #############################\n\n"
lsusb

printf "\n##### PCMCIA card info ##################\n\n"
if [ -x /sbin/pccardctl ]; then
    pccardctl info
else
    echo "'pccardctl' is not installed (package \"pcmciautils\")."
fi

printf "\n##### rfkill ############################\n\n"
rfkill list all

printf "\n##### lsmod #############################\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"

printf "\n##### interfaces ########################\n\n"
sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### ifconfig ##########################\n\n"
if [ -x /sbin/ifconfig ]; then
    IFCONFIG=$(ifconfig -a)
else
    IFCONFIG=$(ip address show)
fi
echo "$IFCONFIG"
IFCONFIG=$(sed -n '1h; 1!H; ${g;s/\n /\\ /g;p}' <<< "$IFCONFIG")
IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p; s#^[0-9]\+: \([^ :]\+\):.* link/ether.*#\1#p' <<< "$IFCONFIG"))
if (( ${#IFACESETH[@]} > 0 )); then
    IFETHMATCHES=${IFACESETH[@]}
    IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
fi

printf "\n##### iwconfig ##########################\n\n"
iwconfig

printf "\n##### route #############################\n\n"
if [ -x /sbin/route ]; then
    route -n
else
    ip route show
fi

printf "\n##### resolv.conf #######################\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### network managers ##################\n\n"
printf "Installed:\n\n"
for NETMGRNR in "${!NETMGRPATHS[@]}"; do
    if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
	NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
    fi
done
printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
NETMGRMATCHES=${NETMGRMATCHES// |/|}
NETMGRMATCHES="(${NETMGRMATCHES#|})"
printf "\nRunning:\n\n"
ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"

printf "\n##### NetworkManager info ###############\n\n"
if [ -x /usr/bin/nm-tool ]; then
    nm-tool
elif [ -x /usr/bin/nmcli ]; then
    nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
    echo
    nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
else
    echo "NetworkManager is not installed (package \"network-manager\")."
fi

printf "\n##### NetworkManager.state ##############\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf ###############\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### NetworkManager profiles ###########\n\n"
if [ -d /etc/NetworkManager/system-connections ]; then
    if [ -n "$SUDO" ]; then
	trap "" 2 3
	NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
	trap 2 3
	if [ "$SUDOSUCCESS" = "yes" ]; then
	    ORIGIFS="$IFS"
	    IFS=$'\n'
	    for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
		NMWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
		NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
		NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
	    done
	    IFS="$ORIGIFS"
	    sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
	else
	    printf "\nAcquisition of admin privileges failed.\n"
	fi
    else
	echo "No way to acquire admin privileges found."
    fi
else
    echo "No NetworkManager profiles found."
fi

printf "\n##### Netplan config ####################\n\n"
for NPLANFILE in $(find /{lib,etc,run}/netplan -name "*.yaml" 2> /dev/null | sort); do
    NPLANFLCNT=$(egrep -v '^(#|$)' $NPLANFILE)
    if [ -n "$NPLANFLCNT" ]; then
	printf "[%s]\n%s\n\n" "$NPLANFILE" "$NPLANFLCNT"
    fi
done

printf "\n##### iw reg get ########################\n\n"
if [ -x /sbin/iw ]; then
    if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
	REGION=$(cat /etc/timezone)
	printf "Region: %s (based on set time zone)\n\n" "$REGION"
    fi
    echo "$IWREGGET"
else
    echo "'iw' is not installed (package \"iw\")."
fi

printf "\n##### iwlist channels ###################\n\n"
if [ -x /sbin/iwlist ]; then
    iwlist chan
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi

printf "\n##### iwlist scan #######################\n\n"
if [ -x /sbin/iwlist ]; then
    if [ -n "$SUDO" ]; then
	trap "" 2 3
	IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
	trap 2 3
	if [ "$SUDOSUCCESS" = "yes" ]; then
	    if [[ $IWLISTSCAN = *Frequency:* ]]; then
		printf "Channel occupancy:\n\n"
		grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
		echo
	    fi
	    grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
	else
	    printf "\nAcquisition of admin privileges failed.\n"
	fi
    else
	echo "No way to acquire admin privileges found."
    fi
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi

printf "\n##### module infos ######################\n\n"
MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done

printf "\n##### module parameters #################\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
	MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
	printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done

printf "\n##### /etc/modules ######################\n\n"
grep -v '^#' /etc/modules

printf "\n##### modprobe options ##################\n\n"
for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort); do
    MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
    if [ -n "$MODPROBEOPTS" ]; then
	printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
    fi
done

printf "\n##### rc.local ##########################\n\n"
grep -v '^#' /etc/rc.local

printf "\n##### pm-utils ##########################\n\n"
for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
    PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
    if [ -n "$PMUTFLCONT" ]; then
	PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
	printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
    fi
done

printf "\n##### udev rules ########################\n\n"
for UDEVRLFILE in $(find /etc/udev/rules.d -name "*net*.rules" | sort); do
    UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
    if [ -n "$UDEVRULES" ]; then
	printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
    fi
done

printf "\n##### dmesg #############################\n\n"
dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$IFACEMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'

printf "\n########## wireless info END ############\n\n"

exec 2>&4 4>&-
exec 1>&3 3>&-

##### MAC address masking #####

RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'

ORIGIFS="$IFS"
IFS=$'\n'

IFACESIDS=($(sed -n "/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/ {/\(00:\)\{5\}00/! {s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1'/p; s/^[0-9]\+: \([^ :]\+\):.*/'\1'/p}}" <<< "$IFCONFIG"))
IFACESMACS=($(sed -n '/\(00:\)\{5\}00/! s#.*\(HWaddr\|link/[^ ]\+\) \(\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}\).*#\2#p' <<< "$IFCONFIG"))
IFACESIP6S=($(ip6-mac "${IFACESMACS[@]}"))

WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h; /^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$IWLISTSCAN"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$IWLISTSCAN"))
WLAPSIWLIP6S=($(ip6-mac "${WLAPSIWLMACS[@]}"))

WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{print "'\''" $1 "'\''"}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))
WLAPSNMIP6S=($(ip6-mac "${WLAPSNMMACS[@]}"))

IFS="$ORIGIFS"

for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]} [IF$(($IFACENR + 1))]>;I;"
    MACMASKSED+=" /${IFACESIP6S[$IFACENR]}/ s;${IFACESIP6S[$IFACENR]/#\\(::/\(};<IP6 ${IFACESIDS[$IFACENR]} [IF$(($IFACENR + 1))]>;I;"
    IFACEMACC=${IFACESMACS[$IFACENR]//:/}
    if [[ ${IFACESIDS[$IFACENR],,} =~ ${IFACEMACC,,} ]]; then
	MACMASKSED+="s;\(${IFACESIDS[$IFACENR]:1:3}\)$IFACEMACC;\1<IF from MAC [IF$(($IFACENR + 1))]>;Ig;"
    fi
done

for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]}>;I;"
    MACMASKSED+=" /${WLAPSIWLIP6S[$WLAPIWLNR]}/ s;${WLAPSIWLIP6S[$WLAPIWLNR]/#\\(::/\(};<IP6 ${WLAPSIWLIDS[$WLAPIWLNR]}>;I;"
done

for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]} [AN$(($WLAPNMNR + 1))]>;I;"
    MACMASKSED+=" /${WLAPSNMIP6S[$WLAPNMNR]}/ s;${WLAPSNMIP6S[$WLAPNMNR]/#\\(::/\(};<IP6 ${WLAPSNMIDS[$WLAPNMNR]} [AN$(($WLAPNMNR + 1))]>;I;"
done

sed "$MACMASKSED /\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"

##### The End #####

dialog_info "${TERMOUT+\n}Results saved in \"$OUTPUTDIR/$FILEBASE.txt\".${TERMOUT+\n}"

if (( $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") > 19968 )); then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" -C "$OUTPUTDIR" "$FILEBASE.txt" && \
	dialog_info "Results also archived in \"$OUTPUTDIR/$FILEBASE.tar.gz\",${DIALOGBREAK}as they exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums.${TERMOUT+\n}" || \
	dialog_error "Results exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums, but archive could not be created.${TERMOUT+\n}"
fi

if [ -x /usr/bin/pastebinit ] && ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com > /dev/null 2>&1; then
    PASTEBIN=$(dialog_question "Do you also want to post them${DIALOGBREAK}to your default 'pastebinit' provider?")
    if [[ ! $PASTEBIN =~ ^no?$ ]]; then
	PASTERESULT=$(pastebinit -i "$OUTPUTDIR/$FILEBASE.txt" -f text 2>&1) && PASTESUCCESS="yes"
	if [ "$PASTESUCCESS" = "yes" ]; then
	    dialog_info "${TERMOUT+\n}Pastebin successful:\n\n${PASTERESULT}${TERMOUT+\n}"
	else
	    if [ -n "$PASTERESULT" ]; then
		dialog_error "${TERMOUT+\n}Pastebin failed, error message is:\n\n${PASTERESULT}${TERMOUT+\n}"
	    else
		dialog_error "${TERMOUT+\n}Pastebin failed, no error message given.${TERMOUT+\n}"
	    fi
	fi
    else
	echo
    fi
fi
```

---

### Post by jeremy31 on 2017-12-28
That is the script, the results are in wireless-info.**txt**

---

### Post by raphlyn on 2017-12-28
That is the script... lol... I'm bad ^^

But had this link Jeremy :) [https://paste.ubuntu.com/26272793/](https://paste.ubuntu.com/26272793/)

Acer-Wireless still soft blocked ??? 

2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

**[COLOR=#000000]wireless-info.[/COLOR]****[B]txt**
[/B]
```
########## wireless info START ##########


Report from: 28 Dec 2017 18:07 CET +0100


Booted last: 28 Dec 2017 00:00 CET +0100


Script from: 05 Dec 2017 03:13 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-104-generic #127-Ubuntu SMP Mon Dec 11 12:16:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company Device [103c:8319]


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8342]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 04f2:b5db Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
acer_wmi               20480  0
sparse_keymap          16384  2 acer_wmi,hp_wmi
8723de               1413120  0
cfg80211              565248  1 8723de
video                  40960  2 i915,acer_wmi
wmi                    20480  2 acer_wmi,hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b450:eb9e:9e6e:efbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1526293 (1.5 MB)  TX bytes:290503 (290.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:25928 (25.9 KB)  TX bytes:25928 (25.9 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       745     1  0 17:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Connexion filaire 1
GENERAL.CON-UUID:                       68eb68b9-17ac-3175-b858-8e145a88c265
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   68eb68b9-17ac-3175-b858-8e145a88c265 | Connexion filaire 1
IP4.ADDRESS[1]:                         192.168.1.26/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.26
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1514566560
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:62:38:32:36:36:43:5:f:41:5a:31:34:32:33:32:32:36:39:36:36:35:36:33:6:f:4c:69:76:65:62:6f:78:20:46:54:54:48:20:76:32
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::b450:eb9e:9e6e:efbd/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         rtl8723de
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlo1
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
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
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


[[/etc/NetworkManager/system-connections/Connexion Wi-Fi 1]] (600 root)
[connection] id=Connexion Wi-Fi 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Livebox-7eb8
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


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


wlo1      13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)


wlo1      Scan completed :
          Cell 01 - Address: <MAC 'Livebox-7EB8' [AC1]>
                    ESSID:"Livebox-7EB8"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=70/100  
                    Extra:fm=0003


##### module infos ######################


modinfo: ERROR: Module 8723de not found.
[8723de]


[cfg80211]
filename:       /lib/modules/4.4.0-104-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D2A8E57424453F0D1BE1DBE
depends:        
intree:         Y
vermagic:       4.4.0-104-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[8723de]
if2name: wlan%d
ifname: wlan%d
rtw_adaptivity_dc_backoff: 2
rtw_adaptivity_dml: 0
rtw_adaptivity_en: 0
rtw_adaptivity_mode: 0
rtw_adaptivity_th_edcca_hl_diff: 0
rtw_adaptivity_th_l2h_ini: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_amplifier_type_2g: 0
rtw_amplifier_type_5g: 0
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_ant_num: 0
rtw_btcoex_enable: 2
rtw_busy_thresh: 40
rtw_bw_mode: 33
rtw_channel: 1
rtw_channel_plan: 99
rtw_check_hw_status: 0
rtw_chip_version: 0
rtw_decrypt_phy_file: 0
rtw_drv_ant_band_switch: 1
rtw_drv_log_level: 4
rtw_en_gro: 1
rtw_en_napi: 1
rtw_enusbss: 0
rtw_FileMaskEfuse: 0
rtw_force_igi_lb: 0
rtw_full_ch_in_p2p_handshake: 0
rtw_GLNA_type: 0
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 0
rtw_initmac: (null)
rtw_ips_mode: 0
rtw_lbkmode: 0
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mp_customer_str: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_OffEfuseMask: 0
rtw_pll_ref_clk_sel: 15
rtw_power_mgnt: 0
rtw_powertracking_type: 64
rtw_pwrtrim_enable: 0
rtw_qos_opt_enable: 0
rtw_rf_config: 15
rtw_RFE_type: 64
rtw_rfintfs: 2
rtw_rxgain_offset_2g: 0
rtw_rxgain_offset_5gh: 0
rtw_rxgain_offset_5gl: 0
rtw_rxgain_offset_5gm: 0
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_special_rf_path: 0
rtw_switch_usb_mode: 0
rtw_TxBBSwing_2G: 255
rtw_TxBBSwing_5G: 255
rtw_tx_bw_mode: 33
rtw_tx_pwr_by_rate: 2
rtw_tx_pwr_lmt_enable: 2
rtw_usb_rxagg_mode: 2
rtw_vcs_type: 1
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


##### dmesg #############################


[   10.783219] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   10.783227] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   10.810918] rtl8723de 0000:02:00.0 wlo1: renamed from wlan0
[   22.293624] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   22.304678] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   22.406348] r8169 0000:03:00.0 eno1: link down (repeated 2 times)
[   22.407633] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   24.204442] r8169 0000:03:00.0 eno1: link up
[   24.204468] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   32.558484] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 6 times)


########## wireless info END ############
```

---

### Post by chili555 on 2017-12-28
Sorry, Jeremy, I just can't stop myself!> Acer-Wireless still soft blocked ??? 

2: acer-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: noPlease note:> 
hp_wmi                 16384  0
acer_wmi               20480  0
sparse_keymap          16384  2 acer_wmi,hp_wmi
Your laptop is not BOTH an Acer and an HP, is it? Let's blacklist the offending module:```
sudo -i
modprobe -r acer-wmi
echo "blacklist acer-wmi"  >>  /etc/modprobe.d/blacklist.conf
rfkill unblock all
exit
```Is your wireless working now? It may take a reboot.

---

### Post by jeremy31 on 2017-12-28
Nice catch chili555.
I do want a new wireless script after a reboot as I made a change to this to see if it will stop spamming the logs

---

### Post by raphlyn on 2017-12-28
Hmm...  I just can't stop myself too...  

but yes... seems my [COLOR=#000000]laptop is BOTH an Acer and an HP[/COLOR] :)

modprobe -r acer-wmi returns an invalid option 'w'

---

### Post by jeremy31 on 2017-12-28
raphlyn
chili555 is correct on this one.  I have complete confidence that it will work

---

### Post by raphlyn on 2017-12-28
Not sure... I tried something like this without success.. But let's have fun ^^

modprobe -r acer-wmi returns me invalid option 'w'

---

### Post by chili555 on 2017-12-28
Please try again:```
exit
sudo modprobe -r acer-wmi
```Post the exact error or warnings.

---

### Post by raphlyn on 2017-12-28
I agree the acer hp mixx, lol ??? What's this ??? 

But for sure, my HP rfkill returns : 

2 : acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

Exact error : Tried and retried... 

modprobe: invalid option -- 'w'

---

### Post by jeremy31 on 2017-12-28
Try ```
echo "blacklist acer-wmi" | sudo tee /etc/blacklist-acer.conf
```
Reboot

---

### Post by chili555 on 2017-12-28
> **jeremy31 said:**
> Try ```
echo "blacklist acer-wmi" | sudo tee /etc/blacklist-acer.conf
```
RebootNot /etc/[COLOR="#FF0000"]modprobe.d[/COLOR]/blacklist-acer.conf??

---

### Post by jeremy31 on 2017-12-28
That is better

---

### Post by raphlyn on 2017-12-29
Awesome... You did it !

I just have to say I had to reboot three times to make it works... but it works ![COLOR=#000000]
[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by alexbuechele on 2017-12-29
**disregard this post, i figured it out**

I can't get the smlinux driver to work, either :(

my wireless script results:
[https://paste.ubuntu.com/26281199/](https://paste.ubuntu.com/26281199/)

wireless icon doesn't appear in taskbar, but i can open network settings. i see networks but can't connect to them. clicking connect does nothing, clicking settings does nothing

---

### Post by praseodym on 2017-12-29
Why using kernel 4.14? Try the original 4.10 instead with 16.04. Then, you need the other branch of that driver. Uninstall this one first

---

### Post by alexbuechele on 2017-12-29
I have previously tried 4.10, 4.11 and 4.13 (probably a clumsy approach) 

while waiting for a response i tried purging and reinstalling network-manager and network-manager-gnome. after a reboot my wifi works now :) 

now another problem has popped up, but i'll work on it a bit longer alone before i ask for help. i think i jumped the gun posting here :)

---

### Post by carboba on 2017-12-31
I had the same issue but it solved now , follow this [https://github.com/lwfinger/rtlwifi_new/issues/270](https://github.com/lwfinger/rtlwifi_new/issues/270)
it worked for me , I upgrade my linux kernel to Linux 4.14.10-041410-generic and I followed the process

---

### Post by jeremy31 on 2017-12-31
Why use a 4.14 kernel when [https://github.com/smlinux/rtl8723de/tree/4.10-down](https://github.com/smlinux/rtl8723de/tree/4.10-down) works with 4.4 and others

---

### Post by carboba on 2017-12-31
@jeremy31, Thanks , I didn't see that

---

### Post by jeremy31 on 2018-01-06
Larry Finger now has a fix, you should remove the module from dkms if you installed from my github or smlinux's
```
dkms uninstall rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all
depmod -a
```
Reboot and then to install from rtlwifi-new
```
sudo apt-get install git build-essential dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot

---

### Post by praseodym on 2018-01-07
Thanks

---

### Post by jlk.fl on 2018-01-11
Hello,

I am currently on Ubuntu 17.10 with the RTL8723de and I installed as you said, plus I did the routine in the Basic Wireless Issue topic.

Ubuntu says "No Wifi adapter found" and doesn't suggest me any network, any help ? :)

Thanks !

---

### Post by praseodym on 2018-01-11
Please run

```
sudo modprobe -v rtl8723de
dmesg | grep rtl
```
Maybe deactivating SecureBoot?

---

### Post by jlk.fl on 2018-01-12
So I deactivated secure boot and this is what modprobe returns :
```
insmod /lib/modules/4.13.0-25-generic/updates/dkms/rtl8723de.ko 
modprobe: ERROR: could not insert 'rtl8723de': Unknown symbol in module, or unknown parameter (see dmesg)



```
and the grep :
```

[    7.529386] rtlwifi: loading out-of-tree module taints kernel.
[    7.529500] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    7.546839] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
[    7.652220] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[    7.652222] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    7.654364] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    7.654369] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   81.679065] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
[  135.329822] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
[  250.181881] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
[  363.540549] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)



```
Thank you for the answer ;)



[HR][/HR]

---

### Post by jeremy31 on 2018-01-12
I think that issue was fixed
```
sudo dkms uninstall rtlwifi-new/0.6
sudo dkms remove rtlwifi-new/0.6 --all
```
```
cd rtlwifi_new
git pull
```
Hopefully this shows new files and changed files being downloaded
```
cd
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot

---

### Post by jlk.fl on 2018-01-13
Still "No wifi adapter found" 

Here are the results of each command : 

**sudo uninstall** :
```
-------- Uninstall Beginning --------
Module:  rtlwifi-new
Version: 0.6
Kernel:  4.13.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

rtl_pci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl_usb.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtlwifi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


btcoexist.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


halmac.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


phydm_mod.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8188ee.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8192c-common.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8192ce.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8192cu.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8192de.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8192ee.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8192se.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8723ae.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8723be.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8723de.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8723-common.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8821ae.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rtl8822be.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.
```

**sudo remove** :
```

-------- Uninstall Beginning --------
Module:  rtlwifi-new
Version: 0.6
Kernel:  4.13.0-25-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.6
completely from the DKMS tree.
------------------------------
Done.
```

**git pull** :

```
Already up-to-date.
```

**dkms add** : 

```
Already up-to-date.
```

**dkms install** : 

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...(bad exit status: 2)
make -j2 KERNELRELEASE=4.13.0-25-generic -C /lib/modules/4.13.0-25-generic/build M=/var/lib/dkms/rtlwifi-new/0.6/build......................................
cleaning build area...(bad exit status: 2)

DKMS: build completed.

rtl_pci.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl_usb.ko:
Running module version sanity check.
Error! Module version A75DE26919101CBBB95F197 for rtl_usb.ko
is not newer than what is already found in kernel 4.13.0-25-generic (F27BFC8AFE2C9C9AD2C27D2).
You may override by specifying --force.

rtlwifi.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

btcoexist.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

halmac.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

phydm_mod.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8188ee.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8192c-common.ko:
Running module version sanity check.
Error! Module version 819074F315681EC1A9E6161 for rtl8192c-common.ko
is not newer than what is already found in kernel 4.13.0-25-generic (F6DAD9E9BD83515DCFF3382).
You may override by specifying --force.

rtl8192ce.ko:
Running module version sanity check.
Error! Module version 5A96102E4D95F4187C98FE1 for rtl8192ce.ko
is not newer than what is already found in kernel 4.13.0-25-generic (652BC11F71608AFD57EF5CA).
You may override by specifying --force.

rtl8192cu.ko:
Running module version sanity check.
Error! Module version 947E63A8FA734B54AECAF91 for rtl8192cu.ko
is not newer than what is already found in kernel 4.13.0-25-generic (F728A58B6CE5C24C2D80E37).
You may override by specifying --force.

rtl8192de.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8192ee.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8192se.ko:
Running module version sanity check.
Error! Module version B617170E71A9E70B1ABE840 for rtl8192se.ko
is not newer than what is already found in kernel 4.13.0-25-generic (E0C11CAE0E9A0C78868D17B).
You may override by specifying --force.

rtl8723ae.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8723be.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8723de.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8723-common.ko:
Running module version sanity check.
Error! Module version 5AAF25B4699EF07310A021A for rtl8723-common.ko
is not newer than what is already found in kernel 4.13.0-25-generic (D7EA94BD5D056F91DA3C87E).
You may override by specifying --force.

rtl8821ae.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

rtl8822be.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

depmod...

DKMS: install completed.
```

**dmesg | grep rtl** :

```
dmesg | grep rtl
[    7.832933] rtlwifi: loading out-of-tree module taints kernel.
[    7.833077] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    7.870363] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
[    7.948851] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[    7.948854] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    7.951412] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    7.951416] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[  176.156971] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
[  231.849722] rtl8723de: Unknown symbol rtl8723de_firmware_selfreset (err 0)
```

---

### Post by jeremy31 on 2018-01-13
I think it is time to give up on that source code
```
sudo dkms uninstall rtlwifi-new/0.6
sudo dkms remove rtlwifi-new/0.6 --all
```

Then install another source
```
cd
sudo apt-get install build-essential git dkms
git clone https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Reboot

---

### Post by eoxs540 on 2018-01-14
Hi,
I am using Ubutu 16.04 64 bits with rtl8723 adapter. Unfortunately, like other people the adapter was not recognized by default in Ubuntu
I am trying to install your driver with your procedure:
cd
sudo apt-get install build-essential git dkms
git clone [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

I obtain this message in the terminalsudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' all KVER=4.10.0-42-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8723de: 5.1.1.8_21285.20171026_COEX20170111-1414 not found
Error! Bad return status for module build on kernel: 4.10.0-42-generic (x86_64)
Consult /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log for more information.

and the log file is here: 

DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 4.10.0-42-generic (x86_64)
dimanche 14 janvier 2018, 14:01:14 (UTC+0100)
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-42-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build  modules
make[1] : on entre dans le répertoire « /usr/src/linux-headers-4.10.0-42-generic »
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:41:33: fatal error: linux/sched/signal.h: Aucun fichier ou dossier de ce type
compilation terminated.
scripts/Makefile.build:294 : la recette pour la cible « /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o » a échouée
make[2]: *** [/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o] Erreur 1
Makefile:1524 : la recette pour la cible « _module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build » a échouée
make[1]: *** [_module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build] Erreur 2
make[1] : on quitte le répertoire « /usr/src/linux-headers-4.10.0-42-generic »
Makefile:1884 : la recette pour la cible « modules » a échouée
make: *** [modules] Erreur 2

What is wrong in my installation ?
Thanks for the help
Olivier

---

### Post by jeremy31 on 2018-01-14
> **eoxs540 said:**
> Hi,
I am using Ubutu 16.04 64 bits with rtl8723 adapter. Unfortunately, like other people the adapter was not recognized by default in Ubuntu
I am trying to install your driver with your procedure:
cd
sudo apt-get install build-essential git dkms
git clone [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

I obtain this message in the terminalsudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' all KVER=4.10.0-42-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8723de: 5.1.1.8_21285.20171026_COEX20170111-1414 not found
Error! Bad return status for module build on kernel: 4.10.0-42-generic (x86_64)
Consult /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log for more information.

and the log file is here: 

DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 4.10.0-42-generic (x86_64)
dimanche 14 janvier 2018, 14:01:14 (UTC+0100)
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-42-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build  modules
make[1] : on entre dans le répertoire « /usr/src/linux-headers-4.10.0-42-generic »
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:41:33: fatal error: linux/sched/signal.h: Aucun fichier ou dossier de ce type
compilation terminated.
scripts/Makefile.build:294 : la recette pour la cible « /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o » a échouée
make[2]: *** [/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o] Erreur 1
Makefile:1524 : la recette pour la cible « _module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build » a échouée
make[1]: *** [_module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build] Erreur 2
make[1] : on quitte le répertoire « /usr/src/linux-headers-4.10.0-42-generic »
Makefile:1884 : la recette pour la cible « modules » a échouée
make: *** [modules] Erreur 2

What is wrong in my installation ?
Thanks for the help
Olivier

Olivier, you need a different branch for your kernel, first remove the folder
```
rm -rf rtl8723de
```
Then get the right branch and compile
```
git clone -b 4.10-down https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot

---

### Post by eoxs540 on 2018-01-14
Hi again,
You give me the link to the same branch ????
Error in terminal
~$ sudo dkms add ./rtl8723deError! DKMS tree already contains: rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414
You cannot add the same module/version combo more than once.

---

### Post by jeremy31 on 2018-01-14
Try this and then use the dkms commands from above
```
sudo dkms uninstall rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
sudo dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all
```

---

### Post by edy14 on 2018-01-14
Hi,
I am using Ubuntu 17.10 64 bits with rtl8723 adapter on hp 17-bs075nf with Windows10 dualboot. Unfortunately, like  other people the adapter was not recognized by default in Ubuntu
I am trying to install your driver with your procedure:
```
cd
sudo apt-get install build-essential git dkms
git clone [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot.
Adapter still not seen by ubuntu.
The odd thing is, while installing Ubuntu from a usb-stick, it was able to connect to the WiFi. But on reboot, no adapter found...
I tried:
```
sudo modprobe -v rtl8723de
insmod /lib/modules/4.13.0-25-generic/updates/dkms/rtl8723de.ko 
modprobe: ERROR: could not insert 'rtl8723de': Required key not available
```
```
dmesg | grep rtl
[   11.170898] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   11.170902] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   11.172389] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   11.172396] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin

```
Did I miss something? Thanks for your help

---

### Post by jeremy31 on 2018-01-14
edy14, Go into UEFI/BIOS settings and disable secure boot, then the driver should work

---

### Post by eoxs540 on 2018-01-14
Hi Jeremy,
Following your info (uninstall, remove, reinstall)
Not yet working.
Testing:

sudo modprobe -v rtl8723de
insmod /lib/modules/4.10.0-42-generic/updates/dkms/rtl8723de.ko 
modprobe: ERROR: could not insert 'rtl8723de': Required key not available

dmesg | grep rtl
[   18.669046] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   18.669048] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   18.683851] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   18.683855] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   18.683859] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   19.845823] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   19.845825] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   19.845843] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   19.845844] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_config.bin
[   19.845848] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin


After this, in in the bios disable secure boot and reboot again and gave the same message.
Adapter still not working ...
Any idea ?
Thx,
Olivier

---

### Post by eoxs540 on 2018-01-14
Ok it works now !!!!
Changes in the BIOS was not saved !!!
Many thanks for your help.
Olivier

---

### Post by edy14 on 2018-01-14
> **edy14 said:**
> Hi,
I am using Ubuntu 17.10 64 bits with rtl8723 adapter on hp 17-bs075nf with Windows10 dualboot. Unfortunately, like  other people the adapter was not recognized by default in Ubuntu
I am trying to install your driver with your procedure:
```
cd
sudo apt-get install build-essential git dkms
git clone [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Then reboot.
Adapter still not seen by ubuntu.
The odd thing is, while installing Ubuntu from a usb-stick, it was able to connect to the WiFi. But on reboot, no adapter found...
Did I miss something? Thanks for your help

Thank you! I missed the step: 
> Go into UEFI/BIOS settings and disable secure boot, then the driver should work
It works! Thank you so much!

---

### Post by praseodym on 2018-01-16
Found one issue in the German forum, firmware was not available. After the installation process run

```
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```

Antenna selection via

```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf 
```

---

### Post by jeremy31 on 2018-01-16
Larry Finger may have updated his github source for the firnware, strange that nobody had firmware or antenna select issues with the smlinux code from github

---

### Post by nidou01 on 2018-01-21
Hi guys
I'm in the same case as @edy14, I have the same laptop and having the same config  Ubuntu 17.10 64 bits- hp 17-bs075nf 
I started by disabling the secure boot 
I ran those steps :

```
sudo apt-get install build-essential git dkms
git clone [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```

but at the final command I got a nice:

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' all KVER=4.13.0-26-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8723de: 5.1.1.8_21285.20171026_COEX20170111-1414 not found
Error! Bad return status for module build on kernel: 4.13.0-26-generic (x86_64)
Consult /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log for more information.


```
And 
```

***cat /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log***
DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 4.13.0-26-generic (x86_64)
Son Jan 21 12:32:08 CET 2018
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-26-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build  modules
make[1]: Entering directory '/lib/modules/4.13.0-26-generic/build'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target 'Makefile'.  Stop.
make[1]: Leaving directory '/lib/modules/4.13.0-26-generic/build'
Makefile:1884: recipe for target 'modules' failed
make: *** [modules] Error 2



```

And indeed there no directory '/lib/modules/4.13.0-26-generic/build' 

Here are some other details that may help :


```
_**uname -r**_
4.13.0-26-generic
```

```
*** cd /usr/src/***
linux-headers-4.13.0-25/                            linux-headers-4.13.0-25-generic/
```
There is no 'linux-headers-4.13.0-26-generic/' ? :confused:

Can anyone help me please 

Thanks !

---

### Post by jeremy31 on 2018-01-21
Try ```
sudo apt-get install linux-headers-4.13.0-26-generic
```
Then see if you can get the other command to work

---

### Post by nidou01 on 2018-01-21
Hi Jeremy,
Thanks for you reply

Unfortunately
```
sudo apt-get install linux-headers-4.13.0-26-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-4.13.0-26-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-4.13.0-26-generic' has no installation candidate


``` 

But instead of installing *-26 headers I downgraded my kernel to 4.13.0-25-generic

by removing linux-image-4.13.0-26-generic using :
 
```
sudo apt remove linux-image-4.13.0-26-generic 


```
then [I][B]reboot
[/B][/I]
and it works !

Thank you everybody ! :guitar:

---

### Post by kr4 on 2018-01-23
Hi, I followed the steps suggested and installed the driver from Jeremmy's git and at first glance it seems to be working fine. However whenever i try to connect to my wifi network it stays at "Wi-Fi Connecting", then it drops and does the same again until it gets tired. Trying things all around the terminal i managed to make it work for a few seconds until i had the bright idea to reboot. I have no idea of what i did for it to get working... or maybe it was just an illusion :o

in anycase... for now I am using an usb adapter to search the forums but that is not always convenient...

I ran the wireless-info script if you would be so kind to take a look.
[ATTACH]278297[/ATTACH]

thanks in advance.

---

### Post by chili555 on 2018-01-24
> **kr4 said:**
> Hi, I followed the steps suggested and installed the driver from Jeremmy's git and at first glance it seems to be working fine. However whenever i try to connect to my wifi network it stays at "Wi-Fi Connecting", then it drops and does the same again until it gets tired. Trying things all around the terminal i managed to make it work for a few seconds until i had the bright idea to reboot. I have no idea of what i did for it to get working... or maybe it was just an illusion :o

in anycase... for now I am using an usb adapter to search the forums but that is not always convenient...

I ran the wireless-info script if you would be so kind to take a look.
[ATTACH]278297[/ATTACH]

thanks in advance.We see:> TURBONETT_10088A  <MAC 'TURBONETT_10088A' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WEP       yes     * 
WEP is terribly outdated and terribly insecure. I have no doubt that the driver you installed wasn't written with much care for WEP.

[https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy) Please see: [B][I]Weak security
[/I][/B].

I suggest that you change the router to WPA2-CCMP, sometimes called AES.

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Finally, detach the USB, reboot and try to connect. Any improvement?

---

### Post by kr4 on 2018-01-24
> WEP is terribly outdated and terribly insecure. I have no doubt that the  driver you installed wasn't written with much care for WEP.

[https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy) Please see: ***Weak security***
I agree, but sadly there is not much i can do about that. However i tried connecting to my phone's hotspot which has WPA2 and i obtained the same results.

> Change the last line to read:

    ```
REGDOMAIN=IS 
```
done with my country code but no improvements yet.

I went back and took a look at the *history *command. I basically did
```

sudo iwconfig wlo1 essid TURBONETT_10088A key myWEPKey
sudo ifconfig wlo1 down
sudo ifconfig wlo1 up 

```
**repeatedly**, and then, with a few ifconfig up/down in between :oops:
```

sudo usermod -a -G netdev user
sudo rfkill unblock wifi
sudo lshw -class network
sudo iwconfig wlo1 essid TURBONETT_10088A key myWepKey
ping google.com
sudo dhclient wlo1
ifconfig
ping google.com

```
At that point it starts to ping google, i get exited and reboot...

I am not sure if that helps. i try it now and it doesn't do much, so maybe it was just beginners luck.

---

### Post by chili555 on 2018-01-24
> I agree, but sadly there is not much i can do about thatWhy is that? Is it your landlord's router or what? If it is yours, you can certainly change it.> sudo iwconfig wlo1 essid TURBONETT_10088A key e75f7c0bb7
ping google.com
sudo dhclient wlo1
ifconfig
ping google.comWhy are you doing this all manually? Isn't Network Manager running? Generally, manual methods are in conflict with NM and won't work well, if at all.

---

### Post by kr4 on 2018-01-28
> **chili555 said:**
> Why is that? Is it your landlord's router or what? If it is yours, you can certainly change it.Why are you 

Yep, not my router.

> **chili555 said:**
> 
doing this all manually? Isn't Network Manager running? Generally, manual methods are in conflict with NM and won't work well, if at all.
With the problem that im getting i was willing to try anyting to make it work.

---

### Post by chili555 on 2018-01-28
If you reboot with the probably conflicting USB detached, does it do the same thing, try but fail to connect?

What is the result of this exact sequence of commands?```
sudo iwconfig wlo1 essid TURBONETT_10088A key e75f7c0bb7
sudo dhclient wlo1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Again, with the USB and ethernet, if any, detached.

---

### Post by kr4 on 2018-01-28
> **chili555 said:**
> If you reboot with the probably conflicting USB detached, does it do the same thing, try but fail to connect?

What is the result of this exact sequence of commands?```
sudo iwconfig wlo1 essid TURBONETT_10088A key aaaaaaa
sudo dhclient wlo1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Again, with the USB and ethernet, if any, detached.

iwconfig does not show any results and the dhclient just freezes until it gives up or I crtl+c... In fact iwconfig is not doing anything. 
If i do 
```
sudo iwconfig wlo1 essid TURBONETT_10088A key aaaaaaa
iwconfig
```
it shows as if it didn't even try.```
wlo1      unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2018-01-28
> the dhclient just freezes until it gives up or I crtl+c.Let's amend the sequence just a bit:```
[COLOR="#FF0000"]sudo service network-manager stop[/COLOR]
sudo iwconfig wlo1 essid TURBONETT_10088A key e75f7c0bb7
sudo dhclient [COLOR="#FF0000"]-v[/COLOR] wlo1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Does the USB connect and work well, WEP notwithstanding?

---

### Post by kr4 on 2018-01-28
> **chili555 said:**
> Let's amend the sequence just a bit:```
[COLOR=#FF0000]sudo service network-manager stop[/COLOR]

there is no service network-manager...

[CODE]Failed to stop netowrk-manager.service: Unit netowrk-manager.service not loaded.

sudo service --status-all
 [ + ]  acpid
 [ - ]  alsa-utils
 [ - ]  anacron
 [ + ]  apparmor
 [ + ]  apport
 [ + ]  avahi-daemon
 [ + ]  bluetooth
 [ - ]  console-setup.sh
 [ + ]  cron
 [ + ]  cups
 [ + ]  cups-browsed
 [ + ]  dbus
 [ - ]  dns-clean
 [ + ]  gdm3
 [ + ]  grub-common
 [ - ]  hwclock.sh
 [ + ]  irqbalance
 [ + ]  kerneloops
 [ - ]  keyboard-setup.sh
 [ + ]  kmod
 [ + ]  network-manager
 [ + ]  networking
 [ - ]  plymouth
 [ - ]  plymouth-log
 [ - ]  pppd-dns
 [ + ]  procps
 [ - ]  rsync
 [ + ]  rsyslog
 [ - ]  saned
 [ + ]  speech-dispatcher
 [ + ]  thermald
 [ + ]  udev
 [ + ]  ufw
 [ - ]  unattended-upgrades
 [ - ]  uuidd
 [ + ]  whoopsie
 [ - ]  wicd
 [ - ]  x11-common

```

I'm I missing something?

USB has no trouble connecting.

---

### Post by jeremy31 on 2018-01-28
> Failed to stop netowrk-manager.service: Unit netowrk-manager.service not loaded.

Looks like you had a typo, netowrk-manager?

---

### Post by kr4 on 2018-01-28
> Failed to stop netowrk-manager.service: Unit netowrk-manager.service not loaded. 			 		 	 Looks like you had a typo, netowrk-manager?
my bad :oops:

> **chili555 said:**
> Let's amend the sequence just a bit:```
[COLOR=#FF0000]sudo service network-manager stop[/COLOR]
sudo iwconfig wlo1 essid TURBONETT_10088A key e75f7c0bb7
sudo dhclient [COLOR=#FF0000]-v[/COLOR] wlo1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Does the USB connect and work well, WEP notwithstanding?

yep that works... 
Is this going to be my all time medicine? are there any other choices than doing a batch file for this process? :/

---

### Post by chili555 on 2018-01-28
> yep that works... 
Is this going to be my all time medicine? are there any other choices than doing a batch file for this process? :/Awesome.

Let's populate /etc/network/interfaces and see if it works:```
sudo nano  /etc/network/interfaces
```Add this to the end of the file:```

auto wlo1
iface wlo1 inet dhcp
wireless-essid TURBONETT_10088A
wireless-key  e75f7c0bb7 
```Proofread carefully twice. Save the file changes (Ctrl+o followed by Enter) and exit the text editor (Ctrl+x). Reboot.

Did you connect?```
ping -c3 www.ubuntu.com
```

By the way, Network Manager is now off the case and will not show or manage your wireless. Ignore it.

---

### Post by kr4 on 2018-01-28
> **chili555 said:**
> 
Did you connect?```
ping -c3 www.ubuntu.com
```


I't did connect. Thank you very much. But will it work with other wireless networks? I'm curious for 
```
wireless-essid TURBONETT_10088A
wireless-key  e75f7c0bb7 
```

---

### Post by chili555 on 2018-01-28
> But will it work with other wireless networks?It will only work if you amend the file to add the details of the new network.

---

### Post by Kanfused on 2018-03-07
> **eoxs540 said:**
> Ok it works now !!!!
Changes in the BIOS was not saved !!!
Many thanks for your help.
Olivier

Does Bluetooth works for you? As you may be knowing, rtl8723d bluetooth firmware is available in the linux-firmware.git repository. I copied the firmware to the /lib/firmware/rtl_bt, still bluetooth is not working. It is weird that, this laptop (mine is similar - HP 15-BS576TX) has RTL8723DE wireless module and RTL8723B is detected as the firmware and complains about missing rtl8723b_config.bin despite the presence of rtl8723d firmware and config.bin. Here is my thread regarding this problem: [https://ubuntuforums.org/showthread.php?t=2386594&p=13746440#post13746440](https://ubuntuforums.org/showthread.php?t=2386594&p=13746440#post13746440)

---

### Post by alphacentauri82 on 2018-04-27
i can't make it work either. (hp G6 240 - ubuntu 18.04 fresh install)


```


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...
'make' all KVER=4.15.0-20-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8723de: 5.1.1.8_21285.20171026_COEX20170111-1414 not found
Error! Bad return status for module build on kernel: 4.15.0-20-generic (x86_64)
Consult /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log for more information.



```
And the log

```


DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 4.15.0-20-generic (x86_64)
vie abr 27 14:03:02 -03 2018
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-20-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-20-generic'
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.c:22:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h: In function ‘_init_timer’:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:287:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:288:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o' failed
make[2]: *** [/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
Makefile:1884: recipe for target 'modules' failed
make: *** [modules] Error 2



```

---

### Post by alphacentauri82 on 2018-04-27
Just so you know, i fixed it with this one:

[https://github.com/lwfinger/rtlwifi_new/tree/extended](https://github.com/lwfinger/rtlwifi_new/tree/extended)

---

### Post by praseodym on 2018-04-28
Good to know that Larrys PPA works here. Is it 18.04? You are using kernel 4.15.

---

### Post by Kanfused on 2018-05-08
With kernel 4.17-rcX onwards, RTL8723DE Bluetooth also is supported. But, you will have to get the rtl8723d bt firmware from linux firmware git repo. More information is here: [https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-amp-Bluetooth-Linux-driver/m-p/6477307/highlight/true#M146067](https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-amp-Bluetooth-Linux-driver/m-p/6477307/highlight/true#M146067)

---

### Post by jaseemharry on 2018-06-04
I followed these steps but i get an error. 
```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' all KVER=4.11.12-041112-generic...........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8723de: 5.1.1.8_21285.20171026_COEX20170111-1414 not found
Error! Bad return status for module build on kernel: 4.11.12-041112-generic (x86_64)
Consult /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log for more information.

Log File

cat /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/make.log
DKMS make.log for rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414 for kernel 4.11.12-041112-generic (x86_64)
Mon Jun  4 19:33:14 IST 2018
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.11.12-041112-generic/build M=/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build  modules
make[1]: Entering directory `/usr/src/linux-headers-4.11.12-041112-generic'
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_mi.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/pci_intf.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/pci_ops_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.o
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_connect&#8217;:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:744:10: error: variable &#8216;roam_info&#8217; has initializer but incomplete type
   struct cfg80211_roam_info roam_info = {};
          ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:744:29: error: storage size of &#8216;roam_info&#8217; isn&#8217;t known
   struct cfg80211_roam_info roam_info = {};
                             ^
In file included from ./include/linux/kmod.h:22:0,
                 from ./include/linux/module.h:13,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/basic_types.h:81,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:31,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/linux/gfp.h:239:20: warning: passing argument 3 of &#8216;cfg80211_roamed&#8217; makes pointer from integer without a cast [-Wint-conversion]
 #define GFP_ATOMIC (__GFP_HIGH|__GFP_ATOMIC|__GFP_KSWAPD_RECLAIM)
                    ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:760:50: note: in expansion of macro &#8216;GFP_ATOMIC&#8217;
   cfg80211_roamed(padapter->pnetdev, &roam_info, GFP_ATOMIC);
                                                  ^
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:91:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/net/cfg80211.h:5233:6: note: expected &#8216;const u8 * {aka const unsigned char *}&#8217; but argument is of type &#8216;unsigned int&#8217;
 void cfg80211_roamed(struct net_device *dev,
      ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:760:3: error: too few arguments to function &#8216;cfg80211_roamed&#8217;
   cfg80211_roamed(padapter->pnetdev, &roam_info, GFP_ATOMIC);
   ^
In file included from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service_linux.h:91:0,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/osdep_service.h:42,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:22:
./include/net/cfg80211.h:5233:6: note: declared here
 void cfg80211_roamed(struct net_device *dev,
      ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_preinit_wiphy&#8217;:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6762:7: error: &#8216;struct wiphy&#8217; has no member named &#8216;max_sched_scan_reqs&#8217;
  wiphy->max_sched_scan_reqs = 1;
       ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c: At top level:
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6795:25: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .change_virtual_intf = cfg80211_rtw_change_iface,
                         ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6795:25: note: (near initialization for &#8216;rtw_cfg80211_ops.change_virtual_intf&#8217;)
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6818:22: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .add_virtual_intf = cfg80211_rtw_add_virtual_intf,
                      ^
/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.c:6818:22: note: (near initialization for &#8216;rtw_cfg80211_ops.add_virtual_intf&#8217;)
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.11.12-041112-generic'
make: *** [modules] Error 2

```
Please help.

---

### Post by praseodym on 2018-07-19
Hi  jaseemharry,

try it with this one

```
sudo dkms remove -m rtl8723de -v 5.1.1.8_21285.20171026_COEX20170111-1414 --all
sudo rm -r /usr/src/rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414/ 
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot

---

### Post by calaciryaa on 2018-11-11
Hi!
Just wanted to thank you all!

I have a HP notebook 15 da0065nf running on Lubuntu 18.04.1 in dual boot with Windows 10. Realtek RTL 8723DE didn't work, and all my attempts failed but jeremy31's answers fixed it! (simply had to unistall/reinstall dkms), I'm so glad! Now it works, not as well as expected (low signal) but maybe because of the device itself ( too cheap I guess...)

For information: lubuntu installed from live CD (couldn't make the usb key boot...), secure boot disabled, need to press F9 to access GRUB at boot.
Sorry for my language. 

And thank you all so much!

---

### Post by chili555 on 2018-11-11
> Now it works, not as well as expected (low signal) but maybe because of the device itself ( too cheap I guess...)
There is an antenna select feature in the driver. If you'd like additional guidance, please start a new thread.

---


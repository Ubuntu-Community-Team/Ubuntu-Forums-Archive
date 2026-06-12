---
title: "RTL8812au problem in 20.04"
date: 2020-04-29
forum: Networking &amp; Wireless
---

### Post by rpessoa on 2020-04-29
> **chili555 said:**
> That's your device:We wonder then, why the driver loads and doesn't create an interface and trigger Network Manager and get to work.

Let's look for clues in the log:

```
sudo modprobe 8812au && dmesg | grep -i rtl
```

Hello,

I was using my Ubuntu 20.04 with no issues. Yesterday I did an update and my wifi is down. I followed what you posted here:

```
modinfo 8812au | grep 003F
```

```
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
```

But the next step gives me an error message:
 
```
sudo modprobe 8812au && dmesg | grep -i rtl
```

```
modprobe: ERROR: could not insert '8812au': Exec format error
```

Any idea what I can do next to fix my wifi that was working before the update?

---

### Post by jeremy31 on 2020-04-29
Split from [https://ubuntuforums.org/showthread.php?t=2439884](https://ubuntuforums.org/showthread.php?t=2439884)
Please post results from terminal for ```
modinfo 8812au; uname -r; cat /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

---

### Post by rpessoa on 2020-04-29
> **jeremy31 said:**
> Split from [https://ubuntuforums.org/showthread.php?t=2439884](https://ubuntuforums.org/showthread.php?t=2439884)
Please post results from terminal for ```
modinfo 8812au; uname -r; cat /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

Ok, so the output is:

```

filename:       /lib/modules/5.4.0-28-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     A1B4B8FF70567B29CF1C971
alias:          usb:v056Ep4007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0242d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p025Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
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
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       5.4.0-26-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         linux Secure Boot Module Signature key
sig_key:        28:6B:5E:A2:99:D3:7E:42:A1:B5:F7:E2:A7:E2:6E:8E:F0:43:9C:2C
sig_hashalgo:   sha512
signature:      34:01:19:87:49:4D:14:07:C2:D8:2B:BA:C1:E4:2D:4B:FF:09:5F:0F:
        8B:69:40:14:27:97:A6:04:23:B5:10:84:67:8C:5A:BF:1B:F2:CF:FF:
        EF:12:E3:CE:C3:3C:90:1C:FA:B5:BB:01:DB:F7:7D:62:0B:D3:33:66:
        96:A1:1B:BC:1C:DC:98:43:6E:27:A1:BD:20:EE:B9:91:D7:04:F1:86:
        99:67:6D:1D:6B:BD:64:16:90:E5:C4:35:AD:B4:8F:C9:9B:75:2B:7E:
        76:FE:93:C8:5C:3D:93:C5:6C:0F:2B:DE:95:AC:D7:C5:32:B9:00:22:
        C7:E5:D3:85:0D:EA:C5:5E:FF:33:4D:8F:D4:5C:5E:56:1C:87:E1:40:
        B9:A4:EA:E5:32:33:D4:11:BF:CB:92:DA:ED:79:61:42:C1:99:A4:0E:
        C3:61:AB:3D:AD:34:54:DD:07:EC:D4:38:13:EC:FC:9B:A2:08:58:B2:
        70:8E:F7:AE:32:94:80:35:A9:EF:5D:C6:BD:70:44:23:46:47:6C:D2:
        C5:3D:2E:E5:8C:FC:44:58:24:7C:37:88:3E:6E:9E:74:29:97:8C:4F:
        7E:2D:FE:3A:82:B3:04:11:2F:0E:2B:7E:C5:3E:1D:01:FC:57:16:14:
        3B:88:DE:63:EF:F4:0C:3B:A0:27:20:FB:E0:31:DB:1A
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
5.4.0-28-generic
PACKAGE_NAME="rtl8812au"
PACKAGE_VERSION="4.3.8.12175.20140902+dfsg"
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' all"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"


```

---

### Post by jeremy31 on 2020-04-29
OK do ```
gedit admin:///usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```
Change the line MAKE="'make' all" to ```
MAKE="'make' all KVER=${kernelver}"
```
Save and exit
then do ```
sudo sed -i 's/5.4.0-26-generic/5.4.0-28-generic/' /lib/modules/5.4.0-28-generic/updates/dkms/8812au.ko
```
Reboot

---

### Post by rpessoa on 2020-04-29
Did everything but unfortunately it didn't work. I still don't have any sign of my wifi. :( Any other suggestion? and Thanks for helping! :)

---

### Post by jeremy31 on 2020-04-29
See the wireless script link in my signature and post results

---

### Post by rpessoa on 2020-04-29
> **jeremy31 said:**
> See the wireless script link in my signature and post results

```



########## wireless info START ##########

Report from: 29 Apr 2020 09:45 EDT -0400

Booted last: 29 Apr 2020 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Ethernet Connection (2) I219-V [1462:7968]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13b1:003f Linksys WUSB6300 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 001 Device 003: ID 1038:1260 SteelSeries ApS SteelSeries Arctis 7
Bus 001 Device 002: ID 1b1c:0c03 Corsair H100iGTX Cooler
Bus 001 Device 005: ID 046d:c332 Logitech, Inc. G502 Proteus Spectrum Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

8812au               1290240  0
cfg80211              704512  1 8812au
mxm_wmi                16384  0
wmi                    32768  1 mxm_wmi

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
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.0.119/24 brd 192.168.0.255 scope global dynamic noprefixroute enp0s31f6
       valid_lft 42710sec preferred_lft 42710sec
    inet6 fe80::ec39:cef1:ef63:d9a1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp0s31f6 proto dhcp metric 100 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
192.168.0.0/24 dev enp0s31f6 proto kernel scope link src 192.168.0.119 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search test.example.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root        1070       1  0 09:37 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       80372d4f-5237-36d1-8b9f-258cf0343c47
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.119/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             24.200.243.189
IP4.DNS[3]:                             24.200.210.241
DHCP4.OPTION[1]:                        dhcp_lease_time = 43200
DHCP4.OPTION[2]:                        domain_name_servers = 192.168.0.1 24.200.243.189 24.200.210.241
DHCP4.OPTION[3]:                        expiry = 1588210665
DHCP4.OPTION[4]:                        host_name = linux
DHCP4.OPTION[5]:                        interface_mtu = 1500
DHCP4.OPTION[6]:                        ip_address = 192.168.0.119
DHCP4.OPTION[7]:                        next_server = 192.168.0.1
DHCP4.OPTION[8]:                        requested_broadcast_address = 1
DHCP4.OPTION[9]:                        requested_domain_name = 1
DHCP4.OPTION[10]:                       requested_domain_name_servers = 1
DHCP4.OPTION[11]:                       requested_domain_search = 1
DHCP4.OPTION[12]:                       requested_host_name = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[15]:                       requested_nis_domain = 1
DHCP4.OPTION[16]:                       requested_nis_servers = 1
DHCP4.OPTION[17]:                       requested_ntp_servers = 1
DHCP4.OPTION[18]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[19]:                       requested_root_path = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       requested_static_routes = 1
DHCP4.OPTION[22]:                       requested_subnet_mask = 1
DHCP4.OPTION[23]:                       requested_time_offset = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       routers = 192.168.0.1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::ec39:cef1:ef63:d9a1/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::5ef4:abff:feac:2e6a
DHCP6.OPTION[1]:                        dhcp6_domain_search = test.example.com
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   80372d4f-5237-36d1-8b9f-258cf0343c47 | Wired connection 1

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied

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

[[/etc/NetworkManager/system-connections/Ipanema]] (600 root)
[connection] id=Ipanema | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Ipanema
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

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

enp0s31f6  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s31f6  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[8812au]
filename:       /lib/modules/5.4.0-28-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     A1B4B8FF70567B29CF1C971
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       5.4.0-28-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         linux Secure Boot Module Signature key
sig_key:        28:6B:5E:A2:99:D3:7E:42:A1:B5:F7:E2:A7:E2:6E:8E:F0:43:9C:2C
sig_hashalgo:   sha512
signature:      34:01:19:87:49:4D:14:07:C2:D8:2B:BA:C1:E4:2D:4B:FF:09:5F:0F:
        8B:69:40:14:27:97:A6:04:23:B5:10:84:67:8C:5A:BF:1B:F2:CF:FF:
        EF:12:E3:CE:C3:3C:90:1C:FA:B5:BB:01:DB:F7:7D:62:0B:D3:33:66:
        96:A1:1B:BC:1C:DC:98:43:6E:27:A1:BD:20:EE:B9:91:D7:04:F1:86:
        99:67:6D:1D:6B:BD:64:16:90:E5:C4:35:AD:B4:8F:C9:9B:75:2B:7E:
        76:FE:93:C8:5C:3D:93:C5:6C:0F:2B:DE:95:AC:D7:C5:32:B9:00:22:
        C7:E5:D3:85:0D:EA:C5:5E:FF:33:4D:8F:D4:5C:5E:56:1C:87:E1:40:
        B9:A4:EA:E5:32:33:D4:11:BF:CB:92:DA:ED:79:61:42:C1:99:A4:0E:
        C3:61:AB:3D:AD:34:54:DD:07:EC:D4:38:13:EC:FC:9B:A2:08:58:B2:
        70:8E:F7:AE:32:94:80:35:A9:EF:5D:C6:BD:70:44:23:46:47:6C:D2:
        C5:3D:2E:E5:8C:FC:44:58:24:7C:37:88:3E:6E:9E:74:29:97:8C:4F:
        7E:2D:FE:3A:82:B3:04:11:2F:0E:2B:7E:C5:3E:1D:01:FC:57:16:14:
        3B:88:DE:63:EF:F4:0C:3B:A0:27:20:FB:E0:31:DB:1A
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

[cfg80211]
filename:       /lib/modules/5.4.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8795FC14A499B3F7A2F6AD8
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-28-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        42:A8:A9:98:8B:E6:F1:71:2C:AF:A3:32:4E:72:D5:45:3C:41:3F:7A
sig_hashalgo:   sha512
signature:      5C:D8:AC:A2:FD:65:17:DB:37:3C:41:4F:49:45:94:86:F4:B3:EF:B0:
        6F:CF:F7:C7:27:AA:1A:4A:E8:AC:88:C7:BA:D6:71:B9:64:E4:08:16:
        33:A0:CB:BF:A7:A0:9F:33:14:66:1E:A9:61:42:72:50:04:85:79:8D:
        97:36:57:F4:45:04:2C:80:4D:B4:37:EE:D6:CC:A5:D0:43:95:0A:DC:
        AB:F2:13:D7:45:73:B8:85:CF:6B:0C:BA:FB:79:20:97:8F:AE:72:E9:
        18:0D:D6:64:2D:99:BB:62:A1:23:28:50:4B:B6:69:07:56:FE:F9:C5:
        99:78:95:94:A4:E0:79:36:27:DF:66:48:C4:D8:CF:86:29:12:5E:CF:
        CD:40:FF:DC:92:44:9A:1D:A5:57:08:81:5B:A0:0D:2D:42:35:30:0E:
        76:90:8F:D7:E6:8F:66:04:22:3E:CF:C3:99:4C:7B:F2:CE:8A:54:D6:
        83:45:EB:82:3A:CB:E4:26:E3:C8:73:97:06:C2:EB:71:A5:38:75:53:
        AC:5D:2E:DD:8B:68:DE:1C:F8:43:35:C2:B1:C5:E5:19:01:9B:F1:23:
        87:74:D0:64:50:AD:CE:AE:B4:D7:34:67:DB:40:1E:8F:12:D2:D5:E9:
        F7:B6:BD:0E:64:87:24:52:BC:00:15:33:04:08:00:E6:DE:42:54:AA:
        FC:BC:1D:BF:4F:6B:73:AD:77:F7:37:22:C0:C9:D6:A3:CA:D9:02:83:
        54:4B:DA:51:84:AD:84:3A:F8:34:27:79:42:E9:CD:4F:74:65:8C:F2:
        43:A5:26:6F:F1:20:B3:29:29:5C:C2:16:4C:ED:DB:EE:CD:B6:AD:5E:
        C0:E6:C0:54:4D:F9:A7:90:04:38:60:48:51:B2:CA:5D:7D:06:E4:44:
        71:29:C4:73:62:50:4C:30:D6:41:B5:B3:47:71:21:1E:A6:22:AB:19:
        9B:56:28:B1:FB:CD:77:0E:30:71:7B:AD:2C:BD:57:7E:9C:EF:42:75:
        4F:E3:17:44:15:FF:3E:0C:F9:AB:5A:3C:EB:DA:7C:42:41:6B:CE:A9:
        F0:7E:A5:1D:C4:64:7B:17:D9:51:5E:62:5E:7F:AF:D5:99:F3:AE:02:
        50:65:E7:7F:61:AF:54:9B:8D:EF:F0:A4:01:C6:51:84:AE:41:8D:F4:
        7F:E7:B1:C0:D3:E2:F2:BA:38:48:52:A0:FC:B4:BA:F8:0C:C1:BB:66:
        2D:D1:65:2B:A9:C6:2E:1D:D7:C5:90:61:D1:60:9D:54:B8:E9:7C:C2:
        1D:3B:D3:51:5B:CC:F7:92:2B:12:86:4C:EC:FB:BD:E7:E3:D5:1A:EC:
        9B:BA:C5:AA:2A:31:0D:73:AD:56:BA:77
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/blacklist-radeon.conf]
blacklist radeon

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

[   10.393976] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   10.394024] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
[  127.629024]  ? _rtw_malloc+0x2d/0x2f [8812au]
[  127.629084]  ? _rtw_memcpy+0x10/0x12 [8812au]
[  127.629149]  ? rtw_5g_rates_init+0x1a/0x1c [8812au]
[  127.629209]  ? rtw_spt_band_alloc+0xb0/0xb2 [8812au]
[  127.629268]  rtw_wdev_alloc+0xf6/0x29c [8812au]
[  127.629334]  rtw_usb_if1_init+0xf0/0x20c [8812au]
[  127.629390]  rtw_drv_init+0x246/0x2d3 [8812au]

########## wireless info END ############



```

---

### Post by jeremy31 on 2020-04-29
Ok, lets ditch the rtl8812au-dkms
```
sudo apt remove rtl8812au-dkms
```
Install something that should work
```
sudo apt install git 
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au/
sudo dkms-install.sh
```
Reboot

---

### Post by rpessoa on 2020-04-29
> **jeremy31 said:**
> Ok, lets ditch the rtl8812au-dkms
```
sudo apt remove rtl8812au-dkms
```
Install something that should work
```
sudo apt install git 
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au/
sudo dkms-install.sh
```
Reboot

YEAH! Yes it is finally working! Thanks a lot!!! :D

Final question: do I need to redo this every time I update the kernel? or if it stops working after an update?

---

### Post by jeremy31 on 2020-04-29
That one should work with kernel updates.  It also works with quite a few Realtek chipsets RTL8812au, RTL8814au, and RTL8821au
I used it on Mint 19 and now Ubuntu 20.04 with my Edimax AC1750 USB wifi

---

### Post by rpessoa on 2020-04-29
Great! Thanks a lot! Mine is the Linksys one.

:D

---

### Post by jeremy31 on 2020-04-29
Please use the thread tools near the top right of the page to mark as solved.  That source code will work for the following device ID's
```
0846:9054
20F4:809B
20F4:809A
2357:0106
0BDA:8813
7392:A833
7392:A834
056E:400D
056E:400B
0B05:1853
0B05:1852
0B05:1817
2001:331A
0BDA:8813
2357:011F
2357:0120
2357:0122
2357:011E
3823:6249
0BDA:A811
056E:4007
0411:029B
0846:9052
2019:AB32
0411:0242
056E:400F
056E:400E
0E66:0023
2001:3318
2001:3314
04BB:0953
7392:A813
7392:A812
7392:A811
0BDA:0823
0BDA:0820
0BDA:A811
0BDA:8822
0BDA:0821
0BDA:0811
0BDA:881A
2604:0012
0BDA:8812
148F:9097
050D:1109
0411:025D
20F4:805B
2357:0122
2357:010F
2357:010E
2357:0115
2357:010D
2357:0103
2357:0101
13B1:003F
2001:3316
2001:3315
2001:3313
2001:330E
0846:9051
07B8:8812
2019:AB30
1740:0100
1058:0632
2001:3313
0586:3426
0E66:0022
0B05:17D2
0409:0408
0789:016E
04BB:0952
0DF6:0074
7392:A822
050D:1106
0BDA:881C
0BDA:881B
0BDA:881A
0BDA:8812
```

---

### Post by bobsuncle on 2020-05-19
> **jeremy31 said:**
> Ok, lets ditch the rtl8812au-dkms
```
sudo apt remove rtl8812au-dkms
```
Install something that should work
```
sudo apt install git 
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au/
sudo dkms-install.sh
```
Reboot

This is a bit depressing ....

I had hoped that 20.04 would include support for the 8812 chipset so that we wouldn't need to use these sorts of repositories.

---


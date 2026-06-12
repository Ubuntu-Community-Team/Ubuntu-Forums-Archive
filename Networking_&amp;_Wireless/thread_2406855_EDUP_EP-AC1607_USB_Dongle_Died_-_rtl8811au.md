---
title: "EDUP EP-AC1607 USB Dongle Died - rtl8811au"
date: 2018-11-26
forum: Networking &amp; Wireless
---

### Post by electrosteam on 2018-11-26
Lubuntu 18.04.1 LTS, up to date.


I added an EDUP EP-AC1607 USB dongle to my system in September.
Installed the rtl8812au driver using Synaptic Package Manager and got it working fine (after a few teething problems).


Recorded a wireless info script for it on 10Sep18.
Linux 4.15.0-33-generic #36-Ubuntu.


Tried the dongle out today - no joy.
Did a new wireless info script.
Linux 4.15.0-39-generic #42-Ubuntu.


lsusb recognizes the dongle, but no evidence of rf operation.
lsmod shows cfg80211 as '0', wheras the 10Sep18 showed '1 8812au'.
rfkill shows no result, wheras 10Sep18 showed 'Wireless LAN, no blocks'.
Did an un-install/install cycle of the driver package without any joy.
Tried Rebooting and different USB socket - no result.

Any suggestions ?
(got to research how to get pastebin to work)
John.

---

### Post by jeremy31 on 2018-11-26
Try in terminal ```
sudo apt-get install --reinstall rtl8812au-dkms
```
Reboot

---

### Post by electrosteam on 2018-11-27
Jeremy,
did the install, reboot sequence, no change.
Still no pastebin account, but the wireless info text file size is less than 17 kB, so should be Ok to paste below.

```



########## wireless info START ##########


Report from: 27 Nov 2018 18:19 AEDT +1100


Booted last: 27 Nov 2018 00:00 AEDT +1100


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:43:58 UTC 2018 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Lubuntu


##### lspci #############################


02:01.0 Ethernet controller [0200]: Broadcom Limited BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell BCM4401 100Base-T [1028:015f]
    Kernel driver in use: b44


##### lsusb #############################


Bus 001 Device 002: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


dell_laptop            20480  0
dell_smbios            20480  1 dell_laptop
dell_wmi_descriptor    16384  1 dell_smbios
cfg80211              532480  0
mxm_wmi                16384  1 nouveau
wmi                    20480  4 dell_wmi_descriptor,mxm_wmi,nouveau,dell_smbios
ssb                    57344  1 b44
video                  40960  2 dell_laptop,nouveau


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
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eth0' [IF1]> brd <MAC address>
    inet 192.168.1.104/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0
       valid_lft 84712sec preferred_lft 84712sec
    inet6 fe80::2a20:67e9:73ba:468a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


default via 192.168.1.1 dev eth0 proto dhcp metric 100 
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.104 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       460     1  0 17:50 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4401 100Base-T
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       c7c6dfe6-5d79-4215-a8d5-b4c9843c671a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.104/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        expiry = 1543387866
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       requested_subnet_mask = 1
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       ip_address = 192.168.1.104
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::2a20:67e9:73ba:468a/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c7c6dfe6-5d79-4215-a8d5-b4c9843c671a | Auto Ethernet


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
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WiFi-D97A]] (600 root)
[connection] id=WiFi-D97A | type=wifi | permissions=
[wifi] bssid=<MAC address> | mac-address=<MAC address> | mac-address-blacklist= | ssid=WiFi-D97A
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | autoconnect=false | permissions=
[wifi] bssid=<MAC address> | mac-address=<MAC address> | mac-address-blacklist= | mtu=1500 | ssid=Bus Depot
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WiFi-D97A 1]] (600 root)
[connection] id=WiFi-D97A 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WiFi-D97A
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Australia/Sydney (based on set time zone)


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


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.15.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-39-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/4.15.0-39-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     12D8BAB8F43573B88998E25
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       4.15.0-39-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


##### module parameters #################


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   26.292339] 8812au: version magic '4.15.0-38-generic SMP mod_unload 686 ' should be '4.15.0-39-generic SMP mod_unload 686 '
[   42.837592] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   45.824184] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   45.824189] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[   45.824264] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   92.832168] b44 ssb0:0 eth0: Link is down
[   95.840119] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   95.840127] b44 ssb0:0 eth0: Flow control is off for TX and off for RX


########## wireless info END ############

```

Note that the wireless info text was taken with both ethernet cable and dongle connected.

John

---

### Post by jeremy31 on 2018-11-28
Post results for ```
dkms status
```

---

### Post by electrosteam on 2018-11-28
```

~$ dkms status
rtl8812au, 4.2.2, 4.15.0-39-generic, i686: built
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.15.0-39-generic, i686: installed (WARNING! Diff between built and installed module!)

```

I did try a re-install of the rtl8812au package (via Synaptic Package Manager) as my first attempt at rectification.
John

---

### Post by jeremy31 on 2018-11-28
What about ```
modinfo 8812au
```

---

### Post by electrosteam on 2018-11-29
```

~$ modinfo 8812au
filename:       /lib/modules/4.15.0-39-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     0FE007DE1CB755560C5BB1D
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
vermagic:       4.15.0-38-generic SMP mod_unload 686 
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

```

The dongle was inserted for the above, thanks,
John.

---

### Post by jeremy31 on 2018-11-29
Ok, I see the problem now, do ```
sudo apt remove rtl8812au-dkms
```
Reboot and hopefully it works

---

### Post by electrosteam on 2018-11-30
Entered the command suggested, and rebooted.
Doesn't look encouraging.
 ```

john@Bluebox:~$ nmcli dev wifi list
john@Bluebox:~$ 

```

Would trying the dongle in my wife's Windows 10 machine provide useful data (I have the appropriate install disc for that)?
John.

---

### Post by jeremy31 on 2018-12-01
```
sudo dkms install rtl8812au/4.2.2
```
Reboot

---

### Post by electrosteam on 2018-12-02
Jeremy,
Not looking good for this dongle:

```

john@Bluebox:~$ sudo dkms install rtl8812au/4.2.2
[sudo] password for john: 


8812au:
Running module version sanity check.
Error! Module version v4.2.2_7502.20130517 for 8812au.ko
is not newer than what is already found in kernel 4.15.0-39-generic (v4.3.8_12175.20140902).
You may override by specifying --force.


depmod............


DKMS: install completed.
john@Bluebox:~$ 


john@Bluebox:~$ nmcli dev wifi list
john@Bluebox:~$ 

```

---

### Post by jeremy31 on 2018-12-02
Reboot
What does ```
dkms status
```
Show
Just need a module that has your wifi cards ID in it build with the correct modversion

---

### Post by electrosteam on 2018-12-02
Reboot as suggested:

```

john@Bluebox:~$ dkms status
rtl8812au, 4.2.2, 4.15.0-39-generic, i686: installed (WARNING! Diff between built and installed module!)
john@Bluebox:~$ 

```

Using Synaptic Package Manager, my system shows nothing installed for rtl8812au.
But lists the following as available:
rtl8812au-dkms          4.3.8.12175.20140902+dfsg-0ubuntu8

John

---

### Post by jeremy31 on 2018-12-02
We can try a hack and see if it fixes the module that is there
```
sudo sed -i 's/4.15.0-38/4.15.0-39/' /lib/modules/4.15.0-39-generic/updates/dkms/8812au.ko
```
Reboot

The problem with the rtl8812au-dkms is that dkms support is a little broken and it builds against the old kernel headers when a new kernel is installed

With the source code you have now, hopefully dkms works in it and the issue won't happen with the next kernel update

---

### Post by electrosteam on 2018-12-02
Jeremy,
Thank you for being so tolerant and persistant.

Entered command, then:
```

john@Bluebox:~$ dkms status
rtl8812au, 4.2.2, 4.15.0-39-generic, i686: installed (WARNING! Diff between built and installed module!)
john@Bluebox:~$ nmcli dev wifi list
john@Bluebox:~$  /sbin/iw dev
john@Bluebox:~$ 

```

Synaptic Package Manager shows rtl8812au as not installed.

---

### Post by jeremy31 on 2018-12-02
So have you rebooted since running the command?  If you have and it still isn't working, do ```
sudo depmod -a
```
Reboot again

---

### Post by electrosteam on 2018-12-02
Jeremy,
the reboot did the trick - amazing.
Operating on the dongle.
Thank you.

For future upgrades to the kernel, can you recommend a procedure to avoid this problem ?

John (happy in Sydney).

---

### Post by jeremy31 on 2018-12-02
I think you might be ok with the code you will be using with the next kernel update according to the dkms status results.  If it doesn't work out that way, bump this thread

---

### Post by electrosteam on 2019-08-02
jeremy31,

Lubuntu 18.04.2 LTS on an old tower.

Today's offered upgrade has disabled the WiF.
Tried the uninstall/reinstall/reboot cycle without success.
Other system problems are also evident and need to be dealt with at the same time.

I will now work through all the suggestions in this thread, and look closely at those in the current thread [https://ubuntuforums.org/showthread.php?t=2407625](https://ubuntuforums.org/showthread.php?t=2407625), " [SOLVED] Driver for RTL8811 Wireless Adapter for Ubuntu 18.04 ".

John

---


---
title: "HP wifi issues in UBUNTU 16.04"
date: 2017-05-21
forum: Networking &amp; Wireless
---

### Post by sayanmndl21 on 2017-05-21
I have tried a lot of solutions but nothing helps. I have a RTL8723BE card, although it connects(sometimes) the network is so slow that it's literally *not connected*.
The recent fix i followed this link: [URL="https://ubuntuforums.org/showthread.php?t=2206487&page=2"]https://ubuntuforums.org/showthread.php?t=2206487&page=2

[/URL]I downloaded the latest version and tried out.. It showed the following error:
```
sayan@sayan-HP-Pavilion-Notebook:~/Desktop/backports-4.2.6-1$ make
make[5]: 'conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/compat/main.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/compat/lib-average.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/compat/compat.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/main.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/regd.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/hw.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/key.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/dfs_pattern_detector.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/dfs_pri_detector.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/beacon.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/gpio.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/init.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/main.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/recv.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/xmit.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/link.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/antenna.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/channel.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/mci.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/pci.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ath9k.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9002_hw.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_hw.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/hw.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_phy.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9002_phy.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar5008_phy.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9002_calib.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_calib.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/calib.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/eeprom.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/eeprom_def.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/eeprom_4k.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/eeprom_9287.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ani.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/mac.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9002_mac.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_mac.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_eeprom.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_paprd.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/btcoex.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_mci.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_aic.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ar9003_rtt.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ath9k_hw.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/common.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/common-init.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/common-beacon.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/common-debug.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/common-spectral.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ath9k_common.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/htc_hst.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/hif_usb.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/wmi.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/htc_drv_txrx.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/htc_drv_main.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/htc_drv_beacon.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/htc_drv_init.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/htc_drv_gpio.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/drivers/net/wireless/ath/ath9k/ath9k_htc.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/main.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/status.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/sta_info.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/wep.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/wpa.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/scan.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/offchannel.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/ht.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/agg-tx.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/agg-rx.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/vht.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/ibss.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/iface.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/rate.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/michael.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/tkip.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/aes_ccm.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/aes_gcm.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/aes_cmac.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/aes_gmac.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/cfg.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/ethtool.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/rx.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/spectmgmt.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/tx.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/key.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/util.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/wme.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/event.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/chan.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/trace.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mlme.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/tdls.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/ocb.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/led.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mesh.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mesh_plink.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mesh_hwmp.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mesh_sync.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mesh_ps.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/pm.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/rc80211_minstrel_ht.o
  LD [M]  /home/sayan/Desktop/backports-4.2.6-1/net/mac80211/mac80211.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/core.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/sysfs.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/radiotap.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/util.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/reg.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/scan.o
  CC [M]  /home/sayan/Desktop/backports-4.2.6-1/net/wireless/nl80211.o
/home/sayan/Desktop/backports-4.2.6-1/net/wireless/nl80211.c: In function ‘nl80211_send_iface’:
/home/sayan/Desktop/backports-4.2.6-1/net/wireless/nl80211.c:2391:6: error: implicit declaration of function ‘nla_put_u64’ [-Werror=implicit-function-declaration]
      nla_put_u64(msg, NL80211_ATTR_WDEV, wdev_id(wdev)) ||
      ^
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/home/sayan/Desktop/backports-4.2.6-1/net/wireless/nl80211.o' failed
make[6]: *** [/home/sayan/Desktop/backports-4.2.6-1/net/wireless/nl80211.o] Error 1
scripts/Makefile.build:440: recipe for target '/home/sayan/Desktop/backports-4.2.6-1/net/wireless' failed
make[5]: *** [/home/sayan/Desktop/backports-4.2.6-1/net/wireless] Error 2
Makefile:1491: recipe for target '_module_/home/sayan/Desktop/backports-4.2.6-1' failed
make[4]: *** [_module_/home/sayan/Desktop/backports-4.2.6-1] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[3]: *** [modules] Error 2
Makefile.real:88: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2


```

This is my wireless info:
```
########## wireless info START ##########

Report from: 21 May 2017 09:52 GMT +0000

Booted last: 21 May 2017 00:00 GMT +0000

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.8.0-53-generic #56~16.04.1-Ubuntu SMP Tue May 16 01:18:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:8096]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 17ef:7997 Lenovo 
Bus 001 Device 002: ID 064e:930c Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8723be              90112  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              761856  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              581632  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    16384  3 mxm_wmi,nouveau,hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp0s20u6 Link encap:Ethernet  HWaddr <MAC 'enp0s20u6' [IF2]>  
          inet addr:192.168.42.59  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::b273:9c7b:4a44:b73b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2742 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1110112 (1.1 MB)  TX bytes:529467 (529.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:244876 (244.8 KB)  TX bytes:244876 (244.8 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

enp0s20u6  no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20u6
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20u6
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20u6

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       838     1  0 09:45 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Android
GENERAL.PRODUCT:                        Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u6' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/net/enp0s20u6
GENERAL.IP-IFACE:                       enp0s20u6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       daa74105-d560-30f1-a5b2-fe260be25523
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   daa74105-d560-30f1-a5b2-fe260be25523 | Wired connection 2
IP4.ADDRESS[1]:                         192.168.42.59/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.59
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1495363623
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = sayan-HP-Pavilion-Notebook
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::b273:9c7b:4a44:b73b/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.8.0-53-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b7776b96-d022-4204-8167-3930b13327ba | D-Link_DIR-816

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
D-Link_DIR-816  <MAC 'D-Link_DIR-816' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --        no        

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

[[/etc/NetworkManager/system-connections/STUDENT]] (600 root)
[connection] id=STUDENT | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=STUDENT
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/No networks found]] (600 root)
[connection] id=No networks found | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=No networks found
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Srikanth Vemula 1]] (600 root)
[connection] id=Srikanth Vemula 1 | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=Srikanth Vemula
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link_DIR-816]] (600 root)
[connection] id=D-Link_DIR-816 | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=D-Link_DIR-816
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Connectify-Dipramit]] (600 root)
[connection] id=Connectify-Dipramit | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=Connectify-Dipramit
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Srikanth Vemula]] (600 root)
[connection] id=Srikanth Vemula | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=Srikanth Vemula
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CintLAB]] (600 root)
[connection] id=CintLAB | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=CintLAB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi_Malay]] (600 root)
[connection] id=WiFi_Malay | type=wifi | permissions=user:sayan:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=WiFi_Malay
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Ouagadougou (based on set time zone)

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

enp0s20u6  no frequency information.

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

enp0s20u6  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'D-Link_DIR-816' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"D-Link_DIR-816"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000037ea1143
                    Extra: Last beacon: 736ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     1520FD8B69687790125304A
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B06F4AE01E9561133D82E7E
depends:        
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     886A7942BD1E48BF21ECA79
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B936ED0E7D6B2CC6861A1AE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 2
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist bcma
blacklist brcm80211
blacklist bcma
blacklist brcm80211
blacklist bcma
blacklist brcm80211
blacklist bcma
blacklist brcm80211

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be ant_sel=2

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   19.168479] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   19.186407] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.186998] rtlwifi: rtlwifi: wireless switch is on
[   19.445557] rtl8723be 0000:08:00.0 wlo1: renamed from wlan0
[   44.475805] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   44.560659] r8169 0000:09:00.0 eno1: link down
[   44.560751] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   44.582996] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 3 times)
[   69.531601] wlo1: authenticate with <MAC 'D-Link_DIR-816' [AC1]>
[   69.557794] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 1/3)
[   69.659232] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 2/3)
[   69.763245] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 3/3)
[   69.867235] wlo1: authentication with <MAC 'D-Link_DIR-816' [AC1]> timed out
[   70.972278] wlo1: authenticate with <MAC 'D-Link_DIR-816' [AC1]>
[   70.996955] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 1/3)
[   71.099387] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 2/3)
[   71.203297] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 3/3)
[   71.307335] wlo1: authentication with <MAC 'D-Link_DIR-816' [AC1]> timed out
[   72.796463] wlo1: authenticate with <MAC 'D-Link_DIR-816' [AC1]>
[   72.820756] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 1/3)
[   72.923425] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 2/3)
[   73.027420] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 3/3)
[   73.131445] wlo1: authentication with <MAC 'D-Link_DIR-816' [AC1]> timed out
[   75.119826] wlo1: authenticate with <MAC 'D-Link_DIR-816' [AC1]>
[   75.145293] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 1/3)
[   75.247528] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 2/3)
[   75.351548] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 3/3)
[   75.455522] wlo1: authentication with <MAC 'D-Link_DIR-816' [AC1]> timed out
[   87.440513] wlo1: authenticate with <MAC 'D-Link_DIR-816' [AC1]>
[   87.464563] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 1/3)
[   87.568190] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 2/3)
[   87.672180] wlo1: send auth to <MAC 'D-Link_DIR-816' [AC1]> (try 3/3)
[   87.703208] wlo1: authenticated
[   87.705498] wlo1: associate with <MAC 'D-Link_DIR-816' [AC1]> (try 1/3)
[   87.808190] wlo1: associate with <MAC 'D-Link_DIR-816' [AC1]> (try 2/3)
[   87.912188] wlo1: associate with <MAC 'D-Link_DIR-816' [AC1]> (try 3/3)
[   88.016451] wlo1: association with <MAC 'D-Link_DIR-816' [AC1]> timed out
[   93.018418] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  113.794999] rndis_host 1-6:1.0 enp0s20u6: renamed from usb0
[  113.814286] IPv6: ADDRCONF(NETDEV_UP): enp0s20u6: link is not ready

########## wireless info END ############
```

Help appreciated
Thank you!

---

### Post by jeremy31 on 2017-05-21
Welcome to the forums
You don't need to install anything as this might be an issue with HP using one antenna wire on a wireless chip with 2 antenna connections.

Try ```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723
```

See if the signal strength improves so that you can connect

---


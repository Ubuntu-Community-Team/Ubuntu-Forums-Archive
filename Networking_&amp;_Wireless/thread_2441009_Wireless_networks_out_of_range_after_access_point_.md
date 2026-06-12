---
title: "Wireless networks out of range after access point setup, please help"
date: 2020-04-17
forum: Networking &amp; Wireless
---

### Post by colbygb on 2020-04-17
Hi,

I have been struggling with this problem. My goal is set up my Jetson TX2, ubuntu 18.04, as an access point so I can remotely login using ssh. After setting up an access point, I would then turn off hotspot so I can re-connect to wireless internet, but none of the wireless networks show up anymore although I know they are there. I have tried everything I can find online regarding this but I have had no luck.  First time I just re-flashed the Jetson and things were fine again, but after trying again same problem surfaced. I really would like to understand and fix this. I have attached a text file with all relevant wireless information using [this]("https://ubuntuforums.org/showthread.php?t=370108").

```


########## wireless info START ##########


Report from: 17 Apr 2020 12:55 CDT -0500


Booted last: 17 Apr 2020 00:00 CDT -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.9.140-tegra #1 SMP PREEMPT Mon Dec 9 22:52:02 PST 2019 aarch64 aarch64 aarch64 GNU/Linux


, rw, rootwait, rootfstype=ext4, console=ttyS0,115200n8, console=tty0, fbcon=map:0, net.ifnames=0, video=tegrafb, no_console_suspend=1, earlycon=uart8250,mmio32,0x3100000, nvdumper_reserved=0x2772e0000, gpt, tegra_fbmem2=0x140000@0x9607d000, lut_mem2=0x2008@0x9607a000, usbcore.old_scheme_first=1, tegraid=18.1.2.0.0, maxcpus=6, boot.slot_suffix=, boot.ratchetvalues=0.2031647.1, bl_prof_dataptr=0x10000@0x275840000, sdhci_tegra.en_boot_part_access=1, quiet


##### desktop ###########################


Unity


##### lspci #############################


##### lsusb #############################


Bus 002 Device 002: ID 05e3:0626 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: bluedroid_pm: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmfmac-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


cfg80211              589351  1 bcmdhd


##### interfaces ########################


[/etc/network/interfaces]
source-directory /etc/network/interfaces.d


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: dummy0: <BROADCAST,NOARP> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'dummy0' [IF1]> brd <MAC address>
3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'eth0' [IF2]> brd <MAC address>
    inet 192.168.0.109/24 brd 192.168.0.255 scope global dynamic noprefixroute eth0
       valid_lft 7085sec preferred_lft 7085sec
    inet6 fe80::3f3a:6668:9ad5:7971/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state DORMANT group default qlen 1000
    link/ether <MAC 'wlan0' [IF3]> brd <MAC address>
5: l4tbr0: <BROADCAST,MULTICAST> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'l4tbr0' [IF4]> brd <MAC address>
    inet 192.168.55.1/24 brd 192.168.55.255 scope global l4tbr0
       valid_lft forever preferred_lft forever
    inet6 fe80::1/128 scope link tentative 
       valid_lft forever preferred_lft forever
6: rndis0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast master l4tbr0 state DOWN group default qlen 1000
    link/ether <MAC 'l4tbr0' [IF4]> brd <MAC address>
7: usb0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast master l4tbr0 state DOWN group default qlen 1000
    link/ether <MAC 'usb0' [IF6]> brd <MAC address>
8: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF7]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


eth0      no wireless extensions.


dummy0    no wireless extensions.


docker0   no wireless extensions.


rndis0    no wireless extensions.


usb0      no wireless extensions.


l4tbr0    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=31 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


default via 192.168.0.1 dev eth0 proto dhcp metric 100 
169.254.0.0/16 dev eth0 scope link metric 1000 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.0.0/24 dev eth0 proto kernel scope link src 192.168.0.109 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '/run/resolvconf/resolv.conf']


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root      8725     1  0 11:57 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         eqos
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eth0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/2490000.ether_qos/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f6df4fb2-9b3e-3573-8217-385d1b6fa1d1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.109/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1587153235
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       requested_ntp_servers = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.109
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_netbios_scope = 1
DHCP4.OPTION[20]:                       dhcp_message_type = 5
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 7200
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_host_name = 1
DHCP4.OPTION[26]:                       dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[27]:                       domain_name_servers = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::3f3a:6668:9ad5:7971/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f6df4fb2-9b3e-3573-8217-385d1b6fa1d1 | Wired connection 1


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF7]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       99558670-ba68-453f-812c-4dc3fccd2297
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.17.0.0/16, nh = 0.0.0.0, mt = 0
IP6.GATEWAY:                            --
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   99558670-ba68-453f-812c-4dc3fccd2297 | docker0


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corp.
GENERAL.PRODUCT:                        BCM4354 WLAN card
GENERAL.DRIVER:                         bcmsdh_sdmmc
GENERAL.DRIVER-VERSION:                 0
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlan0' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/3440000.sdhci/mmc_host/mmc1/mmc1:0001/mmc1:0001:2/net/wlan0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2afa8486-f649-4620-a940-239719bca157 | 512 Grimauld place


GENERAL.DEVICE:                         l4tbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'l4tbr0' [IF4]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/l4tbr0
GENERAL.IP-IFACE:                       l4tbr0
GENERAL.IS-SOFTWARE:                    yes
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         192.168.55.1/24
IP4.GATEWAY:                            --
IP6.ADDRESS[1]:                         fe80::1/128
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::1/128, nh = ::, mt = 256
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         dummy0
GENERAL.TYPE:                           dummy
GENERAL.NM-TYPE:                        NMDeviceDummy
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         dummy
GENERAL.DRIVER-VERSION:                 1.0
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'dummy0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/dummy0
GENERAL.IP-IFACE:                       dummy0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         rndis0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         tegra-xudc-new
GENERAL.DRIVER-VERSION:                 29-May-2008
GENERAL.FIRMWARE-VERSION:               tegra-xudc
GENERAL.HWADDR:                         <MAC 'l4tbr0' [IF4]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/3550000.xudc/gadget/net/rndis0
GENERAL.IP-IFACE:                       rndis0
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         tegra-xudc-new
GENERAL.DRIVER-VERSION:                 29-May-2008
GENERAL.FIRMWARE-VERSION:               tegra-xudc
GENERAL.HWADDR:                         <MAC 'usb0' [IF6]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/3550000.xudc/gadget/net/usb0
GENERAL.IP-IFACE:                       usb0
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/10-ubuntu-fan.conf]]
[keyfile]
unmanaged-devices+=interface-name:fan-*


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


[[/etc/NetworkManager/system-connections/512 Grimauld place]] (600 root)
[connection] id=512 Grimauld place | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF3]> | mac-address-blacklist= | ssid=512 Grimauld place
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


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


eth0      no frequency information.


dummy0    no frequency information.


docker0   no frequency information.


rndis0    no frequency information.


usb0      no frequency information.


l4tbr0    no frequency information.


lo        no frequency information.


wlan0     21 channels in total; available frequencies :
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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


dummy0    Interface doesn't support scanning.


docker0   Interface doesn't support scanning.


rndis0    Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Invalid argument


l4tbr0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.9.140-tegra/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        
intree:         Y
vermagic:       4.9.140-tegra SMP preempt mod_unload modversions aarch64
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


bluedroid_pm
nvhost_vi
nvgpu


##### modprobe options ##################


[/etc/modprobe.d/bcmdhd.conf]
install bcmdhd test -d /lib/firmware/brcm && /sbin/modprobe --ignore-install bcmdhd
options bcmdhd op_mode=2


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


[/etc/modprobe.d/blacklist-mttcan.conf]
blacklist mttcan


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/blacklist-tegra-safety.conf]
blacklist tegra-safety


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 3275.002419] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready
[ 3277.971619] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3278.075421] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############



```

Please help before I go insane.

---

### Post by charles-scoville on 2020-04-19
Probably not as helpful as you would like, but I notice your WiFi is broadcom. In my experience, broadcom is a joke for GNU/Linux support pretty much across the board. Which is quite ironic considering they are the progenitors of the RPi.

...

Just searching for your BCM4354 WLAN, I found this interesting snippet that I think is related to your broadcom BT device, and firmware which is quite interesting.
> There may be incorrect naming between presented firmware name and name requested from Linux kernel. For example, system may request BCM4354A2-13d3-3485.hcd but actually this is BCM4356A2-13d3-3485.hcd. This is happens because incorrect naming in Linux kernel. Just rename file to name that need to kernel. Here quick naming convertion:

Here is the source for this quote. [https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware).

They are talking about Bluetooth there, but a lot of cards nowadays are both Bluetooth+WiFi combined, so the fix may be combined too. You could try the same fix they recommend there, and force the kernel to use a different firmware.

Here is another link that appears to have clean firmware.
[https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211)

That's just my non-expert, kneejerk, off-the-cuff assessment. Hopefully it's helpful, but don't bet the race on it.

---

### Post by colbygb on 2020-04-20
Hi,

Thanks for the reply. So that is some interesting stuff you found but I wasn't able to find any evidence that the wrong firmware was being loaded. All drivers seems to be in place in '/lib/firmware/bcrm'.

The output of dmesg --syslog had a couple things that seemed relevant.  

[FONT=Arial][    5.723650] wifi_platform_get_country_[/FONT][FONT=Arial]code_map: could not get country_code_map[/FONT]
[FONT=Arial][    5.723655] wifi_plat_dev_drv_probe:[/FONT][FONT=Arial]platform country code map is not available
[/FONT]
[FONT=Arial][    7.720225] wl_android_wifi_on in[/FONT]
[FONT=Arial][    7.720229] wifi_platform_set_power = 1[/FONT]
[FONT=Arial][    7.931018] vdd-1v8: voltage operation not allowed[/FONT]
[FONT=Arial][    7.935894] sdhci-tegra 3440000.sdhci: could not set regulator OCR (-1) #happens 7 times[/FONT]
[FONT=Arial]
[    8.311502] Firmware up: op_mode=0x0002, MAC=00:04:4b:df:81:2d
[    8.315787] clm path from default:/lib/firmware/brcm/bcmdhd.clm_blob       
[    8.315819] Skipping the clm download. len:0 memblk:          (null)
[    8.318033] dhd_preinit_ioctls pspretend_threshold for HostAPD failed  -23
[    8.321556] Firmware version = wl0: May 17 2019 16:59:40 version 7.35.349.79 (r714996 CY) FWID 01-e527e2ad
[    8.323945] dhd_interworking_enable: failed to set WNM info, ret=-23


then this happens a bunch of times until end of message


[  111.119941]  __wl_cfg80211_scan :
[  111.119974] Invalid Scan Command at SoftAP mode
[  111.119989]  wl_cfg80211_scan : 



[/FONT]

I am really not sure what to do here, this stuff is a bit over my head. [https://patchwork.kernel.org/patch/10750349/](https://patchwork.kernel.org/patch/10750349/) had some stuff that seemed to explain the .clm_blob thing but wasn't able to follow to closely about how I would fix. Seems like setting up the hotspot changes some setting that points to the correct firmware? I don't know just very annoying blehhh

---

### Post by charles-scoville on 2020-04-20
At a glance, this part concerns me most:

_[FONT=Arial]sdhci-tegra 3440000.sdhci: could not set regulator OCR (-1) #happens 7 times[/FONT]_[FONT=Arial]

The important thing I see is that 'could not set regulator' bit. 

I'm  an electrical engineering type, this means I may have some biases. "To a  man with just a hammer, every problem is a nail." So, to me, a  'regulator' is a *voltage regulator*; a thing that makes/controls  voltage. Hypothetically, let's say this cannot be started, that would  mean the device could not be powered on. This would also likely mean a  FW issue IMHO, as setting up any kind of adjustable voltage regulators  is the responsibility of the FW.

Something that further supports the theory that this is voltage regulator related is, interestingly, the line just before that:

[FONT=Arial]_vdd-1v8: voltage operation not allowed_
[/FONT][FONT=Arial]
vdd  stands for "Voltage Drain Drain" and is a reference to the voltage  across a CMOS transistor drain. This is bog standard jargon in EE, and  is used when talking about a chip's positive supply voltage.  Furthermore, 1v8 is also bog standard in EE, and actually means 1.8  volts; a very common logic level voltage for modern CMOS chips. The  "voltage operation not allowed," therefore, most likely means that  something system side tried to set/get this voltage, and the thing on  the listening side wasn't able to do that. 

That line is the first thing that looks like an error, so we should look at the line before:

[/FONT][/FONT]_[FONT=Arial][FONT=Arial][FONT=Arial]wifi_platform_set_power = 1[/FONT][/FONT][/FONT]_[FONT=Arial]

And,  to me, it all makes quite a bit of sense now. The system is trying to  power the WiFi platform, internally it's probably breaking this down  into smaller steps, one being selecting the specific voltage. It  eventually sends a command to the FW to do exactly this, the FW says "I  can't do that," goes limp, and nothing else can work after that.  Everything else you see afterwards really can't be trusted, as it's not  exactly as if it's getting double checked or anything.

> I wasn't able to find any evidence that the wrong firmware was being loaded.

I think you actually have. Or, rather, that the correct firmware isn't being loaded at all.
[/FONT]
This  post is long enough, so I'll try not to bury you with all the details. But,  basically, in short, the WiFi platform itself is a little computer all  on it's own. A "System On a Chip" or SoC. This computer has it's own  BIOS, the ROM bootloader, as well as it's own OS, the firmware blob. But  therein lies the problem. If you look at the logs you posted, the file "bcmdhd.clm_blob" is apparently not being loaded. 

Notice "[FONT=Arial]Skipping the clm download" here:[/FONT]
[U]
[FONT=Arial]clm path from default:/lib/firmware/brcm/bcmdhd.clm_blob 
Skipping the clm download. len:0 memblk: (null)[/FONT][/U]

This  could be the fault of the ROM/bootloader in the WiFi platform, but that should be  highly unlikely. The ROM bootloader is virtually guaranteed to work  fine, or the whole chip would be scrap out of the factory. (It would be  like getting a motherboard that couldn't even load to a BIOS screen.) It  is far more likely that the system (Linux) is not saying the right  things to the WiFi platform to get to a point to even load the firmware  blob, which is in perfect alignment with the previous messages regarding  setting up the regulator.

But does this actually help us?

Well, doing a Google search on a solution to the regulator problem, brought up this Nvidia thread:

[https://forums.developer.nvidia.com/t/jetson-tx2-does-not-login/110477](https://forums.developer.nvidia.com/t/jetson-tx2-does-not-login/110477)

There  is a solution in the above thread involving reflashing with something called  "Jetpack." If that makes any sense to you, you could try that. 

Other  than this, I have limited options to give you, as this really seems like  a maintainer issue, not a user settings issue.

---

### Post by colbygb on 2020-04-24
Hi,

Thanks again. So yes, I went ahead and re-flashed the OS and installed jetpack through their SDK manager, gui for installing libraries for AI, CUDA. I will have to look into the voltage thing, I still see these messages on startup screen.

Thanks again for your help!

Colby

---


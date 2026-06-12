---
title: "ASUS 1215p wifi keeps failing"
date: 2020-09-25
forum: Networking &amp; Wireless
---

### Post by TygerTung on 2020-09-25
Hi, I have this old trusty ASUS netbook, and haven't had any problems for years, but just recently the wifi stops working, usually if you are not on the machine for a while and then I have found no way of getting it going again other than a hard restart.

I was previously using Ubuntu studio 18.04, but I just installed Lubuntu 20.04, hoping that the problem would be fixed by re-installing, however the problem persists.

Could it be that there has been a kernel upgrade, and the wifi module doesn't like it? Previously the bluetooth would never work, but it started working a couple of months ago, maybe due to an update.

Any help would be appreciated.

Cheers,

Sam

---

### Post by Yellow Pasque on 2020-09-26
Please run the wirless info script: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by TygerTung on 2020-09-30
I ran the script and here is the output, but it has been stable for the last few days, maybe the problem doesn't exist too much?

I saw on that link that there was a broadcom guide, maybe I'll have a look at that.

```

########## wireless info START ##########

Report from: 27 Sep 2020 12:51 NZDT +1300

Booted last: 27 Sep 2020 00:00 NZST +1200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	20.04
Codename:	focal

##### kernel ############################

Linux 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: ASUSTeK Computer Inc. Eee PC 1015PX [1043:8468]
	Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: AzureWave BCM4313 802.11bgn Wireless Network Adapter [1a3b:2047]
	Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 13d3:3315 IMC Networks Bluetooth module
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
9: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

EFI variables are not supported on this system

##### lsmod #############################

brcmsmac              573440  0
brcmutil               16384  1 brcmsmac
b43                   417792  0
cordic                 16384  2 b43,brcmsmac
mac80211              843776  2 b43,brcmsmac
cfg80211              704512  3 b43,mac80211,brcmsmac
ssb                    73728  1 b43
libarc4                16384  1 mac80211
asus_wmi               32768  0
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
bcma                   65536  3 b43,brcmsmac
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  2 asus_wmi,i915

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
3: wlp2s0b1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp2s0b1' [IF2]> brd <MAC address>
    inet 192.168.20.101/24 brd 192.168.20.255 scope global dynamic noprefixroute wlp2s0b1
       valid_lft 85962sec preferred_lft 85962sec
    inet6 fe80::6868:64f8:9889:fc72/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp1s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0b1  IEEE 802.11  ESSID:"Perisimon"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Perisimon' [AC1]>   
          Bit Rate=39 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:47  Invalid misc:37   Missed beacon:0

##### route #############################

default via 192.168.20.1 dev wlp2s0b1 proto dhcp metric 600 
192.168.20.0/24 dev wlp2s0b1 proto kernel scope link src 192.168.20.101 metric 600 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root         401       1  0 Sep26 ?        00:00:48 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Broadcom Inc. and subsidiaries
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 5.4.0-48-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0b1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               4 (full)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlp2s0b1
GENERAL.IP-IFACE:                       wlp2s0b1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Perisimon
GENERAL.CON-UUID:                       14e7721b-3c9b-464a-b1c5-600f2d565b48
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/20
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     39 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               yes
IP4.ADDRESS[1]:                         192.168.20.101/24
IP4.GATEWAY:                            192.168.20.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.20.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.20.0/24, nh = 0.0.0.0, mt = 600
IP4.DNS[1]:                             192.168.20.1
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        domain_name_servers = 192.168.20.1
DHCP4.OPTION[3]:                        expiry = 1601250263
DHCP4.OPTION[4]:                        ip_address = 192.168.20.101
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_domain_name_servers = 1
DHCP4.OPTION[8]:                        requested_domain_search = 1
DHCP4.OPTION[9]:                        requested_host_name = 1
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[12]:                       requested_nis_domain = 1
DHCP4.OPTION[13]:                       requested_nis_servers = 1
DHCP4.OPTION[14]:                       requested_ntp_servers = 1
DHCP4.OPTION[15]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_root_path = 1
DHCP4.OPTION[17]:                       requested_routers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_subnet_mask = 1
DHCP4.OPTION[20]:                       requested_time_offset = 1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       routers = 192.168.20.1
DHCP4.OPTION[23]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::6868:64f8:9889:fc72/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/3
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   14e7721b-3c9b-464a-b1c5-600f2d565b48 | Perisimon

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8152 v2.0 Fast Ethernet (Eee PC 1015PX)
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:01:00.0/net/enp1s0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID                         BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Perisimon                    <MAC 'Perisimon' [AC1]>  Infra  1     2412 MHz  270 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       yes     *      
wayneguest                   <MAC 'wayneguest' [AC4]>  Infra  1     2412 MHz  130 Mbit/s  24      &#9602;___  WPA2       no             
Polk MagniFi Mini-9603.l001  <MAC 'Polk MagniFi Mini-9603.l001' [AC2]>  Infra  1     2412 MHz  130 Mbit/s  22      &#9602;___  --         no             
wayneswireless               <MAC 'wayneswireless' [AC5]>  Infra  1     2412 MHz  130 Mbit/s  20      &#9602;___  WPA2       no             
--                           <MAC '' [AC6]>  Infra  4     2427 MHz  130 Mbit/s  20      &#9602;___  WPA2       no             
Trustpower_2.4GHz_5813       <MAC 'Trustpower_2.4GHz_5813' [AC3]>  Infra  1     2412 MHz  195 Mbit/s  17      &#9602;___  WPA1 WPA2  no             
David                        <MAC 'David' [AC7]>  Infra  6     2437 MHz  130 Mbit/s  17      &#9602;___  WPA2       no             

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

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NetComm 8003.nmconnection]] (600 root)
[connection] id=NetComm 8003 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=NetComm 8003
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Perisimon.nmconnection]] (600 root)
[connection] id=Perisimon | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Perisimon
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

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

phy#0
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp1s0    no frequency information.

lo        no frequency information.

wlp2s0b1  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp1s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlp2s0b1  Scan completed :
          Cell 01 - Address: <MAC 'Perisimon' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Perisimon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000126983d22e
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Polk MagniFi Mini-9603.l001' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Polk MagniFi Mini-9603.l001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000992a169fadd
                    Extra: Last beacon: 236ms ago
          Cell 03 - Address: <MAC 'Trustpower_2.4GHz_5813' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Trustpower_2.4GHz_5813"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000022d4c07a180
                    Extra: Last beacon: 3200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'wayneguest' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"wayneguest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000def0c0f3980
                    Extra: Last beacon: 152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'wayneswireless' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"wayneswireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000def0c08fb90
                    Extra: Last beacon: 612ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000075cef782183
                    Extra: Last beacon: 3700ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'David' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"David"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000ac11db70a55
                    Extra: Last beacon: 2576ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/5.4.0-48-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     14089E4F4C7371630B37861
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
retpoline:      Y
intree:         Y
name:           brcmsmac
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      66:5C:F0:80:40:C6:1B:F1:0F:5C:31:BD:F3:F8:33:17:92:09:6F:D8:
		6B:89:99:CC:72:C3:5D:F1:0B:22:8D:63:CB:47:9C:07:E1:EF:3F:D1:
		50:98:FF:B2:44:62:3D:F9:90:02:D3:CA:9F:A9:CC:0C:5F:A4:DB:31:
		35:89:3A:58:D3:DB:CC:40:7A:8A:99:72:38:3A:B1:1B:CA:27:E2:2B:
		76:91:BC:8D:96:77:63:6B:FC:03:84:39:58:E0:E7:7D:61:AA:A2:60:
		B4:83:2B:33:FA:F1:A6:59:C3:C5:91:77:BF:E6:C7:DF:F3:7F:0C:BE:
		19:49:5B:D7:FB:FF:0C:BA:C9:9D:92:30:4B:82:2F:B8:B0:FD:BA:1E:
		79:36:BB:8E:73:C5:67:B8:09:37:02:81:CC:62:D3:2B:42:C0:03:7E:
		6F:9A:54:4B:B8:9D:94:E2:01:22:24:12:0B:CA:3F:09:67:DD:3B:2D:
		8E:16:C2:42:64:BA:4A:16:79:E2:A8:BC:C0:CD:C6:83:EE:DF:A6:CC:
		09:17:55:B0:3C:A6:A1:4F:23:5A:2E:83:11:E5:32:00:09:89:31:67:
		DA:41:3A:FA:2E:1E:F4:C8:5B:43:10:64:61:07:A5:A8:4B:4B:35:3E:
		6A:53:05:0E:CC:55:2A:49:3C:F7:19:C0:6D:31:5F:45:BB:AC:90:47:
		C7:09:14:7B:E6:1E:D7:78:D5:3A:D2:84:85:FE:82:F4:10:98:B9:EB:
		C9:3F:3E:C5:7F:DA:37:CC:A5:49:A3:39:DE:EF:BA:EB:26:11:6F:FE:
		EA:5A:D5:41:D0:EC:68:94:AD:5E:8D:E4:AA:5A:14:B5:AF:F3:91:4C:
		6A:11:D4:A1:50:9F:E5:8E:E3:F5:76:25:8F:31:8D:07:9B:BC:66:22:
		F1:D0:DE:D1:9A:43:0A:33:C0:C5:E7:A2:B3:D1:E5:CE:EE:2B:57:6C:
		D3:72:5B:FF:54:6C:4F:9D:E5:C5:31:8B:96:35:F0:C5:8B:32:FE:F7:
		D3:A9:17:9E:10:62:8D:5F:CF:DA:0A:04:F0:CB:7C:EC:70:C0:D7:7E:
		DD:3E:D6:53:7A:23:F6:DC:34:16:A4:58:01:86:3D:F1:76:ED:96:B9:
		24:20:5F:25:4C:08:14:26:39:3B:43:94:7E:05:72:E8:3E:AA:3B:42:
		10:F6:EC:41:DB:E6:6F:76:17:B0:AB:94:81:38:39:6F:EF:BC:42:78:
		71:C9:AA:E6:80:8B:65:CC:3A:2A:02:1C:F0:BE:9D:64:C6:53:71:D6:
		22:58:D3:D5:E7:39:A1:EC:DB:54:A4:88:DF:67:24:3E:44:2A:47:B0:
		07:E8:B9:DC:B3:53:28:0B:83:B8:FA:D4

[brcmutil]
filename:       /lib/modules/5.4.0-48-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     B3F119D70FB75A37C52A13E
depends:        
retpoline:      Y
intree:         Y
name:           brcmutil
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      6D:21:0A:87:B2:4B:10:30:39:FF:75:9C:B4:BE:89:7C:11:19:14:93:
		5E:89:20:D7:3B:55:9F:1F:17:A5:FF:0A:29:B9:C1:13:86:3E:0F:03:
		8D:8A:74:D1:AC:C7:F9:BE:18:55:44:35:C0:04:FC:15:14:E2:BF:8A:
		B7:E2:C4:FE:CE:E7:07:10:FA:20:AF:2B:F9:E9:CE:CA:E4:A5:C4:9B:
		EC:D7:E2:85:25:02:0C:AC:A9:60:54:77:E0:69:5F:FD:E4:F8:29:1B:
		20:85:8C:4E:AF:09:C8:AA:44:8B:E9:06:C5:DB:54:83:1A:3A:46:47:
		F6:9F:49:E1:4E:95:51:4D:2B:CC:E0:47:71:78:02:C6:5F:E5:EB:8F:
		8F:63:D9:E9:2B:E5:01:35:78:B7:B2:17:2C:E0:5F:A8:A0:28:42:9D:
		F0:39:7C:6A:4F:98:32:00:C7:B5:17:50:0D:05:FE:E9:4B:1E:07:BB:
		C6:42:A9:48:AF:A8:CA:22:49:DC:50:C2:96:2A:13:2C:BA:4B:B3:62:
		FE:0E:F5:C6:D5:6C:59:BA:AB:D2:81:5E:6E:66:BB:3E:51:73:96:3F:
		72:11:F7:74:C9:52:23:7A:6C:A7:9A:32:12:02:0C:A9:C5:DE:07:1C:
		68:D7:65:01:A4:BF:DB:0E:D5:5B:D7:BC:A3:FB:45:86:43:4C:2D:66:
		58:EE:CD:C5:5D:ED:63:0F:27:83:E3:59:00:2B:C9:D5:3B:F0:6D:26:
		6E:FB:21:89:26:4F:A2:B7:D2:B9:BA:9D:23:4B:42:CB:B2:D9:7A:F3:
		4C:59:69:88:AD:02:7A:07:B7:9A:46:99:0F:6E:34:0D:D7:77:8C:94:
		4B:E7:89:5D:9D:C5:68:3E:AA:A9:11:B8:31:A4:8F:CF:6C:76:46:2C:
		F4:D9:CC:27:A1:11:15:05:21:9B:DE:CD:F9:87:8D:89:67:C4:9A:7D:
		EE:E3:BA:E2:09:00:20:41:E6:B8:08:93:54:B8:86:69:86:78:3A:C0:
		59:ED:13:65:EE:31:D7:3A:68:51:55:46:42:D2:2E:09:51:18:08:D4:
		4A:86:8E:01:01:8C:EF:42:BA:8B:38:C0:9C:B8:64:82:34:BF:68:90:
		B4:53:62:DC:D8:09:9D:29:7E:0E:C0:0E:40:1A:08:F0:61:C9:92:AA:
		9F:A6:F8:1C:53:F2:1C:0A:32:B9:F8:23:3C:DD:28:B2:44:D3:AB:F4:
		B6:2A:73:DC:6B:98:92:B7:5A:81:1C:D1:CA:C6:7F:4E:6B:73:4F:F8:
		F6:13:E4:4E:02:CE:17:83:F7:B4:B9:F9:1E:8B:F8:3C:8D:64:E5:D9:
		9A:7F:D5:B3:06:43:1D:72:37:2E:D4:89

[b43]
filename:       /lib/modules/5.4.0-48-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode42.fw
firmware:       b43/ucode40.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode30_mimo.fw
firmware:       b43/ucode33_lcn40.fw
firmware:       b43/ucode29_mimo.fw
firmware:       b43/ucode26_mimo.fw
firmware:       b43/ucode25_mimo.fw
firmware:       b43/ucode25_lcn.fw
firmware:       b43/ucode24_lcn.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode16_lp.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     4FA93F2524656CE354CBF84
depends:        mac80211,ssb,bcma,cfg80211,cordic
retpoline:      Y
intree:         Y
name:           b43
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      77:D2:A0:FA:12:6A:44:AB:D2:0A:B8:62:92:9C:75:37:84:4F:9D:35:
		FD:94:3A:47:8B:DA:68:AF:C9:B3:51:7A:FE:9E:B9:0E:8B:4D:F7:73:
		AC:B6:F8:07:E7:D4:65:8A:A1:97:3E:BB:60:AB:51:65:B0:36:CB:CE:
		07:CC:02:5D:DD:A7:70:B3:89:C2:A7:A6:31:33:F6:50:C6:39:81:F7:
		6A:6B:35:0A:E6:D5:FB:A3:89:C3:54:3E:0F:98:2C:08:D2:07:83:A7:
		38:3A:F2:5F:91:65:1B:79:D8:50:79:A7:36:55:CA:B7:16:7E:7D:8A:
		A8:AC:9B:1E:A5:16:C3:CD:48:79:87:B2:23:DF:C0:2B:2F:99:F9:5C:
		DC:E1:98:3C:0B:E3:03:4D:56:8C:11:F6:3B:53:C4:60:C8:86:B1:9E:
		89:A7:14:69:62:E2:D4:2E:C8:3B:33:5A:25:A5:BE:A2:ED:7D:7B:09:
		6A:FA:2E:B5:EF:0A:2B:96:9D:64:CA:55:D0:C6:6B:89:5D:3F:8A:F3:
		28:08:2D:85:1E:46:4F:75:27:D9:1C:86:61:AA:04:E9:46:7D:EE:05:
		12:57:56:7A:0F:31:28:8E:B2:73:9C:7C:4B:05:6B:B1:E6:9A:F0:C8:
		65:A0:00:D2:8C:4F:34:42:36:8B:82:9D:A0:C8:C6:08:2C:97:73:FA:
		99:AE:F1:13:9B:88:C6:C2:36:8E:FD:0F:C6:9B:23:83:5F:3A:72:B7:
		21:63:6D:29:F3:41:29:E8:D0:15:0B:93:14:20:8C:69:A5:F6:3D:76:
		83:74:AC:1E:78:3F:8A:98:C5:E8:8F:71:74:6B:51:AB:7B:60:64:D5:
		B4:9F:1D:B5:01:38:0B:C2:DD:C3:18:3E:86:D6:7A:F6:B5:30:70:75:
		10:6D:D1:89:D6:B8:A6:84:89:72:79:77:75:4C:D3:47:D8:D9:1E:69:
		A1:89:39:F9:99:6C:7F:61:FB:3C:8F:77:57:B7:0B:55:CE:5E:8D:26:
		0A:C7:0A:30:96:F5:73:BF:BC:B3:64:29:52:F3:92:26:14:67:68:90:
		26:10:C0:EA:F0:A2:AB:99:24:ED:44:DF:2E:7B:23:6C:93:72:9E:66:
		DD:6E:6F:DE:02:65:D8:FB:23:47:E8:E9:5D:28:DA:CB:85:1B:BA:1B:
		DE:81:EB:8B:9E:5D:3F:92:50:91:50:95:72:71:8C:E1:EA:1D:D1:87:
		00:03:63:4D:C9:02:2D:FE:5B:3B:20:AA:89:E9:A8:11:C3:B6:94:B3:
		36:67:1F:78:8D:E4:B6:BF:DD:75:4B:A1:CA:67:92:6F:00:81:1F:D0:
		18:79:3F:C0:13:29:CE:64:2C:6C:8B:22
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/5.4.0-48-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FAB28EB495445A127E0CC46
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      48:44:E5:3D:AE:1B:AC:D8:69:05:F4:BE:C2:E9:98:22:FC:7F:82:E7:
		8F:2E:42:5A:85:67:BA:A6:2D:66:F1:9B:5D:A2:69:EE:3E:77:5C:60:
		59:9B:A0:62:3D:C7:99:D1:07:7E:D0:AF:6C:30:1F:4E:03:79:D9:D7:
		99:3B:88:3B:CC:C2:4B:CC:0F:AB:5B:1D:0F:F0:55:A5:8A:F8:5C:10:
		B6:88:63:65:56:36:48:D7:12:D6:CC:77:64:B7:C0:17:D9:EF:45:E0:
		EE:CF:FF:E6:CC:16:DC:1F:A0:76:56:F6:CF:85:CB:15:40:A5:3E:DD:
		47:02:A4:BB:FF:23:B5:20:E1:BF:80:52:AD:5E:7D:C6:9D:2E:3F:10:
		E0:AD:00:09:8F:96:15:6A:08:8C:1D:97:23:A9:39:67:DB:5D:EF:59:
		3D:B9:61:71:9E:70:EB:A6:49:A1:C6:57:58:A3:86:CC:73:B7:0A:E3:
		5F:3B:26:2D:06:6F:15:3C:16:7B:A0:92:0A:5D:7B:70:A7:D9:9F:7F:
		EB:6B:C5:93:B8:77:A5:FC:B6:43:34:98:94:B1:7B:A5:FE:13:37:E9:
		20:09:B0:46:6D:DA:C8:2B:69:4B:D1:F3:D4:25:25:80:41:D0:20:C9:
		AD:9F:4F:86:62:3C:6F:E2:A1:28:F9:4A:CF:2E:C0:28:42:05:9F:19:
		2E:92:6B:8B:77:F3:FF:5A:DF:91:00:85:D5:43:D6:6B:77:0B:04:C8:
		4A:E7:70:98:18:05:F8:D6:D4:B2:E4:4B:AF:6F:0E:86:1A:F0:B4:F3:
		77:E7:68:DA:56:F2:D2:EE:EE:6F:01:4A:D5:C5:45:71:18:04:7F:18:
		FE:FC:2B:04:47:14:DE:50:1F:E2:BF:55:07:F2:5A:4D:41:BB:0C:4F:
		1A:71:E0:7A:18:0D:48:CA:CF:1D:C6:63:4A:3D:CD:08:8B:A8:6A:A2:
		EF:51:95:73:BC:64:F4:6F:0F:9D:57:C7:DE:97:A5:ED:17:A4:E6:9E:
		EA:89:33:A5:E6:A7:2F:FC:AE:FE:3C:9D:35:2F:71:F3:1A:72:AA:9E:
		DE:22:5C:8E:54:F5:B2:BC:A8:F6:60:B0:08:9B:EB:CF:34:77:F5:75:
		32:96:A1:07:DD:8E:3D:2E:34:36:05:B0:0D:0E:2B:3D:2A:27:A7:42:
		0A:C2:FA:16:AA:BD:85:B5:46:AC:C8:26:D1:F7:2B:41:0E:8F:83:29:
		22:AF:E3:C3:E0:3B:C9:04:E0:25:C6:2B:C3:F4:7F:31:35:DA:EB:9F:
		3A:D0:D2:8F:CD:49:EE:B7:A3:93:D0:57:57:32:65:59:F0:FB:3A:88:
		5E:94:BA:FB:10:11:56:D7:32:F5:7A:A7
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.4.0-48-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     548020DDB9CC1C141282FF4
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      34:CF:4E:69:17:36:90:E5:63:7D:72:3F:10:A5:98:E7:86:13:E0:59:
		E2:66:4A:D0:B3:7F:3E:F8:99:38:8E:20:70:D7:25:E9:CF:23:F4:6A:
		D7:B4:16:06:D1:2C:5B:CA:BF:5D:D4:30:07:17:6B:1E:5D:2A:58:57:
		03:00:78:82:38:46:07:81:4D:45:46:EB:E7:A4:AA:07:0F:54:4F:B3:
		58:4F:E0:0C:2A:5A:B0:9C:C9:52:91:A3:1E:E0:D3:28:C6:BA:30:CC:
		46:AE:03:4C:6F:3D:65:8E:30:5B:82:F4:C6:B7:C0:0D:C4:98:3B:71:
		CE:DE:B2:3E:D1:B9:0B:90:8E:F6:29:4C:6D:9E:B5:65:62:76:DA:9E:
		E2:A0:58:54:CA:37:68:0A:93:8E:51:3F:4D:89:09:71:52:19:19:36:
		98:D8:79:71:BF:F3:A0:D9:C1:C4:8E:24:6C:92:AE:5C:2A:4F:9B:42:
		FE:C7:EA:09:7A:70:72:DF:DF:2E:EA:C7:F1:CC:52:B0:67:96:4F:46:
		72:B0:9F:1C:CE:81:29:87:C2:63:7E:6F:87:42:BB:76:00:BC:32:C3:
		C4:13:2D:B3:AB:D5:56:21:49:26:E9:3A:DA:C9:46:C6:9D:18:EB:CD:
		98:9C:03:83:48:57:5F:8A:E0:FF:1E:4D:B6:20:D4:56:D7:24:57:D5:
		84:CE:DF:A5:4A:AD:93:B8:F8:FF:9C:A5:76:F7:75:A8:3F:FF:54:61:
		E5:BC:FE:C2:D6:33:98:E3:00:81:40:6A:26:9D:59:B4:33:3F:EC:C8:
		EA:38:46:51:E3:8C:49:E1:8D:14:A6:4C:F6:34:A1:BC:E2:FB:CE:65:
		2E:E0:AF:E1:9F:3A:72:14:74:8B:32:35:A1:23:FA:A2:93:E5:BB:19:
		6A:28:F6:22:53:D9:15:73:08:B2:64:BD:96:54:40:75:6F:26:8F:F2:
		94:8E:4E:00:73:D9:A8:50:D6:2C:CD:58:E6:56:21:05:10:41:C7:FF:
		1C:D8:F0:40:D0:50:38:9B:0C:34:A9:FA:95:F9:44:01:A3:44:B6:5A:
		66:45:B1:DE:36:9A:A8:DA:B9:42:C8:B6:2F:1A:E8:F6:1D:A0:18:61:
		AC:E9:20:C4:5F:E6:A1:DD:9F:DA:64:35:A2:56:EC:24:C4:B3:0C:9A:
		AD:2D:36:C4:2E:46:1B:54:26:10:D5:3B:1F:58:57:31:92:4B:60:C1:
		8F:41:17:7C:07:D3:9B:AD:23:71:AC:5F:26:4C:54:FE:13:AE:90:97:
		1C:EA:EE:7A:D8:4E:FD:59:CF:AB:8C:55:89:EF:B9:22:9A:BF:3D:72:
		C1:E8:0C:3B:7A:53:DA:C8:8D:8E:BC:7B
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/5.4.0-48-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     571863F88D3D9D6896EF515
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      BE:50:5D:1C:14:F5:43:43:1E:FF:E0:13:34:FB:BA:D2:04:F0:CA:19:
		F9:13:38:27:7D:79:02:25:5E:E2:A1:EC:3E:0F:E1:5D:2A:50:90:A9:
		B7:8D:47:B3:78:27:24:C5:A7:F5:D6:0C:54:53:08:F5:39:CD:05:F7:
		01:A5:A0:60:8C:C0:EF:E9:44:C6:A2:69:EE:BF:90:AF:51:26:51:2B:
		21:03:CB:46:97:6E:DB:11:88:62:F9:87:4D:49:B0:97:45:75:95:97:
		83:06:C6:C6:37:97:61:29:D3:B7:30:62:5A:7C:FA:A6:AA:04:9B:47:
		98:DA:7C:C1:6C:50:7C:A6:36:66:B2:64:C2:AF:1C:20:76:AC:25:53:
		FC:D8:1A:0A:71:FE:94:66:9F:79:8C:5B:8B:81:3E:5B:10:F8:99:34:
		B9:1E:9E:42:37:9C:3D:B3:DB:85:1E:6A:C0:8D:CE:84:F1:34:D6:D2:
		BC:B0:C7:37:6D:99:CF:F7:50:A9:7D:E3:68:FF:67:56:18:E1:37:76:
		44:37:49:EE:C7:E1:AE:17:CD:A2:A5:26:66:24:71:ED:76:2E:81:7B:
		A7:5B:0E:F7:B8:5E:D5:58:A9:15:F8:FF:17:A3:DD:E0:14:DF:E6:CD:
		F6:A3:D0:FD:8E:31:1D:06:0F:B6:0C:66:BA:10:B2:42:54:51:5C:AD:
		D8:32:35:27:58:BC:40:9F:6B:73:BC:EE:8D:27:DF:C6:4B:B3:E2:D0:
		2C:47:06:E8:E4:80:AE:91:FA:DA:45:FB:9D:6F:E7:F0:A1:C3:83:FC:
		C1:28:DA:3A:15:AD:E3:9E:83:3F:77:2E:F2:49:3A:06:9B:57:9E:08:
		63:A8:DD:98:E1:D3:BC:D1:63:11:AF:C2:AD:94:B3:8A:D7:17:4F:3D:
		BD:54:BF:BB:4A:08:34:5D:54:C0:8E:0C:E2:96:2C:74:23:26:4D:83:
		A7:B8:2E:34:9F:23:6C:18:CA:A8:20:79:01:C0:F1:16:09:E6:4E:D6:
		FF:0F:6A:14:DF:BE:87:B7:20:FB:AA:B1:A8:96:F5:C1:F8:E2:D3:52:
		40:2D:F1:87:EC:C7:AB:D2:A3:7B:55:06:81:0B:82:B5:B0:EC:E5:B5:
		09:13:2B:5F:92:83:51:3E:E3:E4:B7:3F:47:4C:7D:2B:CD:B1:B0:1B:
		0B:44:9B:1D:DE:C7:04:2E:39:76:2F:A0:63:29:09:F2:99:76:3F:6E:
		F5:32:E3:16:29:62:C5:40:F1:E6:AD:C8:C5:9F:0A:69:69:EC:3C:F0:
		21:CB:28:ED:E3:01:9D:88:70:C9:14:D6:CC:B1:9F:5C:C8:6B:BB:25:
		C1:D6:92:B8:B0:15:AF:2B:96:1F:39:DD

[bcma]
filename:       /lib/modules/5.4.0-48-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     28BC6D6DBB15EC3F0F53EA3
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       5.4.0-48-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        69:0F:B2:8C:24:82:6C:28:AB:28:F7:D2:E5:B8:D0:0B:2C:EF:1F:87
sig_hashalgo:   sha512
signature:      CD:2C:B3:16:F7:E4:2D:8A:8E:31:9E:75:D1:0C:03:64:9E:77:FA:43:
		A0:ED:8A:0A:5E:42:AF:B1:61:19:BC:14:7E:60:F7:DD:A8:26:B0:06:
		8E:40:32:1D:3E:4E:F4:90:AF:32:D6:1E:FD:6D:BA:0F:A8:C2:47:F4:
		20:1D:C8:B3:87:14:ED:BF:3E:54:48:58:74:23:C3:41:B9:DA:7A:5B:
		7E:F1:3F:DE:D3:02:F2:EB:37:20:87:8A:48:2A:E9:20:7C:53:B8:90:
		78:18:B4:53:E3:92:A5:9C:AC:A5:6A:F3:CF:96:AB:6A:71:68:E9:D8:
		63:0F:16:DC:5F:C3:21:31:EB:37:99:51:EE:81:F2:2F:D1:2A:47:C3:
		46:87:25:5B:D7:47:99:B9:5E:BE:2D:69:B4:D3:79:E3:31:50:78:FF:
		C7:A1:1F:AA:A7:9C:0B:EC:59:F7:4A:D6:8F:F8:3C:1E:4D:7E:EF:38:
		1B:D5:F8:FE:5A:4D:1E:67:17:62:FC:2A:2F:29:63:42:BD:37:81:6B:
		5E:E8:80:04:DD:D4:2A:7F:99:F8:C5:E4:B4:A7:C6:36:8E:32:91:2F:
		85:05:F0:C6:3B:79:85:4E:00:C8:DF:71:01:6B:30:7F:7D:A7:7B:03:
		51:B0:9C:AC:9E:22:58:AF:17:89:6C:87:63:6A:92:0A:BD:BF:D7:EC:
		E1:48:A7:FE:24:FB:54:91:17:7F:F1:94:A1:A2:EB:01:EB:02:8C:6E:
		65:30:16:6B:69:A6:D9:54:82:29:FF:B5:7A:19:DE:ED:86:47:A3:B8:
		D5:83:14:4F:1B:CB:91:80:21:62:65:37:02:95:70:9F:67:BA:C9:14:
		B1:C2:C3:23:5D:07:62:08:B0:14:21:A6:41:89:F4:D7:40:AD:3D:FD:
		27:72:C4:F7:AC:A7:46:94:C7:89:97:09:95:1F:03:5D:81:A4:4C:93:
		76:17:7B:DD:F4:51:E6:D1:55:57:A1:11:13:E0:7A:D9:21:61:45:22:
		28:9E:B7:B1:D7:17:75:EA:2A:B0:14:48:74:AE:1B:55:95:59:AE:73:
		4E:9A:EA:76:F4:34:D4:69:E4:69:4B:40:BD:26:9C:95:C5:5E:25:76:
		CF:22:8F:CD:50:74:DD:85:C7:4E:CD:97:16:E9:7D:A9:D0:F9:68:D7:
		0B:78:91:91:37:EC:CE:9C:F6:4A:3D:37:FD:CB:6D:42:46:91:FA:C5:
		F3:EC:17:E0:83:49:AA:4D:E6:BF:A1:A6:68:D9:6B:7E:30:EA:DF:60:
		7E:E6:1B:EE:37:22:F7:EB:21:B2:FA:E0:39:80:F6:CF:57:86:AF:CB:
		76:DE:19:76:70:56:B5:8C:2C:02:F9:3A

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[29595.355428] wlp2s0b1: send auth to <MAC 'Perisimon' [AC1]> (try 1/3)
[29595.357045] wlp2s0b1: authenticated
[29595.360187] wlp2s0b1: associate with <MAC 'Perisimon' [AC1]> (try 1/3)
[29595.364994] wlp2s0b1: RX AssocResp from <MAC 'Perisimon' [AC1]> (capab=0x431 status=0 aid=4)
[29595.365541] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[29595.365560] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[29595.365615] wlp2s0b1: associated
[29596.557463] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0b1: link becomes ready
[29596.816929] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[31410.911523] wlp2s0b1: deauthenticating from <MAC 'Perisimon' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[31410.914276] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[31410.914362] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[31410.914368] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[31411.816212] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[31411.816798] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[31411.816825] brcmsmac bcma0:1: brcms_ops_bss_info_changed: cqm change: threshold -70, hys 4  (implement)
[31411.816848] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[31411.816851] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[31413.491636] wlp2s0b1: authenticate with <MAC 'Perisimon' [AC1]>
[31413.491960] wlp2s0b1: send auth to <MAC 'Perisimon' [AC1]> (try 1/3)
[31413.493535] wlp2s0b1: authenticated
[31413.496198] wlp2s0b1: associate with <MAC 'Perisimon' [AC1]> (try 1/3)
[31413.500241] wlp2s0b1: RX AssocResp from <MAC 'Perisimon' [AC1]> (capab=0x431 status=0 aid=1)
[31413.500764] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[31413.500780] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[31413.500789] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[31413.500836] wlp2s0b1: associated
[31414.986710] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[31414.991469] wlp2s0b1: deauthenticating from <MAC 'Perisimon' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[31414.994545] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[31414.994570] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement) (repeated 2 times)
[31415.610817] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[31416.777600] wlp2s0b1: authenticate with <MAC 'Perisimon' [AC1]>
[31416.777889] wlp2s0b1: send auth to <MAC 'Perisimon' [AC1]> (try 1/3)
[31416.779443] wlp2s0b1: authenticated
[31416.784198] wlp2s0b1: associate with <MAC 'Perisimon' [AC1]> (try 1/3)
[31416.788328] wlp2s0b1: RX AssocResp from <MAC 'Perisimon' [AC1]> (capab=0x431 status=0 aid=1)
[31416.788906] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[31416.788918] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[31416.788949] wlp2s0b1: associated
[31417.202720] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0b1: link becomes ready
[31417.451705] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

########## wireless info END ############


```

---

### Post by jeremy31 on 2020-10-01
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) and see if that helps

---

### Post by TygerTung on 2020-10-01
Thanks I have implemented those suggestions and will monitor for stability going forward.

---

### Post by TygerTung on 2020-10-06
The internet connection stopped working again this morning; unable to connect to page error, so I went down to the wifi icon and it was only detecting the network which I was connected to Perisimon, however I clicked on Perisimon to reconnect to it, and that failed and no networks were detected. I had to do a hard reset to get the wifi working again.

I ran the script prior to restarting, although I don't know if it makes any difference to the output.

Is there any way to reset the wifi module software without resetting the whole computer?

Cheers,

Sam

---

### Post by chili555 on 2020-10-06
```
brcmsmac              573440  0
brcmutil               16384  1 brcmsmac
b43                   417792  0
cordic                 16384  2 b43,brcmsmac
mac80211              843776  2[COLOR="#FF0000"] b43,brcmsmac[/COLOR]
cfg80211              704512  3 b43,mac80211,brcmsmac
ssb                    73728  1 b43
libarc4                16384  1 mac80211
asus_wmi               32768  0
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
bcma                   65536  3 b43,brcmsmac
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  2 asus_wmi,i915
```Please see Special case #1 here:  [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by TygerTung on 2020-10-06
Thanks, I did that and the ethernet still seems to work, so I'll see how it goes. It's a nuisence having to reset the computer all the time so it would be nice if the wifi was stable.

---

### Post by TygerTung on 2020-10-06
The wifi failed again, no wifi networks detected. Is there any way to reboot the wifi module without rebooting the whole system? If there was a command I might be able to write a script somehow and have it on my desktop to double click each time the wifi failed.

---

### Post by jeremy31 on 2020-10-07
You could try ```
systemctl restart network-manager.service
```
Any chance the wifi router is set to auto channel?  Broadcom wifi on Linux usually won't find access points on 2.4GHz higher than channel 11

---

### Post by TygerTung on 2020-10-07
Thanks, it just failed again now so had to restart the computer. Will try that next time it fails.

No, I changed the channel to 1 as suggested in the above guide.

If the script doesn't work, maybe I'll have to upgrade to 16.04?

---

### Post by SeijiSensei on 2020-10-08
> **TygerTung said:**
> Is there any way to reset the wifi module software without resetting the whole computer?
Maybe removing then reinserting the Broadcom module might work.
```

sudo modprobe -r brcmsmac
sudo modprobe brcmsmac

```

---

### Post by jeremy31 on 2020-10-08
> **TygerTung said:**
> Thanks, it just failed again now so had to restart the computer. Will try that next time it fails.

No, I changed the channel to 1 as suggested in the above guide.

If the script doesn't work, maybe I'll have to upgrade to 16.04?

Based on the wireless script results, I would have recommended channel 11, but those other APs may have switched channels

---

### Post by TygerTung on 2020-10-08
Thanks for the hint. Will try that and the other command next time the wifi blows up.

---

### Post by TygerTung on 2020-10-11
I tried those commands:

```
systemctl restart network-manager.service

sudo modprobe -r brcmsmac
sudo modprobe brcmsmac

```

But unfortunately they were unable to restart the wireless module. All they did after running them a few times in a few different orders was to close the nm-tray programme and I couldn't work out a way to load it up again. There may be a terminal command I could use, but not sure what it was and since the machine couldn't get on the net, I couldn't look it up.

Does anyone know some other commands I might try.

The error seems to occur more frequently when the machine is suspended (lid closed).

---

### Post by TygerTung on 2020-10-22
This command works:

```
sudo service network-manager restart
```

So will just use that.

---


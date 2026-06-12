---
title: "Wifi won't fully authenticate with network (included wireless-info.txt results)"
date: 2019-11-17
forum: Networking &amp; Wireless
---

### Post by theflashman on 2019-11-17
I successfully installed Ubuntu on my Asus TUF gaming laptop. I am dual-booting with windows 10 where wireless works perfectly. No other linux distro has worked with wireless out of the box for installation. After installing, wireless worked and allowed me to update and upgrade the system. After rebooting, I am able to find wireless networks and attempt to connect to them. The problem is that it won't actually connect and keeps asking me to type in the wireless password. I know for sure that it's correct, I tried it on both 2.4 and 5GHz channels, I verified the password in the GUI networking utility, I have attempted to connect via nmtui, and rfkill list confirms that nothing is being blocked.

My wireless networking card is "Realtek 8822BE Wireless LAN 802.11ac PCI-E NIC".

The results of the wireless-info script are:
```


########## wireless info START ##########


Report from: 17 Nov 2019 11:36 MST -0700


Booted last: 17 Nov 2019 00:00 MST -0700


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan


##### kernel ############################


Linux 5.3.0-19-generic #20-Ubuntu SMP Fri Oct 18 09:04:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:208f]
    Kernel driver in use: r8169


04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822]
    Subsystem: AzureWave RTL8822BE 802.11a/b/g/n/ac WiFi adapter [1a3b:2950]
    Kernel driver in use: rtw_pci


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 060f:4276 Joinsoon Electronics Mfg. Co., Ltd Black Web HDD
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 2109:8110 VIA Labs, Inc. Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3526 IMC Networks Bluetooth Radio 
Bus 001 Device 006: ID 2f68:0082 VIA Labs, Inc.          USB2.0 Hub             
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 2109:2811 VIA Labs, Inc. Hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


mac80211              851968  2 rtwpci,rtw88
cfg80211              712704  2 mac80211,rtw88
libarc4                16384  1 mac80211
asus_nb_wmi            28672  0
asus_wmi               32768  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  1 asus_wmi


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: wlp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp4s0' [IF2]> brd <MAC address>


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp4s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


    NetworkManager


Running:


root       937     1  0 11:30 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8822BE 802.11a/b/g/n/ac WiFi adapter
GENERAL.DRIVER:                         rtw_pci
GENERAL.DRIVER-VERSION:                 5.3.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp4s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.7/0000:04:00.0/net/wlp4s0
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
WIFI-PROPERTIES.MESH:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1,/org/freedesktop/NetworkManager/Settings/3
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d295cc69-598b-478e-a2ec-d92120183fc7 |  Wifi 5GHz 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   0ef28369-d40a-425b-8d37-6c8a430fd340 | Wifi 2.4 GHz


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/net/enp2s0
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID                           BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
Wifi 2.4 GHz          <MAC 'Wifi 2.4 GHz' [AC2]>  Infra  1     2412 MHz  130 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2      no             
Wifi 5GHz             <MAC 'Wifi 5GHz' [AC4]>  Infra  149   5745 MHz  270 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2      no             
DIRECT series  <MAC 'DIRECT series' [AC1]>  Infra  1     2412 MHz  65 Mbit/s   60      &#9602;&#9604;&#9606;_  WPA2      no             
Telus                      <MAC 'Telus' [AC3]>  Infra  11    2462 MHz  270 Mbit/s  29      &#9602;___  WPA2      no             


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


[[/etc/NetworkManager/system-connections/Wifi 5GHz 1.nmconnection]] (600 root)
[connection] id= Wifi 5GHz 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Wifi 5GHz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wifi 5GHz.nmconnection]] (600 root)
[connection] id=Wifi 5GHz | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Wifi 5GHz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wifi 2.4 GHz.nmconnection]] (600 root)
[connection] id=Wifi 2.4 GHz | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF2]> | mac-address-blacklist= | ssid=Wifi 2.4 GHz
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/Edmonton (based on set time zone)


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


phy#0
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


wlp4s0    32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
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


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.745 GHz


wlp4s0    Scan completed :
          Cell 01 - Address: <MAC 'DIRECT-EB-HP ENVY 7640 series' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-EB-HP ENVY 7640 series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ccde0989db
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Wifi 2.4 GHz' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Wifi 2.4 GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004b9440ef9
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Telus8147' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Telus8147"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000050728a5af60
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC ' Wifi 5GHz' [AC4]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:" Wifi 5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004b87d3887
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[mac80211]
filename:       /lib/modules/5.3.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E5BAEB02C080FB4E3226D5B
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.3.0-19-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4C:2A:AE:F3:CD:F9:F6:83:8D:98:BF:7B:A3:C7:B1:82:B3:DC:38:84
sig_hashalgo:   sha512
signature:      0E:C3:BC:E6:33:52:92:02:E8:45:F8:A5:2B:02:06:F1:7C:44:F5:6A:
        75:55:27:7E:64:AE:DD:35:8E:A2:12:11:62:C2:4F:42:20:1D:D0:4B:
        8E:42:27:1E:DE:17:FB:E0:36:9A:F0:23:77:A5:32:71:22:12:D3:FC:
        CB:E2:5C:8A:01:57:92:8F:FB:CF:35:4A:0F:BD:84:4F:36:32:F8:7A:
        BA:E0:F9:A9:37:70:BE:D2:B3:F3:E5:C7:C6:97:1E:1B:44:54:63:3D:
        93:BF:B2:68:FC:B6:B2:81:4F:DC:62:9B:90:4C:53:D4:E8:B3:9D:13:
        26:23:0E:B6:3B:9F:F9:E0:D2:48:8F:81:26:38:39:83:BB:8E:6F:4C:
        A2:65:FA:88:C5:99:CB:0A:0E:BE:B2:6D:AD:07:FA:BB:51:C9:4C:F6:
        81:74:90:E0:7E:F9:3A:5D:24:F1:A0:5D:8A:31:C4:0B:66:87:4D:98:
        E5:98:E9:CA:7D:37:67:EC:6C:E5:9F:72:2E:48:0C:03:FF:B9:4B:BD:
        82:18:84:4C:24:37:0A:F6:AB:3A:09:26:73:9F:6D:BE:5A:8A:06:0C:
        7B:EF:13:CE:1A:69:20:47:3D:70:4F:81:43:BB:EF:41:2D:99:D7:CC:
        3D:6A:51:81:6D:E0:15:31:99:66:92:55:8C:30:19:0B:C2:79:FB:47:
        E9:85:CB:30:26:35:ED:48:DA:F1:45:BA:88:B5:96:F0:F5:C6:2D:A4:
        0C:5E:A4:3A:B3:81:07:6B:0F:C9:EF:91:B1:28:73:50:24:32:E9:5D:
        60:8E:3B:9A:E0:37:21:0A:85:9A:B1:C1:1A:8A:53:91:EC:26:3F:8E:
        59:13:40:08:A9:22:41:A2:62:22:4F:31:77:36:0D:FA:4B:71:96:A9:
        3F:AC:C8:0D:F9:B1:EF:01:C9:7C:A2:2C:6D:C4:82:78:54:F8:60:5D:
        59:46:91:06:82:2F:66:B3:1E:DE:CF:BE:F7:5E:64:C4:68:E8:FD:D7:
        44:A4:C9:D4:B6:A9:25:E7:58:9B:35:E7:C7:CB:14:B1:CD:B4:55:9B:
        E0:84:7D:60:F1:7D:EC:AC:42:EF:DD:A4:19:66:54:EB:C6:7B:F3:85:
        AE:6C:C8:AA:AF:13:27:0D:07:7A:E2:6E:C6:C4:49:3A:05:93:8F:F2:
        D6:94:62:F7:03:E5:8E:EF:3B:C0:C0:DD:CF:C4:A5:1C:48:BF:25:F9:
        2B:FE:5B:7B:ED:EC:41:57:D8:51:C9:1D:5C:22:7C:0A:A8:A7:98:DB:
        B8:AB:88:CE:BF:96:B2:1C:31:2D:F0:4D:C6:89:09:AF:66:05:95:62:
        37:AD:0F:CF:D1:C7:84:0D:7B:DC:B7:BE
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/5.3.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     B40A287A6D5CAB8457D0FD4
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.3.0-19-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4C:2A:AE:F3:CD:F9:F6:83:8D:98:BF:7B:A3:C7:B1:82:B3:DC:38:84
sig_hashalgo:   sha512
signature:      7C:80:DD:FA:5A:E6:D3:1C:16:2B:55:49:A2:7D:3B:81:4A:B4:15:6D:
        33:55:14:7A:2B:73:EC:7C:32:D4:0D:01:26:E1:FA:50:F6:53:FE:B1:
        E9:07:8D:CB:3E:FC:04:3C:8D:81:A0:9C:9E:ED:CE:8E:7E:79:4B:C0:
        AD:35:48:5D:9A:4C:6A:FD:A4:CC:2A:F2:A9:FF:8D:7B:98:F3:47:3C:
        DD:EA:6D:30:78:32:9B:EC:D5:BD:B1:22:D2:7A:E5:7A:E5:93:A2:07:
        7B:B0:CE:F5:CD:02:09:42:EB:1A:07:B1:7C:BA:E8:37:DC:3F:A3:9A:
        B0:E5:F0:5D:97:24:F8:29:43:60:DD:AC:9C:9E:E8:89:A7:9A:B6:3F:
        2E:9E:CB:F8:74:AC:CD:28:DE:4B:57:58:DD:92:4A:B4:95:75:95:B3:
        9D:2E:E0:EF:84:15:1C:56:1A:D3:2E:96:B4:84:A4:96:81:F9:FF:23:
        A6:B4:AD:98:D7:C4:77:7A:4D:90:2E:D2:A5:36:B3:0F:8E:67:0A:FA:
        FB:5D:22:DA:F0:C3:37:E5:10:A5:47:EE:3A:F1:25:40:63:86:E4:93:
        A6:57:A9:51:9D:2E:F0:61:B8:D2:15:D4:60:96:D7:31:66:A9:C1:A0:
        BC:5D:BA:B3:8D:8E:87:F1:A0:79:2D:F4:81:2C:CA:1E:0B:30:41:53:
        63:83:7C:D4:55:BA:01:F6:98:58:73:20:FF:D9:F2:00:6E:E7:E0:54:
        E5:33:6F:3C:1B:89:34:47:F0:EB:B6:2E:A4:F4:E3:9A:88:F5:AA:61:
        B8:04:BF:04:B6:A3:20:A3:77:77:AD:00:43:B5:F9:01:24:86:D9:BD:
        BE:89:EA:49:60:78:9C:47:C1:1B:A0:07:E6:0C:62:27:94:3F:AA:33:
        1B:4C:E7:A2:0E:35:54:C2:A8:AC:4D:C7:D4:A3:74:C7:77:BE:2E:D2:
        6B:EE:89:2D:6B:44:94:46:51:C2:36:3A:19:22:58:A7:8B:7B:0A:CB:
        32:37:43:68:66:C9:F4:21:B5:2F:01:BB:03:AF:C8:C4:98:D8:8A:7A:
        6B:60:7C:A1:20:69:3B:9E:92:53:B5:6B:77:D6:07:A3:AC:0E:60:56:
        B0:DD:AF:7A:E7:ED:42:D0:83:52:A4:91:C9:81:9E:A1:7C:2F:CE:1F:
        A4:40:E8:40:1C:CA:EE:74:E7:45:EA:E3:FC:5D:F6:30:1B:08:08:4C:
        4F:B2:94:A6:DD:2F:D9:60:9D:55:DA:EC:B2:2C:21:09:A6:A4:86:C1:
        7C:10:06:01:F3:DF:01:30:62:B3:7C:5D:E0:D6:F7:04:DE:DF:6F:7E:
        0B:53:98:3B:7C:36:FD:17:34:0A:75:98
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/r8822be.conf]
options r8822be aspm=0


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   45.540306] r8169 0000:02:00.0 enp2s0: Link is Down


########## wireless info END ############

```

This is extremely frustrating as I bought this laptop expecting to be able to use it with some version of linux.
Thank you very much for trying to help.

---

### Post by theflashman on 2019-11-21
Still looking for a solution.

---

### Post by praseodym on 2019-11-22
Change the ESSID to something without blank. Please also show

```
modprobe -c | grep -i "10ec.*b822"
lsmod
```

---


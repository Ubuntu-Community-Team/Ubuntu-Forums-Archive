---
title: "Realtek rtl8821ae Slow WIFI Transfer"
date: 2017-10-02
forum: Networking &amp; Wireless
---

### Post by mepsteinj on 2017-10-02
Dear Ubuntu community,
Happy new Ubuntu user here (almost :P).

I finally decided to use Ubuntu for my PC but I'm facing some problems with my WIFI card. I spend more than a week searching for a solution, but I think is time to ask for help!

First, I want to mention that I have a 160 Mbit/s (DOWN) and 10 Mbit/s (UP) internet connection managed by a TP-LINK WDR4300 with DD-WRT.

Days ago, before I switch from WIN10 to Ubuntu, in the same machine I score 120 to 130 Mbit/s (DOWN) and 10 Mbit/s (UP) using speedtest.net, but now in Ubuntu, well, see below:
```
michael@force:~$ speedtestRetrieving speedtest.net configuration...
Testing from VTR (xxx.xx.xx.xxx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Entel (Santiago) [12.59 km]: 17.495 ms
Testing download speed................................................................................
Download: 47.02 Mbit/s
Testing upload speed....................................................................................................
Upload: 4.85 Mbit/s
michael@force:~$
```

As you can see, this speed is really low, and also is the MAX transfer rate I'm getting in the LAN.

The DD-WRT stats display a really low RX Rate (6M), in WIN (270+):
```
xx:xx:xx:xx:xx:xx    ath1    0:43:48    270M    6M    HT40SGI    -34    -90    56    100%
```

I have to set some options in "/etc/modprobe.d/rtl8821ae.conf" in order to fix the disconnect issue and also installed the "rtlwifi_new" driver pack from [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git), and now I can say that I have a relative stable WIFI but very slow. Please note, with the rtl8821ae.conf param the disconnect issue was fixed in the stock driver and later in the rtlwifi_new driver, but the transfer speed is the same in both drivers.

**Here you have the results of the wireless-info script.**

```


########## wireless info START ##########


Report from: 02 Oct 2017 02:23 -03 -0300


Booted last: 02 Oct 2017 00:00 -03 -0300


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


##### kernel ############################


Linux 4.10.0-35-generic #39-Ubuntu SMP Wed Sep 13 07:46:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, libata.noacpi=1


##### desktop ###########################


GNOME


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter [10ec:8812] (rev 01)
    Subsystem: D-Link System Inc RTL8812AE 802.11ac PCIe Wireless Network Adapter [1186:3305]
    Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 002 Device 004: ID 045e:0766 Microsoft Corp. LifeCam VX-800
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8821ae             229376  0
btcoexist             167936  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,btcoexist,rtl8821ae
mac80211              782336  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              602112  2 mac80211,rtlwifi
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wmi                    16384  2 asus_wmi,mxm_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf6500000-f6520000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1483  bytes 114672 (114.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1483  bytes 114672 (114.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.20  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::8819:49c5:2f5e:29aa  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2783  bytes 1420676 (1.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1713  bytes 316118 (316.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


eno1      no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"Familia EA - 5G"  
          Mode:Managed  Frequency:5.26 GHz  Access Point: <MAC 'Familia EA - 5G' [AC1]>   
          Bit Rate=300 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:46   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1093     1  0 00:55 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8812AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.10.0-35-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Familia EA - 5G
GENERAL.CON-UUID:                       4a50eead-15dc-4cec-93d3-80cf18119db8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     300 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6b2d3be3-6632-48df-bbff-634097e92695 | Familia EA NS
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   4a50eead-15dc-4cec-93d3-80cf18119db8 | Familia EA - 5G
IP4.ADDRESS[1]:                         192.168.1.20/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home.lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        wpad = 22:a:22
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = FORCE
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       expiry = 1506920479
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.20
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home.lan
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::8819:49c5:2f5e:29aa/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579V Gigabit Network Connection (P8P67 Deluxe Motherboard)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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


SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Familia EA              <MAC 'Familia EA' [AC4]>  Infra  10    2457 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
Familia EA - Invitados  <MAC 'Familia EA - Invitados' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
Macaca                  <MAC 'Macaca' [AC3]>  Infra  7     2442 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
Familia EA - 5G         <MAC 'Familia EA - 5G' [AC1]>  Infra  52    5260 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 
ARRIS-82F2              <MAC 'ARRIS-82F2' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2      no        
ARRIS-27D2              <MAC 'ARRIS-27D2' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2      no        
ARRIS-27D2-5G           <MAC 'ARRIS-27D2-5G' [AN7]>  Infra  40    5200 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2      no        


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


[[/etc/NetworkManager/system-connections/Familia EA - 5G]] (600 root)
[connection] id=Familia EA - 5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Familia EA - 5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Familia EA NS]] (600 root)
[connection] id=Familia EA NS | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Familia EA NS
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Santiago (based on set time zone)


global
country CL: DFS-JP
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5735 - 5835 @ 80), (N/A, 20), (N/A)


##### iwlist channels ###################


eno1      no frequency information.


lo        no frequency information.


wlp3s0    26 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:5.26 GHz (Channel 52)


##### iwlist scan #######################


eno1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:5.26 GHz (Channel 52)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'Familia EA - 5G' [AC1]>
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"Familia EA - 5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002babb003b
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ARRIS-82F2' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"ARRIS-82F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c522d16b
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Macaca' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Macaca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b999118e2
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Familia EA' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Familia EA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ba7f35bd
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Familia EA - Invitados' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Familia EA - Invitados"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ba7f3da3
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.10.0-35-generic/updates/dkms/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7E8496F0BB118AA70A0D506
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.10.0-35-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     44B60E4AEF8FE0C4508E8FE
depends:        mac80211,rtlwifi
vermagic:       4.10.0-35-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.10.0-35-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9BC255DBB57C8378BEB9E46
depends:        mac80211,cfg80211
vermagic:       4.10.0-35-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: N
int_clear: N
ips: N
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


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae ips=0
options rtl8821ae fwlps=0
options rtl8821ae msi=0
options rtl8821ae int_clear=0


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 2603.244943] wlp3s0: aborting authentication with <MAC 'Familia EA - 5G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2616.963989] wlp3s0: authenticate with <MAC 'Familia EA - 5G' [AC1]>
[ 2616.965160] wlp3s0: send auth to <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 2616.966246] wlp3s0: authenticated
[ 2621.640697] wlp3s0: aborting authentication with <MAC 'Familia EA - 5G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2621.641740] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2621.793582] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 2621.996166] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2622.162362] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 2622.364869] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2624.219323] wlp3s0: authenticate with <MAC 'Familia EA - 5G' [AC1]>
[ 2624.220352] wlp3s0: send auth to <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 2624.221411] wlp3s0: authenticated
[ 2632.788315] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 2632.990758] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 2635.078808] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 2635.281190] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2635.323195] wlp3s0: authenticate with <MAC 'Familia EA - 5G' [AC1]>
[ 2635.323892] wlp3s0: send auth to <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 2635.324904] wlp3s0: authenticated
[ 2635.325847] wlp3s0: associate with <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 2635.327099] wlp3s0: RX AssocResp from <MAC 'Familia EA - 5G' [AC1]> (capab=0x11 status=0 aid=1)
[ 2635.328700] wlp3s0: associated
[ 2635.328736] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 3482.054045] wlp3s0: deauthenticating from <MAC 'Familia EA - 5G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3482.436541] rtl8821ae: Using firmware rtlwifi/rtl8812aefw.bin
[ 3482.436543] rtl8821ae: Using firmware rtlwifi/rtl8812aefw_wowlan.bin
[ 3482.436554] rtl8821ae 0000:03:00.0: Direct firmware load for rtlwifi/rtl8812aefw.bin failed with error -2
[ 3482.436555] rtlwifi: Selected firmware is not available
[ 3482.436727] rtl8821ae 0000:03:00.0: Direct firmware load for rtlwifi/rtl8812aefw_wowlan.bin failed with error -2
[ 3482.436727] rtlwifi: Selected firmware is not available
[ 3482.437327] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3482.439318] rtlwifi: rtlwifi: wireless switch is on
[ 3482.439856] rtl8821ae 0000:03:00.0 wlp3s0: renamed from wlan0
[ 3482.463796] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3482.514545] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3482.717080] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3482.768469] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3482.970924] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 3485.032930] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3485.235419] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3485.291933] wlp3s0: authenticate with <MAC 'Familia EA - 5G' [AC1]>
[ 3485.292691] wlp3s0: send auth to <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 3485.294213] wlp3s0: authenticated
[ 3485.301701] wlp3s0: associate with <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 3485.302986] wlp3s0: RX AssocResp from <MAC 'Familia EA - 5G' [AC1]> (capab=0x11 status=0 aid=1)
[ 3485.304620] wlp3s0: associated
[ 3485.304647] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 3575.669348] wlp3s0: deauthenticating from <MAC 'Familia EA - 5G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3576.074218] rtl8821ae: Using firmware rtlwifi/rtl8812aefw.bin
[ 3576.074221] rtl8821ae: Using firmware rtlwifi/rtl8812aefw_wowlan.bin
[ 3576.074234] rtl8821ae 0000:03:00.0: Direct firmware load for rtlwifi/rtl8812aefw.bin failed with error -2
[ 3576.074236] rtlwifi: Selected firmware is not available
[ 3576.074412] rtl8821ae 0000:03:00.0: Direct firmware load for rtlwifi/rtl8812aefw_wowlan.bin failed with error -2
[ 3576.074413] rtlwifi: Selected firmware is not available
[ 3576.075170] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3576.077135] rtl8821ae 0000:03:00.0 wlp3s0: renamed from wlan0
[ 3576.077441] rtlwifi: rtlwifi: wireless switch is on
[ 3576.107400] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3576.158280] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3576.360764] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3576.412162] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3576.614673] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 3578.681586] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3578.883989] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3578.925982] wlp3s0: authenticate with <MAC 'Familia EA - 5G' [AC1]>
[ 3578.926736] wlp3s0: send auth to <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 3578.928214] wlp3s0: authenticated
[ 3578.929071] wlp3s0: associate with <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 3578.930342] wlp3s0: RX AssocResp from <MAC 'Familia EA - 5G' [AC1]> (capab=0x11 status=0 aid=1)
[ 3578.931930] wlp3s0: associated
[ 3578.931960] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 3958.073841] wlp3s0: deauthenticating from <MAC 'Familia EA - 5G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3958.474022] rtl8821ae: Using firmware rtlwifi/rtl8812aefw.bin
[ 3958.474025] rtl8821ae: Using firmware rtlwifi/rtl8812aefw_wowlan.bin
[ 3958.474039] rtl8821ae 0000:03:00.0: Direct firmware load for rtlwifi/rtl8812aefw.bin failed with error -2
[ 3958.474040] rtlwifi: Selected firmware is not available
[ 3958.474216] rtl8821ae 0000:03:00.0: Direct firmware load for rtlwifi/rtl8812aefw_wowlan.bin failed with error -2
[ 3958.474217] rtlwifi: Selected firmware is not available
[ 3958.476133] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3958.476430] rtlwifi: rtlwifi: wireless switch is on
[ 3958.481729] rtl8821ae 0000:03:00.0 wlp3s0: renamed from wlan0
[ 3958.503262] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3958.554058] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3958.756536] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3958.808971] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3959.011405] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 3961.074950] rtl8821ae: Polling FW ready fail!! REG_MCUFWDL:0x00000706 .
[ 3961.277303] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 3961.331867] wlp3s0: authenticate with <MAC 'Familia EA - 5G' [AC1]>
[ 3961.332620] wlp3s0: send auth to <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 3961.334433] wlp3s0: authenticated
[ 3961.337515] wlp3s0: associate with <MAC 'Familia EA - 5G' [AC1]> (try 1/3)
[ 3961.340790] wlp3s0: RX AssocResp from <MAC 'Familia EA - 5G' [AC1]> (capab=0x11 status=0 aid=1)
[ 3961.342416] wlp3s0: associated
[ 3961.342448] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready


########## wireless info END ############



```

[ATTACH]276935[/ATTACH]

Regard,
Michael

---

### Post by Artanis.ro on 2017-10-03
hi  	[**[COLOR=#000000]mepsteinj[/COLOR]**]("https://ubuntuforums.org/member.php?u=2078728") 	 

, unfortunately I cannot help you with your question, but can you post here your driver for your card?

---

### Post by mepsteinj on 2017-10-03
Hi,
Right now I'm using the ubuntu stock driver, I don't see any improvement using the [rtlwifi_new]("https://github.com/lwfinger/rtlwifi_new.git") drivers, I just make the following change in order to fix the disconnection problem, but I still have the speed problem and for me that's a must! I am waiting to see if someone with more knowledge can help me, otherwise I will have to go back to win ](*,)

```
echo "options rtl8821ae int_clear=0 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8821ae.conf
sudo modprobe -r rtl8821ae && sudo modprobe rtl8821ae
```

---

### Post by mepsteinj on 2017-10-04
Well if you have problem with rtl8821ae, don't lose your time finding a working driver. This WIFI card don't work very well in linux!

I just buy an ASUS PCE-AC55BT A1 and well, you can see the difference below...

```
Retrieving speedtest.net configuration...Testing from VTR (xxx.xx.xx.xxx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Claro Chile SA (Santiago) [12.84 km]: 17.254 ms
Testing download speed................................................................................
Download: 160.24 Mbit/s
Testing upload speed....................................................................................................
Upload: 9.91 Mbit/s
```

---

### Post by Vasu_Muppalla on 2017-10-06
> **mepsteinj said:**
> Hi,
Right now I'm using the ubuntu stock driver, I don't see any improvement using the [rtlwifi_new]("https://github.com/lwfinger/rtlwifi_new.git") drivers, I just make the following change in order to fix the disconnection problem, but I still have the speed problem and for me that's a must! I am waiting to see if someone with more knowledge can help me, otherwise I will have to go back to win ](*,)

```
echo "options rtl8821ae int_clear=0 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8821ae.conf
sudo modprobe -r rtl8821ae && sudo modprobe rtl8821ae
```

I was gonna suggest signal strength but iwconfig shows -30db. Maybe it can be improved still with ant_sel=n where n can be 1 or 2.

---

### Post by mepsteinj on 2017-10-06
> **Vasu_Muppalla said:**
> I had problems with rtl8723be- slow connection. I tried with ant_sel=2 and it worked. You may have to try ant_sel=1 or 2 in modprobe and whichever works, add that in the modprobe.d file. Confirm that with the command iwconfig and see how much signal_level is - if it is -80db or smaller then that is the problem and there's an easy fix.

Hi,
The rtl8821ae driver doesn't have the ant_sel option.

```
[COLOR=#000000][FONT=&amp]##### module infos ######################[/FONT][/COLOR]

[rtl8821ae]
filename:       /lib/modules/4.10.0-35-generic/updates/dkms/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7E8496F0BB118AA70A0D506
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1) [COLOR=#000000][FONT=&amp] (bool)[/FONT][/COLOR]
```

---


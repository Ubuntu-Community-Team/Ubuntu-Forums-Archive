---
title: "Intel Wireless 7265 doesn't connect after change another network"
date: 2017-06-17
forum: Networking &amp; Wireless
---

### Post by Glats on 2017-06-17
Grettings!


I have Ubuntu Gnome 17.04 with kernel 4.10.0-21-generic fresh installed.


When I connect the first time to a wireless network works perfectly. However when I try to change to another network doesn't connect and dmseg displayed this error:
```

aborting authentication with xx:xx:xx:xx:xx:xx by local choice (Reason: 3=DEAUTH_LEAVING)
iwlwifi 0000:02:00.0: No association and the time event is over already

```
My lsmod:
```

iwlwifi               229376  1 iwlmvm
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211

```


I did already try set power manager off, disable ipv6, edit nsswitch.conf, killall wpa_supplicant, set REGDOMAIN, set 'options iwlwifi swcrypto=1 11n_disable=8' into iwlwifi.conf.


Thanks for advanced

---

### Post by Glats on 2017-06-21
For real? nobody has an advice about this?
Come on guys this is so annoying :(

---

### Post by Glats on 2017-06-22
My  wireless info script
```

########## wireless info START ##########

Report from: 22 Jun 2017 19:56 -04 -0400

Booted last: 22 Jun 2017 00:00 -04 -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.12.0-041200rc5-generic #201706112031 SMP Mon Jun 12 00:32:34 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5010]
	Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 0bda:57f5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 005: ID 0b05:1854 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwlmvm                376832  0
mac80211              774144  1 iwlmvm
iwlwifi               245760  1 iwlmvm
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wmi                    16384  2 asus_wmi,mxm_wmi
video                  40960  2 asus_wmi,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 318  bytes 23036 (23.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 318  bytes 23036 (23.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.105  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::ca21:58ff:fedf:23de  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 75050  bytes 94395667 (94.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 35234  bytes 6056144 (6.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"JICS"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'JICS' [AC1]>   
          Bit Rate=300 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:332   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       934     1  0 19:31 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.12.0-041200rc5-generic
GENERAL.FIRMWARE-VERSION:               22.391740.0
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     JICS
GENERAL.CON-UUID:                       8eb59f6d-489a-4247-82c7-362abcb71def
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8eb59f6d-489a-4247-82c7-362abcb71def | JICS
IP4.ADDRESS[1]:                         192.168.0.105/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.244.0.3
IP4.DNS[2]:                             209.244.0.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1498181621
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.105
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 209.244.0.3 209.244.0.4
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::ca21:58ff:fedf:23de/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
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

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
LIMONES          <MAC 'LIMONES' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  62      â–‚â–„â–†_  WPA1 WPA2  no        
JICS             <MAC 'JICS' [AC1]>  Infra  5     2432 MHz  54 Mbit/s  61      â–‚â–„â–†_  WPA2       yes     * 
Maty             <MAC 'Maty' [AC8]>  Infra  7     2442 MHz  54 Mbit/s  32      â–‚â–„__  WPA1 WPA2  no        
Belen            <MAC 'Belen' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  30      â–‚___  WPA1 WPA2  no        
JICSLAND         <MAC 'JICSLAND' [AC4]>  Infra  5     2432 MHz  54 Mbit/s  27      â–‚___  WPA2       no        
SBEME            <MAC 'SBEME' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  22      â–‚___  WPA2       no        
movistar_dd8602  <MAC 'movistar_dd8602' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  20      â–‚___  WPA2       no        
MAXIMO           <MAC 'MAXIMO' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  20      â–‚___  WPA1 WPA2  no        
CESAR            <MAC 'CESAR' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  19      â–‚___  WPA1 WPA2  no        
Marambio_ext     <MAC 'Marambio_ext' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  17      â–‚___  WPA2       no        
Francisco        <MAC 'Francisco' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  15      â–‚___  WPA1 WPA2  no        
Casa garcia      <MAC 'Casa garcia' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  9       â–‚___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/JICS]] (600 root)
[connection] id=JICS | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=JICS
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Santiago (based on set time zone)

global
country CL: DFS-JP
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
	(5735 - 5835 @ 80), (N/A, 20), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

wlp2s0    26 channels in total; available frequencies :
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
          Current Frequency:2.432 GHz (Channel 5)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      4   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'JICS' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"JICS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cfd2691b4
                    Extra: Last beacon: 704ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Belen' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Belen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000189d9161bee
                    Extra: Last beacon: 892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SBEME' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SBEME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b8314e891
                    Extra: Last beacon: 1028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'JICSLAND' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"JICSLAND"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019a6ec565e
                    Extra: Last beacon: 828ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'movistar_dd8602' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"movistar_dd8602"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000105eecd75ad
                    Extra: Last beacon: 744ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Francisco' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Francisco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006a545183
                    Extra: Last beacon: 752ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'LIMONES' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"LIMONES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000081d92984bf
                    Extra: Last beacon: 736ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Maty' [AC8]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Maty"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3ca5d52fb
                    Extra: Last beacon: 644ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'MAXIMO' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MAXIMO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000160f2170
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Marambio_ext' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Marambio_ext"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c55c2a361b
                    Extra: Last beacon: 400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Casa garcia' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"Casa garcia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000011522e159
                    Extra: Last beacon: 456ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'CESAR' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"CESAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000189d19bd13c
                    Extra: Last beacon: 440ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.12.0-041200rc5-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     33002BAF51C74D469497DC2
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.12.0-041200rc5-generic SMP mod_unload 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.12.0-041200rc5-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C80F956D688391DE05E80CE
depends:        cfg80211
intree:         Y
vermagic:       4.12.0-041200rc5-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.12.0-041200rc5-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-30.ucode
firmware:       iwlwifi-8000C-30.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0--30.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--30.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--30.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--30.ucode
firmware:       iwlwifi-Qu-a0-hr-a0--30.ucode
srcversion:     0805CCBBB378B21CD1488B6
depends:        cfg80211
intree:         Y
vermagic:       4.12.0-041200rc5-generic SMP mod_unload 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.12.0-041200rc5-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     41B6AD8CC3A348FE83EF412
depends:        
intree:         Y
vermagic:       4.12.0-041200rc5-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

i915
bbswitch

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
options iwlwifi swcrypto=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  105.260980] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  106.304270] wlp2s0: authenticate with <MAC 'JICS' [AC1]>
[  106.307597] wlp2s0: send auth to <MAC 'JICS' [AC1]> (try 1/3)
[  106.310781] wlp2s0: authenticated
[  106.921772] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  106.921834] wlp2s0: Connection to AP <MAC 'JICS' [AC1]> lost
[  111.307135] wlp2s0: aborting authentication with <MAC 'JICS' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  112.447611] wlp2s0: authenticate with <MAC 'JICS' [AC1]>
[  112.450755] wlp2s0: send auth to <MAC 'JICS' [AC1]> (try 1/3)
[  112.453952] wlp2s0: authenticated
[  113.064974] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  113.065038] wlp2s0: Connection to AP <MAC 'JICS' [AC1]> lost
[  117.455238] wlp2s0: aborting authentication with <MAC 'JICS' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  118.993715] wlp2s0: authenticate with <MAC 'JICS' [AC1]>
[  118.997335] wlp2s0: send auth to <MAC 'JICS' [AC1]> (try 1/3)
[  119.000507] wlp2s0: authenticated
[  119.611451] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  119.611521] wlp2s0: Connection to AP <MAC 'JICS' [AC1]> lost
[  119.910705] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[  120.873561] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-29.ucode failed with error -2
[  120.873567] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-28.ucode failed with error -2
[  120.873572] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-27.ucode failed with error -2
[  120.873575] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
[  120.873579] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
[  120.873583] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[  120.873587] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[  120.873942] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[  120.886020] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[  120.888150] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[  120.955355] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[  120.960652] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[  120.982989] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  120.985181] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  121.065871] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  121.074378] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  121.161090] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[  123.693015] wlp2s0: authenticate with <MAC 'JICSLAND' [AC4]>
[  123.697358] wlp2s0: send auth to <MAC 'JICSLAND' [AC4]> (try 1/3)
[  123.802005] wlp2s0: send auth to <MAC 'JICSLAND' [AC4]> (try 2/3)
[  123.808752] wlp2s0: authenticated
[  123.810028] wlp2s0: associate with <MAC 'JICSLAND' [AC4]> (try 1/3)
[  123.814154] wlp2s0: RX AssocResp from <MAC 'JICSLAND' [AC4]> (capab=0x431 status=0 aid=1)
[  123.815063] wlp2s0: associated
[  123.815132] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  142.523763] wlp2s0: deauthenticating from <MAC 'JICSLAND' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  142.546423] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  143.596088] wlp2s0: authenticate with <MAC 'JICS' [AC1]>
[  143.599425] wlp2s0: send auth to <MAC 'JICS' [AC1]> (try 1/3)
[  143.602761] wlp2s0: authenticated
[  144.213488] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  144.213526] wlp2s0: Connection to AP <MAC 'JICS' [AC1]> lost
[  146.532293] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[  147.577804] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-29.ucode failed with error -2
[  147.577809] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-28.ucode failed with error -2
[  147.577814] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-27.ucode failed with error -2
[  147.577818] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
[  147.577822] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
[  147.577825] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[  147.577829] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[  147.578173] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[  147.590430] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[  147.591953] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[  147.660669] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[  147.666542] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[  147.709445] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  147.711704] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  147.790698] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  147.814594] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[  147.901316] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[  150.425816] wlp2s0: authenticate with <MAC 'JICS' [AC1]>
[  150.430700] wlp2s0: send auth to <MAC 'JICS' [AC1]> (try 1/3)
[  150.434591] wlp2s0: authenticated
[  150.435757] wlp2s0: associate with <MAC 'JICS' [AC1]> (try 1/3)
[  150.439738] wlp2s0: RX AssocResp from <MAC 'JICS' [AC1]> (capab=0x431 status=0 aid=4)
[  150.443280] wlp2s0: associated
[  150.443317] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############



```

---

### Post by him610 on 2017-06-23
Hello Glats,

Your wireless script indicates you are connected to ESSID: JICS with IP 192.168.0.105. Bottom line: your intel 7265 operates.

Your issue with inability to connect with other networks may be best be addressed by the owners/operators of those wireless network APs/routers.

---

### Post by Glats on 2017-06-23
> **him610 said:**
> Hello Glats,

Your wireless script indicates you are connected to ESSID: JICS with IP 192.168.0.105. Bottom line: your intel 7265 operates.

Your issue with inability to connect with other networks may be best be addressed by the owners/operators of those wireless network APs/routers.

Actually I configured the routers by myself.

---

### Post by vocx on 2017-06-23
> **Glats said:**
> My  wireless info script
```

[  120.873561] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-29.ucode failed with error -2
[  120.873567] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-28.ucode failed with error -2
[  120.873572] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-27.ucode failed with error -2
[  120.873575] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
[  120.873579] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
[  120.873583] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[  120.873587] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[  120.873942] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[  120.886020] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210

```
Personally, I find wireless a mystery. It's like black magic, sometimes it works and sometimes it doesn't. Sometimes you use a router and it works, then you change the router and doesn't work any more. Or you upgrade the system and it doesn't work as good as before. So it leaves you wondering where the problem is, in your router, or computer, or internet service provider, or maybe the electronics overheat and don't work as well any more, or what. It's frustrating.

The only thing that I saw strange is the message about the firmware.

You are supposed to have the correct firmware for your kernel. I am also using an Intel 7265 wireless adapter, using the "iwlwifi" kernel module. I had some random issues, but was always able to reconnect to the same network, so not major issues like you describe.

 You may try downloading and copying the missing firmware files "iwlwifi-7265D-29.ucode", etc., to "/lib/firmware/".
```
sudo mv -t /lib/firmware iwlwifi-7265D-29.ucode
```

Online you can find many places that host the firmware files and some explanation for those errors. Apparently if it does not find the latest firmware, it will try using the next one in line.
[LIST]
[*][https://github.com/NetBit73/NeteXt73_pakiety/tree/master/iwlwifi](https://github.com/NetBit73/NeteXt73_pakiety/tree/master/iwlwifi)
[*][https://bugzilla.redhat.com/show_bug.cgi?id=1400269](https://bugzilla.redhat.com/show_bug.cgi?id=1400269)
[/LIST]

I am using 16.04, so my kernel is a bit older than yours. Previously I was loading the v18 firmware, and now the v19. I'm not sure if that had anything to do with my wireless issues. I also have a WiFi signal extensor, which seemed to cause interferences with the main router. So if you have one you may want to turn it off and see if that improves things.

---

### Post by johndough2 on 2017-06-25
Hi

I noticed 

nameserver 127.0.0.53

and thought it odd.

---

### Post by jeremy31 on 2017-06-25
Have you tried Ubuntu 16.04?  It will be supported until 2021 and support for 17.04 will end January 2018
However there might be a possible fix
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```

At the bottom of the file add
```
[device]
wifi.scan-rand-mac-address=no
```

Reboot and see if that fixes it.  I know a lot of USB wifi adapters won't connect at all until this fix is used in 17.04

---

### Post by miatawnt2b on 2017-07-11
> **jeremy31 said:**
> Have you tried Ubuntu 16.04?  It will be supported until 2021 and support for 17.04 will end January 2018
However there might be a possible fix
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```

At the bottom of the file add
```
[device]
wifi.scan-rand-mac-address=no
```

Reboot and see if that fixes it.  I know a lot of USB wifi adapters won't connect at all until this fix is used in 17.04

I can confirm this works for me. I was having the same issue with an intel 7260 after an upgrade to 17.04

---

### Post by BenginM on 2017-07-11
[FONT=Courier New] Salutations!

Are you connecting using Network manger! what are the the configurations in the router for these two *access point* you're trying to connect to .. Channel & a Encrypt Mode! Are you able to connect from your smartphone to these two AP's successfully?

in a terminal run: $ tail -f /var/log/syslog , and try to connect to the target AP in question!

[/FONT]

---


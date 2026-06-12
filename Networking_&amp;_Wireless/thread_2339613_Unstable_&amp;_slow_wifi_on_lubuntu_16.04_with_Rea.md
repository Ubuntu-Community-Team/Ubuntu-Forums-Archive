---
title: "Unstable &amp; slow wifi on lubuntu 16.04 with Realtek 8187SE (MSI Wind U100)"
date: 2016-10-10
forum: Networking &amp; Wireless
---

### Post by cero3 on 2016-10-10
Hi there :-)


I am trying to get an old MSI Wind U100 netbook running (for office and the web). However I am facing serious wifi issues on every linux distribution I've tried (Puppy, Bodhi, DSL, ...). So I now chose Lubuntu in hope of having a better driver compatibility.


I am able to connect to my wifi (sometimes after some failed attempts, turning it off and on again), however it is very unstable, quite slow and disconnects all the time.


Currently it doesn't connect at all. I am trying different things for some days now. It would be greatly appreciated if someone could give me a hint on what I am missing. 


Thank you!


wireless-info output:
```


########## wireless info START ##########


Report from: 10 Oct 2016 23:19 CEST +0200


Booted last: 10 Oct 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:41:41 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1462:0110]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
    Kernel driver in use: rtl818x_pci


##### lsusb #############################


Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


1: msi-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: msi-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl818x_pci            49152  0
msi_wmi                16384  0
mac80211              659456  1 rtl818x_pci
sparse_keymap          16384  2 msi_laptop,msi_wmi
cfg80211              499712  2 mac80211,rtl818x_pci
eeprom_93cx6           16384  1 rtl818x_pci
wmi                    20480  1 msi_wmi
video                  36864  3 i915,msi_laptop,msi_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.178.29  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::d06a:135b:b82a:8e31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74454 (74.4 KB)  TX bytes:111391 (111.3 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11bg  ESSID:"FRITZ!Box 7362 SL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'FRITZ!Box 7362 SL' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:35  Invalid misc:1   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    600    0        0 wlp2s0
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fritz.box


##### network managers ##################


Installed:


    NetworkManager


Running:


root       630     1  0 17:47 ?        00:00:23 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8187SE Wireless LAN Controller (MN54G2 / MS-6894 Wireless Mini PCIe Card)
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.4.0-38-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FRITZ!Box 7362 SL
GENERAL.CON-UUID:                       0af7476d-0b14-484c-8957-025e767de736
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0af7476d-0b14-484c-8957-025e767de736 | FRITZ!Box 7362 SL
IP4.ADDRESS[1]:                         192.168.178.29/24
IP4.GATEWAY:                            192.168.178.1
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.29
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1476997487
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::d06a:135b:b82a:8e31/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
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


SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FRITZ!Box 7362 SL             <MAC 'FRITZ!Box 7362 SL' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       yes     * 
TC-6F650                      <MAC 'TC-6F650' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
WLAN-3DD231                   <MAC 'WLAN-3DD231' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
TC-66CAB                      <MAC 'TC-66CAB' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
FRITZ!Box 7490_6C             <MAC 'FRITZ!Box 7490_6C' [AC10]>  Infra  12    2467 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
MDCC_00997351305126           <MAC 'MDCC_00997351305126' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
FRITZ!Box 7490                <MAC 'FRITZ!Box 7490' [AC11]>  Infra  12    2467 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
jj                            <MAC 'jj' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
MDCC_00951225600765           <MAC 'MDCC_00951225600765' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
skynet                        <MAC 'skynet' [AC8]>  Infra  9     2452 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
FRITZ!Box 7490                <MAC 'FRITZ!Box 7490' [AC13]>  Infra  12    2467 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
HP-Print-13-ENVY 4500 series  <MAC 'HP-Print-13-ENVY 4500 series' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  --         no        
FRITZ!Box 7362 SL             <MAC 'FRITZ!Box 7362 SL' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  15      &#9602;___  WPA2       no        


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


[[/etc/NetworkManager/system-connections/FRITZ!Box 7362 SL]] (600 root)
[connection] id=FRITZ!Box 7362 SL | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FRITZ!Box 7362 SL
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp1s0    no frequency information.


wlp2s0    13 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


Channel occupancy:


      7   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:2.467 GHz (Channel 12)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'FRITZ!Box 7362 SL' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018069f8cc1e
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TC-66CAB' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"TC-66CAB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000049802cb4f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WLAN-3DD231' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"WLAN-3DD231"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016a0b4e1851
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'HP-Print-13-ENVY 4500 series' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-13-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006c8dae6489
                    Extra: Last beacon: 8ms ago
          Cell 05 - Address: <MAC 'MDCC_00951225600765' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MDCC_00951225600765"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000117e2f0ba3e
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'jj' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"jj"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006739e3a3195
                    Extra: Last beacon: 988ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FRITZ!Box 7362 SL' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006bf0549180
                    Extra: Last beacon: 400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'skynet' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"skynet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b0bb11d180
                    Extra: Last beacon: 1696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'MDCC_00997351305126' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MDCC_00997351305126"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000098f6fcd1ba
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'FRITZ!Box 7490_6C' [AC10]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490_6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bc034a276
                    Extra: Last beacon: 456ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'FRITZ!Box 7490' [AC11]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000397703ab0
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'TC-6F650' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"TC-6F650"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001375fc4426
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'FRITZ!Box 7490' [AC13]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000328399a10
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl818x_pci]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 


[mac80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8187se.conf]
options rtl8187se fwlps=N


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="rtl8187se"


##### udev rules ########################


##### dmesg #############################


[11885.482455] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[19015.151646] wlp2s0: authenticate with <MAC 'FRITZ!Box 7362 SL' [AC1]>
[19015.261750] wlp2s0: send auth to <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[19015.269528] wlp2s0: authenticated
[19015.272686] wlp2s0: associate with <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[19015.281025] wlp2s0: RX AssocResp from <MAC 'FRITZ!Box 7362 SL' [AC1]> (capab=0x431 status=0 aid=4)
[19015.281111] wlp2s0: associated
[19015.281273] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[19018.573444] wlp2s0: deauthenticating from <MAC 'FRITZ!Box 7362 SL' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[19021.840550] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[19023.560190] wlp2s0: authenticate with <MAC 'FRITZ!Box 7362 SL' [AC1]>
[19023.616202] wlp2s0: send auth to <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[19023.619910] wlp2s0: authenticated
[19023.624126] wlp2s0: associate with <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[19023.630321] wlp2s0: RX AssocResp from <MAC 'FRITZ!Box 7362 SL' [AC1]> (capab=0x431 status=0 aid=4)
[19023.630404] wlp2s0: associated
[19023.633512] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[19060.031393] wlp2s0: deauthenticating from <MAC 'FRITZ!Box 7362 SL' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[19063.112545] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[19064.846835] wlp2s0: authenticate with <MAC 'FRITZ!Box 7362 SL' [AC1]>
[19064.900281] wlp2s0: send auth to <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[19064.903068] wlp2s0: authenticated
[19064.908119] wlp2s0: associate with <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[19064.915286] wlp2s0: RX AssocResp from <MAC 'FRITZ!Box 7362 SL' [AC1]> (capab=0x431 status=0 aid=4)
[19064.915375] wlp2s0: associated
[19064.915524] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-10-11
The only suggestion I have is to change the wifi router to channel 1 and change network manager setting for IPv6 to ignore

---

### Post by Hadaka on 2016-10-11
Hi in addition to what jeremy31 noted and suggested, I also noticed..
You stated..
"So I now chose [COLOR=#ff0000]Lubuntu[/COLOR] in hope of having a better driver compatibility."
But the diagnostic report shows..
Distributor ID:    Ubuntu
Description: [COLOR=#ff0000]Ubuntu[/COLOR] 16.04.1 LTS
Release:    16.04
Codename:    [COLOR=#ff0000]xenial

[/COLOR]this may be a bit much for the vintage MSI Wind U100 netbook

also your wifi name has spaces in it and linux prefers it doesnt
and there are 2 access points with identical names...
do you have a repeater set up or is that someone else nearby??
You are on [AC1]
wlp2s0 ESSID:"FRITZ!Box 7362 SL"

FRITZ!Box 7362 SL <MAC 'FRITZ!Box 7362 SL' [[COLOR=#ff0000]AC1[/COLOR]=]=> Infra 6 2437 MHz 54 Mbit/s 67 &#9602;&#9604;&#9606;_ WPA2 yes * 
FRITZ!Box 7362 SL <MAC 'FRITZ!Box 7362 SL' [[COLOR=#ff0000]AC7[/COLOR]=]=> Infra 6 2437 MHz 54 Mbit/s 15 &#9602;___  WPA2 no

if possible change your router name to something with no spaces and not duplicate.
Along with doing what jeremy31 suggests
please post the output of..
```
dmesg | grep iwl
```
thanks

---

### Post by cero3 on 2016-10-11
@jeremy31: Thanks! I will try that when getting home.

@Hadaka: 

That's interesting. But there is definitely Lubuntu running on the netbook. ;-) Don't know, why this is diagnosed as Ubuntu.

I am also unsure why the network is showing twice. I don't have a repeater, I will try to reproduce and diagnose this when I'm back home. As for the router: I would prefer not to change the network's name, since I would have to reconnect all other devices, but if nothing else works out, I will try this as well.

---

### Post by cero3 on 2016-10-11
I'm home and suddenly everything seems to work fine. So I won't change anything for now (never change a running system). I will observe this for some days and if it changes back to not working I will try the things you proposed and notify you, else I mark this thread as solved.

Anyway thank you for your help so far.

PS: The doubling of the network doesn't seem to be reproducible. Current status:
```


########## wireless info START ##########


Report from: 11 Oct 2016 22:34 CEST +0200


Booted last: 11 Oct 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:41:41 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1462:0110]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
	Subsystem: Micro-Star International Co., Ltd. [MSI] MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
	Kernel driver in use: rtl818x_pci


##### lsusb #############################


Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: msi-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: msi-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl818x_pci            49152  0
mac80211              659456  1 rtl818x_pci
msi_wmi                16384  0
cfg80211              499712  2 mac80211,rtl818x_pci
sparse_keymap          16384  2 msi_laptop,msi_wmi
eeprom_93cx6           16384  1 rtl818x_pci
wmi                    20480  1 msi_wmi
video                  36864  3 i915,msi_laptop,msi_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.178.29  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::d06a:135b:b82a:8e31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4350408 (4.3 MB)  TX bytes:543923 (543.9 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11bg  ESSID:"FRITZ!Box 7362 SL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'FRITZ!Box 7362 SL' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:51  Invalid misc:76   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    600    0        0 wlp2s0
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fritz.box


##### network managers ##################


Installed:


	NetworkManager


Running:


root       613     1  0 22:22 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8187SE Wireless LAN Controller (MN54G2 / MS-6894 Wireless Mini PCIe Card)
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.4.0-38-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FRITZ!Box 7362 SL
GENERAL.CON-UUID:                       0af7476d-0b14-484c-8957-025e767de736
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0af7476d-0b14-484c-8957-025e767de736 | FRITZ!Box 7362 SL
IP4.ADDRESS[1]:                         192.168.178.29/24
IP4.GATEWAY:                            192.168.178.1
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.29
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1477081434
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::d06a:135b:b82a:8e31/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
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


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FRITZ!Box 7362 SL    <MAC 'FRITZ!Box 7362 SL' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       yes     * 
WLAN-3DD231          <MAC 'WLAN-3DD231' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
MDCC_00997351305126  <MAC 'MDCC_00997351305126' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
TC-6F650             <MAC 'TC-6F650' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
FRITZ!Box 7490_6C    <MAC 'FRITZ!Box 7490_6C' [AC7]>  Infra  12    2467 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
FRITZ!Box 7490       <MAC 'FRITZ!Box 7490' [AC8]>  Infra  12    2467 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
MDCC_00951225600765  <MAC 'MDCC_00951225600765' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
KDG-7C0E4            <MAC 'KDG-7C0E4' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/FRITZ!Box 7362 SL]] (600 root)
[connection] id=FRITZ!Box 7362 SL | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FRITZ!Box 7362 SL
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp1s0    no frequency information.


wlp2s0    13 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:2.467 GHz (Channel 12)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'FRITZ!Box 7362 SL' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000193e6e6b262
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MDCC_00951225600765' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MDCC_00951225600765"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012b5fd8fa88
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WLAN-3DD231' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"WLAN-3DD231"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017d8840479e
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TC-6F650' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"TC-6F650"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000026f2b9f412
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'KDG-7C0E4' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"KDG-7C0E4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b7d4f0180
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'MDCC_00997351305126' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"MDCC_00997351305126"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ac73dad7c2
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FRITZ!Box 7490_6C' [AC7]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490_6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005f3ddab15e
                    Extra: Last beacon: 500ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'FRITZ!Box 7490' [AC8]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f14a4cbd
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'FRITZ!Box 7490' [AC9]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002ec724c8
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl818x_pci]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 


[mac80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 686 
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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8187se.conf]
options rtl8187se fwlps=N


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="rtl8187se"


##### udev rules ########################


##### dmesg #############################


[   15.817301] ieee80211 phy0: hwaddr 001d92cd5364, RTL8187SE + rtl8225-se
[   15.886329] rtl818x_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   31.343750] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   31.353331] r8169 0000:01:00.0 enp1s0: link down
[   31.353428] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   31.411955] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[   35.714566] wlp2s0: authenticate with <MAC 'FRITZ!Box 7362 SL' [AC1]>
[   35.768260] wlp2s0: send auth to <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[   35.771512] wlp2s0: authenticated
[   35.776077] wlp2s0: associate with <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[   35.783396] wlp2s0: RX AssocResp from <MAC 'FRITZ!Box 7362 SL' [AC1]> (capab=0x431 status=0 aid=5)
[   35.783487] wlp2s0: associated
[   35.783634] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   81.052837] wlp2s0: deauthenticating from <MAC 'FRITZ!Box 7362 SL' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   82.289985] wlp2s0: authenticate with <MAC 'FRITZ!Box 7362 SL' [AC1]>
[   82.400242] wlp2s0: send auth to <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[   82.408493] wlp2s0: authenticated
[   82.420087] wlp2s0: associate with <MAC 'FRITZ!Box 7362 SL' [AC1]> (try 1/3)
[   82.427136] wlp2s0: RX AssocResp from <MAC 'FRITZ!Box 7362 SL' [AC1]> (capab=0x431 status=0 aid=5)
[   82.427220] wlp2s0: associated


########## wireless info END ############



```

---


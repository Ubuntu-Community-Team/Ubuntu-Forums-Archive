---
title: "Unable to connect to ethernet connection"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by arnout3 on 2015-05-06
I'm currently unable to connect to the universities ethernet connection with a wire.
This is the info I get from the wireless-info script:
```

########## wireless info START ##########
Report from: 06 May 2015 11:13 CEST +0200
Booted last: 06 May 2015 12:59 CEST +0200
Script from: 30 Apr 2015 17:23 UTC +0000
##### release ###########################
Distributor ID:    UbuntuDescription:    Ubuntu 15.04Release:    15.04Codename:    vivid
##### kernel ############################
Linux 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7
##### desktop ###########################
Ubuntu
##### lspci #############################
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)    Subsystem: Dell Device [1028:05be]    Kernel driver in use: e1000e
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4460]    Kernel driver in use: iwlwifi
##### lsusb #############################
Bus 004 Device 003: ID 8087:07da Intel Corp. Bus 004 Device 002: ID 8087:8000 Intel Corp. Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 003 Device 003: ID 0c45:649d Microdia Bus 003 Device 002: ID 8087:8008 Intel Corp. Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 002 Device 002: ID 413c:5534 Dell Computer Corp. Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 001 Device 008: ID 0424:2514 Standard Microsystems Corp. USB 2.0 HubBus 001 Device 007: ID 095d:9201 Polycom, Inc. Bus 001 Device 006: ID 413c:2134 Dell Computer Corp. Bus 001 Device 002: ID 0461:4d51 Primax Electronics, Ltd 0Y357C PMX-MMOCZUL (B) [Dell Laser Mouse]Bus 001 Device 005: ID 413c:2107 Dell Computer Corp. Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port ReplicatorBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
##### PCMCIA card info ##################
##### rfkill ############################
0: hci0: Bluetooth    Soft blocked: no    Hard blocked: no1: phy0: Wireless LAN    Soft blocked: no    Hard blocked: no2: dell-wifi: Wireless LAN    Soft blocked: no    Hard blocked: no3: dell-bluetooth: Bluetooth    Soft blocked: no    Hard blocked: no
##### lsmod #############################
dell_wmi               16384  0 sparse_keymap          16384  1 dell_wmidell_laptop            16384  0 dcdbas                 16384  1 dell_laptopiwldvm                237568  0 mac80211              720896  1 iwldvmsnd_soc_rt5640         94208  0 snd_soc_rl6231         16384  1 snd_soc_rt5640snd_soc_core          196608  1 snd_soc_rt5640iwlwifi               196608  1 iwldvmcfg80211              540672  3 iwlwifi,mac80211,iwldvmsnd_pcm               106496  8 snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaenginewmi                    20480  1 dell_wmi
##### interfaces ########################
auto loiface lo inet loopback
##### ifconfig ##########################
eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>            inet6 addr: fe80::eef4:bbff:fe6b:2604/64 Scope:Link          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          RX packets:30289 errors:0 dropped:161 overruns:0 frame:0          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:4066887 (4.0 MB)  TX bytes:72780 (72.7 KB)          Interrupt:20 Memory:f7d00000-f7d20000 
wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>            inet addr:10.43.125.165  Bcast:10.43.127.255  Mask:255.255.192.0          inet6 addr: 2a02:2c40:400:0:60d3:e137:4df6:f29d/64 Scope:Global          inet6 addr: fe80::8200:bff:fe29:ab44/64 Scope:Link          inet6 addr: 2a02:2c40:400::1:e086/128 Scope:Global          inet6 addr: 2a02:2c40:400:0:8200:bff:fe29:ab44/64 Scope:Global          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          RX packets:7307 errors:0 dropped:0 overruns:0 frame:0          TX packets:5877 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:2103269 (2.1 MB)  TX bytes:1382530 (1.3 MB)
##### iwconfig ##########################
eth0      no wireless extensions.
lo        no wireless extensions.
wlan0     IEEE 802.11abgn  ESSID:"eduroam"            Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'eduroam' [AC1]>             Bit Rate=121.5 Mb/s   Tx-Power=15 dBm             Retry short limit:7   RTS thr:off   Fragment thr:off          Power Management:on          Link Quality=46/70  Signal level=-64 dBm            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          Tx excessive retries:0  Invalid misc:26   Missed beacon:0
##### route #############################
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface0.0.0.0         10.43.127.254   0.0.0.0         UG    1024   0        0 wlan01.1.1.1         10.43.127.254   255.255.255.255 UGH   10     0        0 wlan010.43.64.0      0.0.0.0         255.255.192.0   U     0      0        0 wlan0169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
##### resolv.conf #######################
nameserver 127.0.1.1search extern.kuleuven.be hwstudent.ghum.kuleuven.be
##### NetworkManager info ###############
GENERAL.DEVICE:                         wlan0GENERAL.TYPE:                           wifiGENERAL.VENDOR:                         Intel CorporationGENERAL.PRODUCT:                        Centrino Advanced-N 6235 (AGN)GENERAL.DRIVER:                         iwlwifiGENERAL.DRIVER-VERSION:                 3.19.0-16-genericGENERAL.FIRMWARE-VERSION:               18.168.6.1GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>GENERAL.MTU:                            1500GENERAL.STATE:                          100 (connected)GENERAL.REASON:                         0 (No reason given)GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlan0GENERAL.IP-IFACE:                       wlan0GENERAL.NM-MANAGED:                     yesGENERAL.AUTOCONNECT:                    yesGENERAL.FIRMWARE-MISSING:               noGENERAL.CONNECTION:                     eduroamGENERAL.CON-UUID:                       3e59a660-d0a4-4d23-8f02-dc9d3ad0a55aGENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7CAPABILITIES.CARRIER-DETECT:            noCAPABILITIES.SPEED:                     121 Mb/sCONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,3}CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   26a26351-cbf1-4347-8454-dffe27c63eab | A9F1BDF1DAB1nvt4F4F59CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   3e59a660-d0a4-4d23-8f02-dc9d3ad0a55a | eduroamWIFI-PROPERTIES.WEP:                    yesWIFI-PROPERTIES.WPA:                    yesWIFI-PROPERTIES.WPA2:                   yesWIFI-PROPERTIES.TKIP:                   yesWIFI-PROPERTIES.CCMP:                   yesWIFI-PROPERTIES.AP:                     yesWIFI-PROPERTIES.ADHOC:                  yesIP4.ADDRESS[1]:                         ip = 10.43.125.165/18, gw = 10.43.127.254IP4.ROUTE[1]:                           dst = 1.1.1.1/32, nh = 10.43.127.254, mt = 10IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000IP4.DNS[1]:                             134.58.126.3IP4.DNS[2]:                             134.58.127.1IP4.DOMAIN[1]:                          extern.kuleuven.beDHCP4.OPTION[1]:                        network_number = 10.43.64.0DHCP4.OPTION[2]:                        requested_domain_search = 1DHCP4.OPTION[3]:                        requested_host_name = 1DHCP4.OPTION[4]:                        requested_broadcast_address = 1DHCP4.OPTION[5]:                        requested_domain_name = 1DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1DHCP4.OPTION[7]:                        requested_time_offset = 1DHCP4.OPTION[8]:                        requested_netbios_scope = 1DHCP4.OPTION[9]:                        expiry = 1430904303DHCP4.OPTION[10]:                       next_server = 0.0.0.0DHCP4.OPTION[11]:                       domain_name = extern.kuleuven.beDHCP4.OPTION[12]:                       dhcp_message_type = 5DHCP4.OPTION[13]:                       requested_interface_mtu = 1DHCP4.OPTION[14]:                       broadcast_address = 10.43.127.255DHCP4.OPTION[15]:                       dhcp_lease_time = 900DHCP4.OPTION[16]:                       requested_subnet_mask = 1DHCP4.OPTION[17]:                       routers = 10.43.127.254DHCP4.OPTION[18]:                       ip_address = 10.43.125.165DHCP4.OPTION[19]:                       requested_static_routes = 1DHCP4.OPTION[20]:                       subnet_mask = 255.255.192.0DHCP4.OPTION[21]:                       domain_name_servers = 134.58.126.3 134.58.127.1DHCP4.OPTION[22]:                       requested_domain_name_servers = 1DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1DHCP4.OPTION[25]:                       requested_routers = 1DHCP4.OPTION[26]:                       domain_search = hwstudent.ghum.kuleuven.be.DHCP4.OPTION[27]:                       requested_ntp_servers = 1DHCP4.OPTION[28]:                       requested_wpad = 1DHCP4.OPTION[29]:                       dhcp_server_identifier = 1.1.1.1IP6.ADDRESS[1]:                         ip = 2a02:2c40:400::1:e086/128, gw = fe80::1IP6.ADDRESS[2]:                         ip = 2a02:2c40:400:0:60d3:e137:4df6:f29d/64, gw = fe80::1IP6.ADDRESS[3]:                         ip = 2a02:2c40:400:0:8200:bff:fe29:ab44/64, gw = fe80::1IP6.ADDRESS[4]:                         ip = fe80::8200:bff:fe29:ab44/64, gw = fe80::1IP6.ROUTE[1]:                           dst = 2a02:2c40:400::/64, nh = ::, mt = 10DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:c2:95:f3:15:e1:77:c7:37:bb:a0:b1:90:3e:a9:fb:ecDHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1DHCP6.OPTION[3]:                        rebind = 0DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1DHCP6.OPTION[5]:                        max_life = 86400DHCP6.OPTION[6]:                        preferred_life = 40000DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1DHCP6.OPTION[9]:                        life_starts = 1430806776DHCP6.OPTION[10]:                       ip6_address = 2a02:2c40:400::1:e086DHCP6.OPTION[11]:                       ip6_prefixlen = 64DHCP6.OPTION[12]:                       renew = 0DHCP6.OPTION[13]:                       dhcp6_server_id = 0:1:0:1:16:74:a3:cc:0:24:81:ae:7:4DHCP6.OPTION[14]:                       iaid = 0b:29:ab:44DHCP6.OPTION[15]:                       starts = 1430806776
GENERAL.DEVICE:                         eth0GENERAL.TYPE:                           ethernetGENERAL.VENDOR:                         Intel CorporationGENERAL.PRODUCT:                        Ethernet Connection I217-LMGENERAL.DRIVER:                         e1000eGENERAL.DRIVER-VERSION:                 2.3.2-kGENERAL.FIRMWARE-VERSION:               0.13-3GENERAL.HWADDR:                         <MAC 'eth0' [IF]>GENERAL.MTU:                            1500GENERAL.STATE:                          70 (connecting (getting IP configuration))GENERAL.REASON:                         0 (No reason given)GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0GENERAL.IP-IFACE:                       GENERAL.NM-MANAGED:                     yesGENERAL.AUTOCONNECT:                    yesGENERAL.FIRMWARE-MISSING:               noGENERAL.CONNECTION:                     Ethernet connection 1GENERAL.CON-UUID:                       93dff12a-c473-40f8-bd4e-5c1271829ecaGENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/13CAPABILITIES.CARRIER-DETECT:            yesCAPABILITIES.SPEED:                     100 Mb/sCONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,8}CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   93dff12a-c473-40f8-bd4e-5c1271829eca | Ethernet connection 1CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   089ddb47-0ed4-4788-9acd-5a8902921e1d | Ethernet connection 2WIRED-PROPERTIES.CARRIER:               on
SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * eduroam         <MAC 'eduroam' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AC13]>  Infra  36    5180 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        eduroam         <MAC 'eduroam' [AN4]>  Infra  100   5500 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        eduroam         <MAC 'eduroam' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  WPA2 802.1X  no        kuleuven-guest  <MAC 'kuleuven-guest' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        kuleuven-guest  <MAC 'kuleuven-guest' [AC14]>  Infra  36    5180 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --           no        kuleuven-guest  <MAC 'kuleuven-guest' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        kuleuven-guest  <MAC 'kuleuven-guest' [AC16]>  Infra  100   5500 MHz  54 Mbit/s  24      &#9602;___  --           no        kuleuven-guest  <MAC 'kuleuven-guest' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        kuleuven-guest  <MAC 'kuleuven-guest' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  --           no        kuleuven-guest  <MAC 'kuleuven-guest' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  --           no        eduroam         <MAC 'eduroam' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AN17]>  Infra  100   5500 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        eduroam         <MAC 'eduroam' [AC15]>  Infra  36    5180 MHz  54 Mbit/s  20      &#9602;___  WPA2 802.1X  no        eduroam         <MAC 'eduroam' [AN19]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        kuleuven-guest  <MAC 'kuleuven-guest' [AN20]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  --           no        eduroam         <MAC 'eduroam' [AN21]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AN22]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X  no        eduroam         <MAC 'eduroam' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  41      &#9602;&#9604;__  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AN24]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        kuleuven        <MAC 'kuleuven' [AN25]>  Infra  36    5180 MHz  54 Mbit/s  19      &#9602;___  WPA2 802.1X  no        eduroam         <MAC 'eduroam' [AC1]>  Infra  36    5180 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2 802.1X  yes     * 
##### NetworkManager.state ##############
[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=trueWimaxEnabled=true
##### NetworkManager.conf ###############
[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq
no-auto-default=<MAC 'eth0' [IF]>,<MAC address>,
[ifupdown]managed=true
##### NetworkManager profiles ###########
[[/etc/NetworkManager/system-connections/WiFi-2.4-32B3]] (600 root)[connection] id=WiFi-2.4-32B3 | type=802-11-wireless[802-11-wireless] ssid=WiFi-2.4-32B3 | mac-address=<MAC 'wlan0' [IF]>[ipv4] method=auto[ipv6] method=auto
[[/etc/NetworkManager/system-connections/A9F1BDF1DAB1nvt4F4F59]] (600 root)[connection] id=A9F1BDF1DAB1nvt4F4F59 | type=802-11-wireless[802-11-wireless] ssid=A9F1BDF1DAB1nvt4F4F59 | mac-address=<MAC 'wlan0' [IF]>[ipv4] method=auto[ipv6] method=auto
[[/etc/NetworkManager/system-connections/GO BUS]] (600 root)[connection] id=GO BUS | type=802-11-wireless[802-11-wireless] ssid=GO BUS | mac-address=<MAC 'wlan0' [IF]>[ipv6] method=auto[ipv4] method=auto
[[/etc/NetworkManager/system-connections/Dublin Airport Free WiFi]] (600 root)[connection] id=Dublin Airport Free WiFi | type=802-11-wireless[802-11-wireless] ssid=Dublin Airport Free WiFi | mac-address=<MAC 'wlan0' [IF]>[ipv6] method=auto[ipv4] method=auto
[[/etc/NetworkManager/system-connections/TELENETHOTSPOT]] (600 root)[connection] id=TELENETHOTSPOT | type=802-11-wireless[802-11-wireless] ssid=TELENETHOTSPOT | mac-address=<MAC 'wlan0' [IF]>[ipv6] method=auto[ipv4] method=auto
[[/etc/NetworkManager/system-connections/Premier Inn Free Wi-Fi]] (600 root)[connection] id=Premier Inn Free Wi-Fi | type=802-11-wireless[802-11-wireless] ssid=Premier Inn Free Wi-Fi | mac-address=<MAC 'wlan0' [IF]>[ipv6] method=auto[ipv4] method=auto
[[/etc/NetworkManager/system-connections/m3connect]] (600 root)[connection] id=m3connect | type=802-11-wireless[802-11-wireless] ssid=m3connect | mac-address=<MAC 'wlan0' [IF]>[ipv6] method=auto[ipv4] method=auto
[[/etc/NetworkManager/system-connections/eduroam]] (600 root)[ipv6] method=auto[connection] id=eduroam | type=802-11-wireless[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>[ipv4] method=auto
[[/etc/NetworkManager/system-connections/iPhone]] (600 root)[connection] id=iPhone | type=802-11-wireless[802-11-wireless] ssid=iPhone | mac-address=<MAC 'wlan0' [IF]>[ipv4] method=auto[ipv6] method=auto
##### iw reg get ########################
Region: Europe/Brussels (based on set time zone)
country BE: DFS-ETSI    (2402 - 2482 @ 40), (N/A, 20), (N/A)    (5170 - 5250 @ 40), (N/A, 20), (N/A)    (5250 - 5330 @ 40), (N/A, 20), (0 ms), DFS    (5490 - 5710 @ 40), (N/A, 27), (0 ms), DFS    (57240 - 65880 @ 2160), (N/A, 40), (N/A), NO-OUTDOOR
##### iwlist channels ###################
eth0      no frequency information.
lo        no frequency information.
wlan0     32 channels in total; available frequencies :          Channel 01 : 2.412 GHz          Channel 02 : 2.417 GHz          Channel 03 : 2.422 GHz          Channel 04 : 2.427 GHz          Channel 05 : 2.432 GHz          Channel 06 : 2.437 GHz          Channel 07 : 2.442 GHz          Channel 08 : 2.447 GHz          Channel 09 : 2.452 GHz          Channel 10 : 2.457 GHz          Channel 11 : 2.462 GHz          Channel 12 : 2.467 GHz          Channel 13 : 2.472 GHz          Channel 36 : 5.18 GHz          Channel 40 : 5.2 GHz          Channel 44 : 5.22 GHz          Channel 48 : 5.24 GHz          Channel 52 : 5.26 GHz          Channel 56 : 5.28 GHz          Channel 60 : 5.3 GHz          Channel 64 : 5.32 GHz          Channel 100 : 5.5 GHz          Channel 104 : 5.52 GHz          Channel 108 : 5.54 GHz          Channel 112 : 5.56 GHz          Channel 116 : 5.58 GHz          Channel 120 : 5.6 GHz          Channel 124 : 5.62 GHz          Channel 128 : 5.64 GHz          Channel 132 : 5.66 GHz          Channel 136 : 5.68 GHz          Channel 140 : 5.7 GHz          Current Frequency:5.18 GHz (Channel 36)
##### iwlist scan #######################
Channel occupancy:
      5   APs on   Frequency:2.412 GHz (Channel 1)      4   APs on   Frequency:2.437 GHz (Channel 6)      1   APs on   Frequency:2.452 GHz (Channel 9)      1   APs on   Frequency:2.462 GHz (Channel 11)      4   APs on   Frequency:5.18 GHz (Channel 36)      1   APs on   Frequency:5.5 GHz (Channel 100)
eth0      Interface doesn't support scanning.
wlan0     Scan completed :          Cell 01 - Address: <MAC 'eduroam' [AC1]>                    Channel:36                    Frequency:5.18 GHz (Channel 36)                    Quality=46/70  Signal level=-64 dBm                      Encryption key:on                    ESSID:"eduroam"                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=0000017ead72c1f1                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 02 - Address: <MAC 'kuleuven-guest' [AC2]>                    Channel:1                    Frequency:2.412 GHz (Channel 1)                    Quality=30/70  Signal level=-80 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=000001898e808c4d                    Extra: Last beacon: 24ms ago          Cell 03 - Address: <MAC 'kuleuven' [AC3]>                    Channel:1                    Frequency:2.412 GHz (Channel 1)                    Quality=30/70  Signal level=-80 dBm                      Encryption key:on                    ESSID:"kuleuven"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=000001898e802d27                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 04 - Address: <MAC 'kuleuven-guest' [AC4]>                    Channel:1                    Frequency:2.412 GHz (Channel 1)                    Quality=25/70  Signal level=-85 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000017eadc2a299                    Extra: Last beacon: 24ms ago          Cell 05 - Address: <MAC 'eduroam' [AC5]>                    Channel:1                    Frequency:2.412 GHz (Channel 1)                    Quality=23/70  Signal level=-87 dBm                      Encryption key:on                    ESSID:"eduroam"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000017eadc21103                    Extra: Last beacon: 5004ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 06 - Address: <MAC 'eduroam' [AC6]>                    Channel:1                    Frequency:2.412 GHz (Channel 1)                    Quality=30/70  Signal level=-80 dBm                      Encryption key:on                    ESSID:"eduroam"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=000001898e802035                    Extra: Last beacon: 5000ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 07 - Address: <MAC 'kuleuven-guest' [AC7]>                    Channel:6                    Frequency:2.437 GHz (Channel 6)                    Quality=32/70  Signal level=-78 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000017eaa6d65f1                    Extra: Last beacon: 24ms ago          Cell 08 - Address: <MAC 'eduroam' [AC8]>                    Channel:6                    Frequency:2.437 GHz (Channel 6)                    Quality=23/70  Signal level=-87 dBm                      Encryption key:on                    ESSID:"eduroam"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000017ea8a5828d                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 09 - Address: <MAC 'kuleuven-guest' [AC9]>                    Channel:6                    Frequency:2.437 GHz (Channel 6)                    Quality=24/70  Signal level=-86 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000017ea8a6435e                    Extra: Last beacon: 24ms ago          Cell 10 - Address: <MAC 'kuleuven' [AC10]>                    Channel:6                    Frequency:2.437 GHz (Channel 6)                    Quality=23/70  Signal level=-87 dBm                      Encryption key:on                    ESSID:"kuleuven"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000017ea8a5e427                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 11 - Address: <MAC 'RoboNet_24' [AC11]>                    Channel:9                    Frequency:2.452 GHz (Channel 9)                    Quality=24/70  Signal level=-86 dBm                      Encryption key:on                    ESSID:"RoboNet_24"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=00000d47b670d757                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK          Cell 12 - Address: <MAC 'kuleuven-guest' [AC12]>                    Channel:11                    Frequency:2.462 GHz (Channel 11)                    Quality=54/70  Signal level=-56 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s                              54 Mb/s                    Mode:Master                    Extra:tsf=0000010372f56a1a                    Extra: Last beacon: 24ms ago          Cell 13 - Address: <MAC 'kuleuven' [AC13]>                    Channel:36                    Frequency:5.18 GHz (Channel 36)                    Quality=46/70  Signal level=-64 dBm                      Encryption key:on                    ESSID:"kuleuven"                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=0000017ead726308                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported          Cell 14 - Address: <MAC 'kuleuven-guest' [AC14]>                    Channel:36                    Frequency:5.18 GHz (Channel 36)                    Quality=45/70  Signal level=-65 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=0000017ead739c28                    Extra: Last beacon: 24ms ago          Cell 15 - Address: <MAC 'eduroam' [AC15]>                    Channel:36                    Frequency:5.18 GHz (Channel 36)                    Quality=23/70  Signal level=-87 dBm                      Encryption key:on                    ESSID:"eduroam"                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=0000000034535034                    Extra: Last beacon: 4048ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : CCMP                        Pairwise Ciphers (1) : CCMP                        Authentication Suites (1) : 802.1x                       Preauthentication Supported    lo        Interface doesn't support scanning.
          Cell 16 - Address: <MAC 'kuleuven-guest' [AC16]>                    Channel:100                    Frequency:5.5 GHz (Channel 100)                    Quality=22/70  Signal level=-88 dBm                      Encryption key:off                    ESSID:"kuleuven-guest"                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s                    Mode:Master                    Extra:tsf=0000017ead8a4822                    Extra: Last beacon: 2320ms ago
##### module infos ######################
[iwldvm]filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.kolicense:        GPLauthor:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>version:        in-tree:description:    Intel(R) Wireless WiFi Link AGN driver for Linuxsrcversion:     259D494A97B601F302CD790depends:        iwlwifi,mac80211,cfg80211intree:         Yvermagic:       3.19.0-16-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5Dsig_hashalgo:   sha512parm:           force_cam:force continuously aware mode (no power saving at all) (bool)
[mac80211]filename:       /lib/modules/3.19.0-16-generic/kernel/net/mac80211/mac80211.kolicense:        GPLdescription:    IEEE 802.11 subsystemsrcversion:     F518BE1BD732F328C9E430Bdepends:        cfg80211intree:         Yvermagic:       3.19.0-16-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5Dsig_hashalgo:   sha512parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
[iwlwifi]filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.kolicense:        GPLauthor:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>version:        in-tree:description:    Intel(R) Wireless WiFi driver for Linuxfirmware:       iwlwifi-100-5.ucodefirmware:       iwlwifi-1000-5.ucodefirmware:       iwlwifi-135-6.ucodefirmware:       iwlwifi-105-6.ucodefirmware:       iwlwifi-2030-6.ucodefirmware:       iwlwifi-2000-6.ucodefirmware:       iwlwifi-5150-2.ucodefirmware:       iwlwifi-5000-5.ucodefirmware:       iwlwifi-6000g2b-6.ucodefirmware:       iwlwifi-6000g2a-5.ucodefirmware:       iwlwifi-6050-5.ucodefirmware:       iwlwifi-6000-4.ucodefirmware:       iwlwifi-7265D-10.ucodefirmware:       iwlwifi-7265-10.ucodefirmware:       iwlwifi-3165-10.ucodefirmware:       iwlwifi-3160-10.ucodefirmware:       iwlwifi-7260-10.ucodefirmware:       iwlwifi-8000-10.ucodesrcversion:     ADFD966DF2A9D56EE93BE48depends:        cfg80211intree:         Yvermagic:       3.19.0-16-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5Dsig_hashalgo:   sha512parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)parm:           fw_restart:restart firmware in case of error (default true) (bool)parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)parm:           nvm_file:NVM file name (charp)parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)parm:           power_save:enable WiFi power management (default: disable) (bool)parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
[cfg80211]filename:       /lib/modules/3.19.0-16-generic/kernel/net/wireless/cfg80211.kodescription:    wireless configuration supportlicense:        GPLauthor:         Johannes Bergsrcversion:     268045EBCFAFDADD136DCF6depends:        intree:         Yvermagic:       3.19.0-16-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5Dsig_hashalgo:   sha512parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
##### module parameters #################
[iwldvm]force_cam: Y
[mac80211]beacon_loss_count: 7ieee80211_default_rc_algo: minstrel_htmax_nullfunc_tries: 2max_probe_tries: 5minstrel_vht_only: Yprobe_wait_ms: 500
[iwlwifi]11n_disable: 0amsdu_size_8K: 0antenna_coupling: 0bt_coex_active: Yfw_monitor: Nfw_restart: Yled_mode: 0nvm_file: (null)power_level: 0power_save: Nswcrypto: 0uapsd_disable: Ywd_disable: 1
[cfg80211]cfg80211_disable_40mhz_24ghz: Nieee80211_regdom: 00
##### /etc/modules ######################
##### modprobe options ##################
[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci
[/etc/modprobe.d/blacklist.conf]blacklist evbugblacklist usbmouseblacklist usbkbdblacklist eepro100blacklist de4x5blacklist eth1394blacklist snd_intel8x0mblacklist snd_aw2blacklist i2c_i801blacklist prism54blacklist bcm43xxblacklist garmin_gpsblacklist asus_acpiblacklist snd_pcspblacklist pcspkrblacklist amd76x_edac
[/etc/modprobe.d/blacklist-rare-network.conf]alias net-pf-3 offalias net-pf-6 offalias net-pf-9 offalias net-pf-11 offalias net-pf-12 offalias net-pf-19 offalias net-pf-21 offalias net-pf-36 off
[/etc/modprobe.d/iwlwifi.conf]remove iwlwifi \(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \&& /sbin/modprobe -r mac80211
[/etc/modprobe.d/mlx4.conf]softdep mlx4_core post: mlx4_en
[/etc/modprobe.d/modesetting.conf]options cirrus modeset=1options mgag200 modeset=1
##### rc.local ##########################
exit 0
##### pm-utils ##########################
##### udev rules ########################
[/etc/udev/rules.d/70-persistent-net.rules]# PCI device 0x8086:0x153a (e1000e)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"# PCI device 0x8086:0x088e (iwlwifi)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
##### dmesg #############################
[  419.476276] wlan0: authenticate with <MAC 'eduroam' [AN21]>[  419.478785] wlan0: direct probe to <MAC 'eduroam' [AN21]> (try 1/3)[  419.682756] wlan0: direct probe to <MAC 'eduroam' [AN21]> (try 2/3)[  419.886846] wlan0: direct probe to <MAC 'eduroam' [AN21]> (try 3/3)[  420.091037] wlan0: authentication with <MAC 'eduroam' [AN21]> timed out[  420.393534] wlan0: authenticate with <MAC 'eduroam' [AC6]>[  420.395451] wlan0: send auth to <MAC 'eduroam' [AC6]> (try 1/3)[  420.396802] wlan0: authenticated[  420.399446] wlan0: associate with <MAC 'eduroam' [AC6]> (try 1/3)[  420.403510] wlan0: RX AssocResp from <MAC 'eduroam' [AC6]> (capab=0x411 status=0 aid=101)[  420.405570] wlan0: associated[  673.397382] wlan0: authenticate with <MAC 'eduroam' [AC1]>[  673.399323] wlan0: send auth to <MAC 'eduroam' [AC1]> (try 1/3)[  673.451911] wlan0: authenticated[  673.453875] wlan0: associate with <MAC 'eduroam' [AC1]> (try 1/3)[  673.456037] wlan0: RX AssocResp from <MAC 'eduroam' [AC1]> (capab=0x11 status=0 aid=21)[  673.457910] wlan0: associated[  673.555865] wlan0: Limiting TX power to 18 dBm as advertised by <MAC 'eduroam' [AC1]> (repeated 6 times)
########## wireless info END ############
```

The output of ifconfig is:

eth0      Link encap:Ethernet  HWaddr ec:f4:bb:6b:26:04  
          inet6 addr: fe80::eef4:bbff:fe6b:2604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59811 errors:0 dropped:429 overruns:0 frame:0
          TX packets:412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8071016 (8.0 MB)  TX bytes:80215 (80.2 KB)
          Interrupt:20 Memory:f7d00000-f7d20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:408934 (408.9 KB)  TX bytes:408934 (408.9 KB)


wlan0     Link encap:Ethernet  HWaddr 80:00:0b:29:ab:44  
          inet addr:10.43.125.165  Bcast:10.43.127.255  Mask:255.255.192.0
          inet6 addr: 2a02:2c40:400:0:60d3:e137:4df6:f29d/64 Scope:Global
          inet6 addr: fe80::8200:bff:fe29:ab44/64 Scope:Link
          inet6 addr: 2a02:2c40:400::1:e086/128 Scope:Global
          inet6 addr: 2a02:2c40:400:0:8200:bff:fe29:ab44/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5026041 (5.0 MB)  TX bytes:3784263 (3.7 MB)




What else should I do to diagnose my problem?

---

### Post by Vladlenin5000 on 2015-05-06
Hi and welcome.

Are you able to connect with other computers and the same cable?
Don't you need some authentication for network?

---

### Post by Viktor_Ferenczi on 2015-05-15
It happens to me as well. 

Ethernet connection works only occasionally.

It is a mainboard port on an EVGA X99 Micro mainboard, reported as **Intel I217-LM** by **lspci**.

Ethernet connection works perfectly all the time in Windows on the same machine (dual boot).

It is happening to a brand new Ubuntu 15.04 installation (default Intel x86 64bit ISO).

Adapter does not get an IP from DHCP server, so I ended up setting a static IP and network parameters.

Then in syslog it complains about temporary failure in name resolution, no other network related errors logged.

I have tried with no success:
- ping 8.8.8.8 did not work, so it is not just the name resolution
- pinging the default gateway did not go through either
- Restarting networking via Network Manager
- Physically re-plugging the network card.
- Unloading/loading e1000e driver.
- Static IPv4 configuration (IP, netmask, DNS).
- Disabling IPv6
- Restarting machine
- Hard restarting by reset

I tried **tcpdump -ni eth0** to capture traffic and saw only outgoing packets. Nothing is coming in.

I tried **ethtool -t eth0** to run the adapter self-test and it reports FAIL. The **Loopback test fails with code 13**. But the hardware is not defective, it works with Windows perfectly and it also worked perfectly some 3 times already in this Linux installation as well. (Maybe the Moon phase? ;) )

I'm pretty sure it is a software issue, likely a driver problem, since the same hardware works perfectly in Windows all the time.

Currently it is not possible to try latest e1000e driver due to build error:
[https://sourceforge.net/p/e1000/bugs/469/](https://sourceforge.net/p/e1000/bugs/469/)
(Unless we can fix it.)

**Workaround: **It seems that turning off the machine completely (plugging out the power cable) for a minute helps, as long as I start Linux after powering up. Adapter self-test (ethtool -t eth0) reports no failure in this case.  It works for me, at least.

If I reboot after a Windows session or don't power off the machine completely, then the adapter does not work in Linux. I guess we see a problem with re-initializing the adapter after previous use.

I also tried searching for a permanent solution based on the above, but found none so far.

---

### Post by chili555 on 2015-05-15
The link you gave us describes a bug in the driver e1000. Your device uses the driver e1000e, a different driver. However, the latest stable e1000e doesn't compile either.

A promising thread I read suggests that auto-negotiation may be the issue. I therefore suggest you try:
```
sudo ethtool -s eth0 autoneg off speed 100

```
Test for a day or so, and if it helps, we'll drop the setting into /etc/rc.local.

---

### Post by Viktor_Ferenczi on 2015-05-15
Thank you for the workaround. The e1000e developers promised a new version in a few days which will build on latest kernels up to 4.1rc1.

---

### Post by diablo666 on 2016-01-14
Hi there, just installed ubuntu 15.10, used the trick suggested by Viktor_Ferenczi ti apt-get update and apt-get upgrade.

Problem persist... someone got some news about that problem?

---


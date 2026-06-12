---
title: "Broadcom BCM4350/16.04/4.7.0-Wireless still says connected but stopped working"
date: 2016-08-15
forum: Networking &amp; Wireless
---

### Post by steelers743 on 2016-08-15
So the issue I am having is my wireless worked fine for a bit but now it still says connected but has no internet connection on my brand new Lenovo Yoga 710. I am sure the hardware still works as I am able to boot into windows and use the wireless just fine. I am new to linux so I am sure you all can help me solve this issue.

I installed 16.04 and on my Lenovo Yoga 710 it was having ACPI boot issue but I was able to fix that by updating to kernel 4.7.0. But after a few days on 4.7.0 the internet just stopped working, it still says it is connected though but no sites will pull up. I figured some update just messed up and didn't have anything important on the system yet so I just reinstalled 16.04 and updated the kernel again. But the issue just happened again and I am stuck on how to fix it.

I don't have any way to get wired internet on that laptop but I am able to use my secondary laptop and a USB to transfer things.
Here is the printout from the script. Thanks
```

########## wireless info START ##########


Report from: 15 Aug 2016 17:16 EDT -0400


Booted last: 15 Aug 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.7.0-040700-generic #201608021801 SMP Tue Aug 2 22:03:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, acpi=noirq, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM4350 802.11ac Wireless Network Adapter [14e4:43a3] (rev 08)
	Subsystem: Lenovo BCM4350 802.11ac Wireless Network Adapter [17aa:075a]
	Kernel driver in use: brcmfmac


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a5c:6414 Broadcom Corp. 
Bus 001 Device 002: ID 04f2:b578 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


brcmfmac              249856  0
brcmutil               16384  1 brcmfmac
cfg80211              569344  1 brcmfmac
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
rfkill                 24576  8 cfg80211,ideapad_laptop,bluetooth
mmc_core              135168  2 brcmfmac,rtsx_pci_sdmmc
usbcore               241664  7 uas,btusb,brcmfmac,uvcvideo,usb_storage,xhci_hcd,xhci_pci
wmi                    16384  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          inet addr:192.168.1.244  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b4ae:536:bac0:9298/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13539 (13.5 KB)  TX bytes:43002 (43.0 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"74386"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: <MAC '74386' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=31 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


##### resolv.conf #######################


nameserver 10.9.0.1
nameserver 10.8.0.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2312     1  0 17:14 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4350 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         brcmfmac
GENERAL.DRIVER-VERSION:                 7.35.180.119
GENERAL.FIRMWARE-VERSION:               01-e791c176
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     74386 1
GENERAL.CON-UUID:                       8dda5b85-bfbf-4ba8-852f-5a20d2a087f2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     24 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,2,3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   69c0f0b3-8bb2-4dd9-8768-8b8f019ea616 | 74386 3
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   8dda5b85-bfbf-4ba8-852f-5a20d2a087f2 | 74386 1
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   b3aa93be-20c3-4ad1-b08a-29943926d310 | 74386 2
IP4.ADDRESS[1]:                         192.168.1.244/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.244
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1471382118
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = steelCurtain
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::b4ae:536:bac0:9298/64
IP6.GATEWAY:                            


SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FINALLY           <MAC 'FINALLY' [AC13]>  Infra  10    2457 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                <MAC '' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
74386             <MAC '74386' [AC1]>  Infra  40    5200 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Gamecocks 2G      <MAC 'Gamecocks 2G' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
xfinitywifi       <MAC 'xfinitywifi' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --         no        
--                <MAC '' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        
xfinitywifi       <MAC 'xfinitywifi' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --         no        
Creighton_almond  <MAC 'Creighton_almond' [AC6]>  Infra  3     2422 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
Schnitzel         <MAC 'Schnitzel' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
xfinitywifi       <MAC 'xfinitywifi' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  --         no        
HOME-81DE-2.4     <MAC 'HOME-81DE-2.4' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
HOME-5A32         <MAC 'HOME-5A32' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
HOME-2482         <MAC 'HOME-2482' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
Utes              <MAC 'Utes' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
--                <MAC '' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
Gamecocks5g       <MAC 'Gamecocks5g' [AC15]>  Infra  36    5180 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
HOME-4982         <MAC 'HOME-4982' [AN17]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
--                <MAC '--' [AN18]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
Redjakal24        <MAC 'Redjakal24' [AC12]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
--                <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
xfinitywifi       <MAC 'xfinitywifi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --         no        
HOME-3727-2.4     <MAC 'HOME-3727-2.4' [AN22]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
HOME-9052_2GEXT   <MAC 'HOME-9052_2GEXT' [AN23]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1       no        
--                <MAC '--' [AN24]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
Creighton         <MAC 'Creighton' [AN25]>  Infra  8     2447 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
Redjakal5         <MAC 'Redjakal5' [AC19]>  Infra  149   5745 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
HOME-D88C-5       <MAC 'HOME-D88C-5' [AC21]>  Infra  161   5805 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2  no        
xfinitywifi       <MAC 'xfinitywifi' [AC17]>  Infra  40    5200 MHz  54 Mbit/s  29      &#9602;___  --         no        
xfinitywifi       <MAC 'xfinitywifi' [AC23]>  Infra  161   5805 MHz  54 Mbit/s  29      &#9602;___  --         no        
xfinitywifi       <MAC 'xfinitywifi' [AC22]>  Infra  161   5805 MHz  54 Mbit/s  29      &#9602;___  --         no        
--                <MAC '--' [AN31]>  Infra  161   5805 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
--                <MAC '' [AC18]>  Infra  44    5220 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
xfinitywifi       <MAC 'xfinitywifi' [AN33]>  Infra  44    5220 MHz  54 Mbit/s  27      &#9602;___  --         no        
Utes              <MAC 'Utes' [AN34]>  Infra  44    5220 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
Mola              <MAC 'Mola' [AC20]>  Infra  161   5805 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
Creighton Jays    <MAC 'Creighton Jays' [AN36]>  Infra  36    5180 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
xfinitywifi       <MAC 'xfinitywifi' [AN37]>  Infra  157   5785 MHz  54 Mbit/s  24      &#9602;___  --         no        
--                <MAC '--' [AN38]>  Infra  149   5745 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
66029648A         <MAC '66029648A' [AN39]>  Infra  149   5745 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
HOME-51D2-5       <MAC 'HOME-51D2-5' [AN40]>  Infra  157   5785 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/74386 2]] (600 root)
[connection] id=74386 2 | type=wifi | permissions=user:steel:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=74386
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/74386 1]] (600 root)
[connection] id=74386 1 | type=wifi | permissions=user:steel:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=74386
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/74386 3]] (600 root)
[connection] id=74386 3 | type=wifi | permissions=user:steel:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=74386
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/74386]] (600 root)
[connection] id=74386 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=74386
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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


wlp1s0    32 channels in total; available frequencies :
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
          Channel 140 : 5.7 GHz
          Current Frequency:5.2 GHz (Channel 40)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.22 GHz (Channel 44)
      3   APs on   Frequency:5.2 GHz (Channel 40)
      1   APs on   Frequency:5.745 GHz
      4   APs on   Frequency:5.805 GHz


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC '74386' [AC1]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"74386"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
          Cell 04 - Address: <MAC 'HOME-81DE-2.4' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"HOME-81DE-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'xfinitywifi' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
          Cell 06 - Address: <MAC 'Creighton_almond' [AC6]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Creighton_almond"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'xfinitywifi' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '10FX11190550' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"10FX11190550"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Redjakal24' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Redjakal24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'FINALLY' [AC13]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"FINALLY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Gamecocks 2G' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Gamecocks 2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Gamecocks5g' [AC15]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Gamecocks5g"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'HOME-81DE-5' [AC16]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HOME-81DE-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'xfinitywifi' [AC17]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
          Cell 18 - Address: <MAC '' [AC18]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Redjakal5' [AC19]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Redjakal5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Mola' [AC20]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Mola"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'HOME-D88C-5' [AC21]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HOME-D88C-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'xfinitywifi' [AC22]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
          Cell 23 - Address: <MAC 'xfinitywifi' [AC23]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago


##### module infos ######################


[brcmfmac]
filename:       /lib/modules/4.7.0-040700-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
depends:        mmc_core,brcmutil,cfg80211,usbcore
intree:         Y
vermagic:       4.7.0-040700-generic SMP mod_unload modversions 
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:Do not use internal roaming engine (int)


[brcmutil]
filename:       /lib/modules/4.7.0-040700-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
depends:        
intree:         Y
vermagic:       4.7.0-040700-generic SMP mod_unload modversions 


[cfg80211]
filename:       /lib/modules/4.7.0-040700-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       4.7.0-040700-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    9.161669] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6414.hcd failed with error -2
[    9.161673] Bluetooth: hci0: BCM: Patch brcm/BCM-0a5c-6414.hcd not found
[    9.175954] brcmfmac 0000:01:00.0: assigned PCI INT A -> IRQ 11
[    9.175962] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:15.0
[    9.175971] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:1d.0
[    9.175976] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:1f.3
[    9.175981] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:1f.4
[    9.282323] brcmfmac 0000:01:00.0: Direct firmware load for brcm/brcmfmac4350-pcie.txt failed with error -2
[    9.698575] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Oct 22 2015 06:16:26 version 7.35.180.119 (r594535) FWID 01-e791c176
[    9.747257] brcmfmac 0000:01:00.0 wlp1s0: renamed from wlan0
[    9.995846] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[   33.420603] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready


########## wireless info END ############



```

---

### Post by steelers743 on 2016-08-15
I believe it could be a firmware issue from this part

##### dmesg #############################


[    9.161669] bluetooth hci0: Direct firmware load for brcm/BCM-0a5c-6414.hcd failed with error -2
[    9.161673] Bluetooth: hci0: BCM: Patch brcm/BCM-0a5c-6414.hcd not found
[    9.175954] brcmfmac 0000:01:00.0: assigned PCI INT A -> IRQ 11
[    9.175962] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:15.0
[    9.175971] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:1d.0
[    9.175976] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:1f.3
[    9.175981] brcmfmac 0000:01:00.0: sharing IRQ 11 with 0000:00:1f.4
[    9.282323] brcmfmac 0000:01:00.0: Direct firmware load for brcm/brcmfmac4350-pcie.txt failed with error -2
[    9.698575] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Oct 22 2015 06:16:26 version 7.35.180.119 (r594535) FWID 01-e791c176
[    9.747257] brcmfmac 0000:01:00.0 wlp1s0: renamed from wlan0
[    9.995846] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[   33.420603] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

not sure how to fix it tho...any help?

---

### Post by steelers743 on 2016-08-20
Any help for my issue?

---

### Post by evgenymarkov on 2016-08-21
Just replace the Broadcom module to Intel 8260 or 7265.

---

### Post by steelers743 on 2016-08-21
> **evgenymarkov said:**
> Just replace the Broadcom module to Intel 8260 or 7265.
Although this could fix my issue I am against replacing a perfectly fine working piece of hardware on my brand new laptop to get around a bug at this time.

---

### Post by steelers743 on 2016-08-21
I was able to replicate the issue with another fresh install and upgrade to longterm kernel 4.4.19. The forum isn't letting me paste the script output though.
I fresh installed, upgraded kernel to fix the acpi bug with 4.4.0 and 4.4.19 seemed to boot fine. After a few hours the computer frooze up and on reboot same issue, wireless show connected to my network but opening a browser just spins.

No on has had this issue before or can think of what is maybe causing it?

---


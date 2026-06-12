---
title: "Simple When When I Plug in Eternet, WiFI gets Simply gets Screwed Up - Weird !"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by markackerman8@gmail.com on 2016-02-15
Ok, so I am quite experience in Ubuntu - 7 years helping the world change over from Windows- please return the favour, Thanks, Mark.

As I said for over a week my Ubuntu-Gnome Laptop kills the routers WiFi as soon as, and ONLY when, I plug my ethernet cable into my running version of Ubuntu-Gnome. As soon as I disable the "Wired Connection" or Unplug it, BAMM, it is back.  This has got to be solvable as it is quite unique.

I EVEN replaced my router 2 days ago, and EVEN reinstalled Ubuntu-Gnome today, and the problem reappeared.  Please help - getting quite frustrated.:o
here is my wifi info from [http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

p.s. if anyone can tell me how to make this code smaller (in a scrolling small window) like I have seen many times please enlighten  me, 
(Edit - It compacted it automatically cool - should have known)

Cheers, Mark
```

########## wireless info START ##########

Report from: 15 Feb 2016 14:03 PST -0800

Booted last: 15 Feb 2016 00:00 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-29-generic #34-Ubuntu SMP Mon Feb 8 16:57:47 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME

##### lspci #############################

07:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
	DeviceName: Intel(R) Wi-Fi Link 2330
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]

0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company Device [103c:1966]

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:571a Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 006: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 005: ID 0eef:a820 D-WAV Scientific Co., Ltd 
Bus 001 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
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

b43                   417792  0
bcma                   53248  1 b43
ssb                    65536  1 b43
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
iwldvm                233472  0
mac80211              733184  2 b43,iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              548864  4 b43,iwlwifi,mac80211,iwldvm
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:569:7508:9a00:<IP6 'eno1' [IF]>/64 Scope:Global
          inet6 addr: 2001:569:7508:9a00:6dad:7245:2312:ee9f/64 Scope:Global
          inet6 addr: fe80::<IP6 'eno1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59557 errors:0 dropped:1 overruns:0 frame:0
          TX packets:209089 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68848751 (68.8 MB)  TX bytes:235219287 (235.2 MB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7844323 (7.8 MB)  TX bytes:675014 (675.0 KB)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.1.1
search telus

##### network managers ##################

Installed:

	NetworkManager

Running:

root       679     1  0 11:53 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:0f:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a89b1249-c1f4-4ad6-8eb4-05c0679e802c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/12
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a89b1249-c1f4-4ad6-8eb4-05c0679e802c | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.64/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DNS[2]:                             75.153.176.9
IP4.DOMAIN[1]:                          telus
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1455659322
DHCP4.OPTION[9]:                        domain_name = telus
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.64
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.254 75.153.176.9
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2001:569:7508:9a00:6dad:7245:2312:ee9f/64
IP6.ADDRESS[2]:                         2001:569:7508:9a00:<IP6 'eno1' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'eno1' [IF]>/64
IP6.GATEWAY:                            fe80::4e8b:30ff:fe24:7758
IP6.DNS[1]:                             2001:568:ff09:10a::53
IP6.DNS[2]:                             2001:568:ff09:10b::53
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:568:ff09:10a::53 2001:568:ff09:10b::53
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:7c:7e:d5:8:6a:39:fd:44:2c:77:be:1:fa:aa:b9:8f

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 2230 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-29-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d3c0d82d-0ee3-43f5-a7a2-1d236533bfc4 | AcksSSID
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   ec25a363-ee65-44bf-a6f1-6c8a4d13f7bd | AcksSSID-2

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
AcksSSID-2     <MAC 'AcksSSID-2' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
AcksSSID-2.4G  <MAC 'AcksSSID-2.4G' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
AcksSSID       <MAC 'AcksSSID' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AcksSSID]] (600 root)
[connection] id=AcksSSID | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=AcksSSID
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AcksSSID-2]] (600 root)
[connection] id=AcksSSID-2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=AcksSSID-2
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Vancouver (based on set time zone)

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

eno1      no frequency information.

lo        no frequency information.

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

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'AcksSSID-2' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"AcksSSID-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017dcee6016
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'AcksSSID' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"AcksSSID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017dcee1ed0
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'AcksSSID-2.4G' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"AcksSSID-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000181c5b0f63
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/4.2.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
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
srcversion:     EBCFBB62711AEC753D1C919
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512
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

[bcma]
filename:       /lib/modules/4.2.0-29-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/4.2.0-29-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     B9B638C64CE9AC05F1A1903
depends:        
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512

[iwldvm]
filename:       /lib/modules/4.2.0-29-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     B715639CA9F6E3BA25A93FD
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.2.0-29-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     2AFF7BF1EB0D33D3ACDC867
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-29-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FF:65:F9:98:FE:FA:F1:09:31:D5:A5:55:D8:66:EF:A1:78:E4:EC:E1
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

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

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 7243.867106] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7244.458662] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7244.509885] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7244.789061] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7245.065874] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7245.646001] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7256.356872] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7256.381084] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7256.498644] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7256.707032] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7257.220565] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7268.887688] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7469.666925] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7469.707583] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7469.870451] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7470.278884] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7470.578478] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7481.209006] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7481.223828] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7481.579609] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7481.864388] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7482.267766] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7494.067643] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7494.634525] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7494.709596] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7494.824181] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7495.284219] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7495.809839] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7506.482647] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7506.506799] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7506.878195] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7507.166945] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7507.434617] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7519.087839] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7519.662052] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7519.700030] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7520.506605] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7520.651241] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7520.755310] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7531.399794] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7531.402262] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7531.912065] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7531.940186] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7532.061243] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7544.108502] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7544.715129] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7544.716779] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7544.996788] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7545.393368] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7545.631062] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7561.821454] wlo1: authenticate with <MAC 'AcksSSID-2' [AC1]>
[ 7561.833553] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 1/3)
[ 7561.989248] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 2/3)
[ 7562.187228] wlo1: send auth to <MAC 'AcksSSID-2' [AC1]> (try 3/3)
[ 7562.268465] wlo1: authentication with <MAC 'AcksSSID-2' [AC1]> timed out
[ 7569.127942] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7569.691207] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7569.745497] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7569.933357] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7570.410480] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7570.922143] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7581.510120] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7581.530898] wlo1: direct probe to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7581.732082] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7581.855365] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7581.910080] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7594.148228] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7594.713796] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7594.763026] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7594.878693] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7595.703343] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7595.947980] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7606.611738] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7606.632200] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7606.780495] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7607.147168] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7607.800510] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7619.168219] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7619.814127] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7619.868844] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7620.034912] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7620.699410] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7621.002184] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7631.672124] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7631.685937] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7632.236590] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7632.519113] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7632.689050] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7644.188188] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7644.726045] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7644.794934] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7645.424981] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7645.731545] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7645.867573] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7656.474743] wlo1: authenticate with <MAC 'AcksSSID' [AC2]>
[ 7656.497558] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 1/3)
[ 7657.091030] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 2/3)
[ 7657.383563] wlo1: send auth to <MAC 'AcksSSID' [AC2]> (try 3/3)
[ 7657.582148] wlo1: authentication with <MAC 'AcksSSID' [AC2]> timed out
[ 7669.208951] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready

########## wireless info END ############

```

I will try anything- this is killing me.

Thanks in advance, Mark

---

### Post by lensman3 on 2016-02-15
Fishing here:  Your eno1 interface is the wired interface and it has two 2001:69 IPv6 address plus the private network IP number.  Could this be screwing up the router.  Is your IP provider IPv6 ready?  Try turning off IPv6 in network manager.  Does your router have a IPv6 6to4 switch in one of the screens?  I'm a "virgin" in the IPv6 world and I think the 2001 are transition tunneling used by providers getting the IPv6 network up and running.  But if you are getting these two IPv6 numbers assigned by your router and IP provider, then this laptop is open to the world!  Does "ip6tables -L -nv" show a IPv6 firewall?  

If your router wireless can't do IPv6 then it might just stop working as a failsafe.  

I read someplace that if eth and wifi were working at the same time, one of the interfaces had a higher Metric than the other so packets were routed over that interface instead of the other.  

This is rather extreme but delete network-manager and hand edit "/etc/network/interfaces".  Use "ifup" and "ifdown" until you get the network right.

---

### Post by markackerman8@gmail.com on 2016-02-15
Thanks, for the reply,

as it stands a 3rd re-install of Ubuntu-Gnome has fixed the problem, now I am slowly adding all my programs to see which one is "screwing with the Router".

1st/  I thought it must be Steam, or specifically Steam Link, 
2nd/ I thought it was a fried router
now it seems it is neither (still suspecting Steam Link for the moment .... but with Steam not running (on the last previous problem setup) it was still an issue

thanks for your help ... just the same

---

### Post by Hadaka on 2016-02-15
Hi,your wireless report shows.
Wireless..[0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887 .. Intel card
Wired......[0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411  Ethernet Controller ..Realtek card
There are no Broadcom cards listed and you have B43 driver loaded. That needs to be removed,Please do..
```
sudo apt-get remove --purge firmware-b43-installer
```
Next the dmesg section of the report shows....access points.. AcksSSID and AcksSSID-2 cycling trying to connect. I would suggest
removing one or the other in your network settings ubtill you get your situation resolved.
Then. your country code is not defined and marked 00 default, this can cause connection problems.. Please do..
```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
Finally the wired connection disabling the wireless is a computer option that can usually be set  to do nothing or disable in bios
check your computers manual for access to your bios.
good luck.

---

### Post by markackerman8@gmail.com on 2016-02-16
Hadaka ,

You are my Ubuntu Addict Hero,

Now I should mention as I did before your post that the problem is solved, or at least gone away with a 3rd re-install.  So and BUT this makes me even more  appreciative of our efforts, as I am an Ubuntu Addict too and love to learn from these rare episodes.

Now, w.r.t. the b43, I installed it following blindly some other suggestions, kinda dumb of me.  But it did not (Obviously) solve the problem or make it worse, **so was NOT the cause.**

The router has and 5G Extender gives it 4 possible SSID's so cycling them seems normal as I had more than one set to automatically connect, as it would normally go the the strongest at the time and stop cycling.  **SO this is NOT the problem**.

W.r.t the country code, I am now going inot the following script to see if it different, but I doubt that is the issue, though thanks just the same as I am learning something new - AWESOME :p.


Here is the network troubleshooting script now that the re-install has been done and it SEEMS fixed.  Perhaps you can help me find the difference that caused the problem on 2 installs in one week.  Remember the problem seemingly must be linked to the "wired" connection, as :
1/ when it (the wired connection) was unplugged, the problem immediately dissolved ... went away. Repeatedly
2/ if the "wired connection" was disabled it also solved the problem.
3/ enabling/ disabling/ connecting any/ disconnecting any wifi with or without wired connection had no effect.

Weird HUH!  :o
Thanks again Hadaka, here is the script, Happy Puzzle Solving, Mark
p.s. may I ask where you are from - cool name!  :D
```

########## wireless info START ##########

Report from: 16 Feb 2016 06:54 PST -0800

Booted last: 16 Feb 2016 00:00 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME

##### lspci #############################

07:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
	DeviceName: Intel(R) Wi-Fi Link 2330
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]

0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company Device [103c:1966]

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:571a Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 006: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 005: ID 0eef:a820 D-WAV Scientific Co., Ltd 
Bus 001 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
iwldvm                233472  0
mac80211              733184  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              548864  3 iwlwifi,mac80211,iwldvm
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:569:7508:9a00:<IP6 'eno1' [IF]>/64 Scope:Global
          inet6 addr: 2001:569:7508:9a00:9d82:9da5:4cdf:395a/64 Scope:Global
          inet6 addr: fe80::<IP6 'eno1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21910307 (21.9 MB)  TX bytes:4499915 (4.4 MB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28900 (28.9 KB)  TX bytes:29183 (29.1 KB)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.1.1
search telus

##### network managers ##################

Installed:

	NetworkManager
	Wicd

Running:

root       787     1  0 02:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:0f:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       718e521f-e5b8-46ae-a53a-4862e076365c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   718e521f-e5b8-46ae-a53a-4862e076365c | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.64/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DNS[2]:                             75.153.176.9
IP4.DOMAIN[1]:                          telus
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1455703784
DHCP4.OPTION[9]:                        domain_name = telus
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.64
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.254 75.153.176.9
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2001:569:7508:9a00:9d82:9da5:4cdf:395a/64
IP6.ADDRESS[2]:                         2001:569:7508:9a00:<IP6 'eno1' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'eno1' [IF]>/64
IP6.GATEWAY:                            fe80::4e8b:30ff:fe24:7758
IP6.DNS[1]:                             2001:568:ff09:10a::53
IP6.DNS[2]:                             2001:568:ff09:10b::53
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:568:ff09:10a::53 2001:568:ff09:10b::53
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:48:28:f3:78:92:1f:74:78:18:9b:12:1d:f3:e6:4d:6f

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 2230 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-27-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AcksSSID]] (600 root)
[connection] id=AcksSSID | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=AcksSSID
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Vancouver (based on set time zone)

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

eno1      no frequency information.

lo        no frequency information.

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

wlo1      Interface doesn't support scanning : Network is down

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     B715639CA9F6E3BA25A93FD
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FBF6EA073A00B4F3836226E
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     75997E53B9CC3BD2CA79F3B
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.553466] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.553469] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.553470] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.553472] iwlwifi 0000:07:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    3.553570] iwlwifi 0000:07:00.0: L1 Enabled - LTR Disabled
[    3.600535] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    3.621085] iwlwifi 0000:07:00.0 wlo1: renamed from wlan0
[    4.250784] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    4.295152] r8169 0000:0f:00.0 eno1: link down (repeated 2 times)
[    4.295213] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    4.297394] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    4.297487] iwlwifi 0000:07:00.0: L1 Enabled - LTR Disabled
[    4.305223] iwlwifi 0000:07:00.0: Radio type=0x2-0x0-0x0
[    4.547692] iwlwifi 0000:07:00.0: L1 Enabled - LTR Disabled
[    4.555456] iwlwifi 0000:07:00.0: Radio type=0x2-0x0-0x0
[    4.613627] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[    5.111146] wlo1: authenticate with <MAC address>
[    5.122892] wlo1: send auth to <MAC address> (try 1/3)
[    5.137345] wlo1: authenticated
[    5.137436] wlo1: waiting for beacon from <MAC address>
[    5.229390] wlo1: associate with <MAC address> (try 1/3)
[    5.234816] wlo1: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=3)
[    5.254999] wlo1: associated
[    5.255027] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[    7.405565] r8169 0000:0f:00.0 eno1: link up
[    7.405574] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[  147.942357] wlo1: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

---

### Post by markackerman8@gmail.com on 2016-02-16
Hadaka,

Here are the before (BAD), and After (Good) differences, perhaps you can enlighten me wher, if anywhere you can see the past problem, AND what could have (can) cause it.

Cheers, Mark

##### route #############################  (GOOD)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

(BAD)
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eno1
**169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1**
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
------------------------------------------------------------------------------------------------

##### NetworkManager info ###############
(BAD) had extra line with:
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
-------------------------------------------------------------------------------------------------

and this section has tomany differences to note:
##### dmesg #############################

Thanks again. Mark :o

---

### Post by Hadaka on 2016-02-16
Hi,You have made so many changes and reloaded the operating
system three or more times, so it would be very difficult to figure
out exactly what transpired once the new load overwrites the older
version,sorry i cant pinpoint it for you. If you are satisfied with your
results,please mark your thread solved.
thanks.

*Note..when you log in, on the second screen where it asks you if you want to log in
you have a choice to login in with a user name,,,or your e mail address
if you dont want to get millions of spam mail i would suggest you uncheck that and check your user name.

---


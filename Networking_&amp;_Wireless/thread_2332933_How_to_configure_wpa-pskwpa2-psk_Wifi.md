---
title: "How to configure wpa-psk/wpa2-psk Wifi"
date: 2016-08-05
forum: Networking &amp; Wireless
---

### Post by pedro.desouza on 2016-08-05
Hello there,

I'm having some trouble connecting to wpa-psk wifi networks. After a fast research I found that wlan0 flag does not exist. How should a proceed?

Background info:

OS: Ubuntu 16.04 LTS
notebook: Lenovo ideapad 300-15isk
Wifi chipset: Intel® Wireless 3165
kernel version: 4.4+
installed drivers: iwlwifi-7265D-16.ucode and iwlwifi-7265-16.ucode
```
iwconfig lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on



```

Thanks for the attention :)

---

### Post by jeremy31 on 2016-08-06
*Thread moved to **Networking & Wireless**.*
Check ```
iwlist scan | egrep -i 'ssid|cipher'
```
Below where your SSID is listed you want to see
```
IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```
If you see TKIP listed, it is likely causing issues
Also predictable network naming scheme is in use now and your wlan0 has been replaced with wlp2s0

---

### Post by pedro.desouza on 2016-08-08
```

iwlist scan | egrep -i 'ssid|cipher'
lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


                    ESSID:"DC-Pos"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP



```

At the University using a wpa/wpa2 enterprise encrypted WiFi I successfully connected as you can see above. Still I cant' connected  at home. I you wiil dp a iwlist scan and post the result when I arrive at home.

Here is what I got: 
```
iwconfig lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"Padoka"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:21:91:73:DE:64   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0



```

and

```
iwlist scan | egrep -i 'ssid|cipher'lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.



```

---

### Post by jeremy31 on 2016-08-09
See the wireless script link in my signature and post your results, a bit strange that it didn't pick up any access points at home

---

### Post by pedro.desouza on 2016-08-11
I ran the script with a wired connection and the results are attached.

As expected I tried running it after attempting wireless connection and didn't work out:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info

--2016-08-11 12:31:44--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... failed: Temporary failure in name resolution.
wget: unable to resolve host address ‘github.com’

```

wireless script on a wired connection:
[ATTACH]270655[/ATTACH]

---

### Post by pedro.desouza on 2016-08-19
Apologies for not posting the full content but I thought it was too large. Please notify me if you prefer posting the content instead of the *.tar.gz file.

---

### Post by howefield on 2016-08-19
> **pedro.desouza said:**
> Apologies for not posting the full content but I thought it was too large. Please notify me if you prefer posting the content instead of the *.tar.gz file.

Post the content between code tags or paste to [pastebin]("http://pastebin.ubuntu.com/") and link here.

---

### Post by pedro.desouza on 2016-08-22
Thanks for the aid. Here is the link for pastebin:
[http://pastebin.ubuntu.com/23078408/](http://pastebin.ubuntu.com/23078408/)

---

### Post by pedro.desouza on 2016-08-31
```

########## wireless info START ##########

Report from: 11 Aug 2016 12:30 BRT -0300

Booted last: 11 Aug 2016 00:00 BRT -0300

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3837]
	Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 30)
	Subsystem: Lenovo Device [17aa:4035]
	Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e360 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04f2:b50e Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915_bpo,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.0.179  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b70:f55e:43b5:431e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2945929 (2.9 MB)  TX bytes:625318 (625.3 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:226 (226.0 B)  TX bytes:306 (306.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2807     1  0 12:14 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       e39e10f7-94ba-4680-82af-04289fc3743a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e39e10f7-94ba-4680-82af-04289fc3743a | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.179/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             189.7.80.22
IP4.DNS[2]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       expiry = 1471534012
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.179
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 604780
DHCP4.OPTION[19]:                       dhcp_lease_time = 604800
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       domain_name_servers = 189.7.80.22 192.168.0.1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 604780
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::b70:f55e:43b5:431e/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Sunrise Point-LP PCI Express Root Port
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-34-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/wlp2s0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5fcabde7-b021-4064-a9ae-47493065a2ca | Padoka

SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Padoka                        <MAC 'Padoka' [AC1]>  Infra  7     2442 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
FlaeDeSC                      <MAC 'FlaeDeSC' [AC4]>  Infra  9     2452 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
guilherme                     <MAC 'guilherme' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
diva                          <MAC 'diva' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
A2HWERQERIORJIWERIPOQKLDEEP2  <MAC 'A2HWERQERIORJIWERIPOQKLDEEP2' [AC6]>  Infra  5     2432 MHz  11 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
dlink                         <MAC 'dlink' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
--                            <MAC '' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2       no        
netvirtua1161                 <MAC 'netvirtua1161' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
--                            <MAC '--' [AN9]>  Infra  9     2452 MHz  11 Mbit/s  25      &#9602;___  WEP        no        
mesa                          <MAC 'mesa' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
ConectaSaoCarlos              <MAC 'ConectaSaoCarlos' [AC9]>  Infra  7     2442 MHz  54 Mbit/s  22      &#9602;___  --         no        
AYRA                          <MAC 'AYRA' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  15      &#9602;___  WPA1 WPA2  no        
A15890P4                      <MAC 'A15890P4' [AN13]>  Infra  100   5500 MHz  54 Mbit/s  15      &#9602;___  WPA2       no        
Escritorioadvocacia           <MAC 'Escritorioadvocacia' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  14      &#9602;___  WPA2       no        
Zeraik                        <MAC 'Zeraik' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/FAST3184-EFD4]] (600 root)
[connection] id=FAST3184-EFD4 | type=wifi | permissions=user:desouza:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FAST3184-EFD4
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Padoka]] (600 root)
[connection] id=Padoka | type=wifi | permissions=user:desouza:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Padoka
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/maminha]] (600 root)
[connection] id=maminha | type=wifi | permissions=user:desouza:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=maminha
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DC-Pos]] (600 root)
[connection] id=DC-Pos | type=wifi | permissions=user:desouza:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=DC-Pos
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Sao_Paulo (based on set time zone)

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

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Padoka' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"Padoka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000273105692e
                    Extra: Last beacon: 4288ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'diva' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"diva"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dcdf6a0762
                    Extra: Last beacon: 3828ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'dlink' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000278ba27b14
                    Extra: Last beacon: 3976ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'FlaeDeSC' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"FlaeDeSC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000653982c8
                    Extra: Last beacon: 4188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d387b1580
                    Extra: Last beacon: 4332ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'A2HWERQERIORJIWERIPOQKLDEEP2' [AC6]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"A2HWERQERIORJIWERIPOQKLDEEP2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000014696c562186
                    Extra: Last beacon: 4440ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ConectaSaoCarlos' [AC7]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"ConectaSaoCarlos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002fd3c1ae
                    Extra: Last beacon: 4576ms ago
          Cell 08 - Address: <MAC 'mesa' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"mesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d387ab1de
                    Extra: Last beacon: 4344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ConectaSaoCarlos' [AC9]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"ConectaSaoCarlos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000300287662
                    Extra: Last beacon: 4328ms ago

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

[  148.440765] wlp2s0: authenticate with <MAC 'Padoka' [AC1]>
[  148.476751] wlp2s0: send auth to <MAC 'Padoka' [AC1]> (try 1/3)
[  148.478525] wlp2s0: authenticated
[  148.478874] ath10k_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  148.478885] ath10k_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  148.481418] wlp2s0: associate with <MAC 'Padoka' [AC1]> (try 1/3)
[  148.484760] wlp2s0: RX AssocResp from <MAC 'Padoka' [AC1]> (capab=0x431 status=0 aid=1)
[  148.486911] wlp2s0: associated
[  158.506681] wlp2s0: deauthenticating from <MAC 'Padoka' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  158.552024] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  163.672225] ath10k_warn: 57 callbacks suppressed
[  163.672264] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  168.689840] ath10k_warn: 48 callbacks suppressed
[  168.689883] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  173.810759] ath10k_warn: 66 callbacks suppressed
[  173.810801] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  178.828680] ath10k_warn: 47 callbacks suppressed
[  178.828723] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  183.556059] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  183.929890] ath10k_warn: 88 callbacks suppressed
[  183.929946] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 11 times)
[  762.586618] r8169 0000:01:00.0 enp1s0: link up
[  762.586652] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready

########## wireless info END ############
```

---

### Post by pedro.desouza on 2016-09-14
I'm out of ideas. Could anyone help me out? Ideas and starting steps is what I'm looking for :)

Thanks

---


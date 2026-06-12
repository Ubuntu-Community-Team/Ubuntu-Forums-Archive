---
title: "Kubuntu 17.04 HotSpot/wifi disconnects"
date: 2017-12-30
forum: Networking &amp; Wireless
---

### Post by lukas-buehrer on 2017-12-30
Hi, (Laptop is asus ux305ca with intel 7265 wlan chip)
my problem is that i get wifi disconnects from time to time when im using the hotspot of my android device with my laptop (think i also got them with my normal router, but i only use my android hot spot for a year now so not really sure how it is now). very rarely but consistently. also got them with ubuntu 16.04 and linux mint 18.3.
in kde the wifi symbol will get grey and a yellow questionmark appears on the wifi symbol. i just have to disconnect and connect again and everything works fine then for another 5-15 hours or so. the problem only is with linux, windows works fine in that regard.

hope my description is understandable. if i have to input some commands to get some specific information pls tell me, im just an average linux user :)

thanks.

---

### Post by Hadaka on 2017-12-30
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the **wireless-info.txt**
~OR~
This method.
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
Thanks.

---

### Post by lukas-buehrer on 2017-12-30
Hi, here is the output of the wireless info txt file

```


########## wireless info START ##########


Report from: 30 Dec 2017 21:34 CET +0100


Booted last: 30 Dec 2017 00:00 CET +0100


Script from: 05 Dec 2017 03:13 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful


##### kernel ############################


Linux 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5110]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 0bda:57cb Realtek Semiconductor Corp. 
Bus 001 Device 011: ID 062a:5918 Creative Labs 
Bus 001 Device 012: ID 24ae:2000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


iwlmvm                385024  0
mac80211              778240  1 iwlmvm
iwlwifi               249856  1 iwlmvm
cfg80211              610304  3 iwlmvm,iwlwifi,mac80211
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi                    24576  1 asus_wmi
video                  40960  3 asus_wmi,int3406_thermal,i915


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF1]> brd <MAC address>
    inet 192.168.43.28/24 brd 192.168.43.255 scope global dynamic wlp1s0
       valid_lft 2908sec preferred_lft 2908sec
    inet6 fe80::eebb:887c:2d8c:9968/64 scope link 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"WLAN-395445"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN-395445' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:243   Missed beacon:0


##### route #############################


default via 192.168.43.1 dev wlp1s0 proto static metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 
192.168.43.0/24 dev wlp1s0 proto kernel scope link src 192.168.43.28 metric 600 


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       736     1  0 Dec29 ?        00:01:10 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.13.0-21-generic
GENERAL.FIRMWARE-VERSION:               29.610311.0
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            1500
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
GENERAL.CONNECTION:                     WLAN-395445
GENERAL.CON-UUID:                       aa16779a-4b7b-4e9b-95b6-2c9c3b4a6805
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   aa16779a-4b7b-4e9b-95b6-2c9c3b4a6805 | WLAN-395445
IP4.ADDRESS[1]:                         192.168.43.28/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.28
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3026
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1676
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1514668982
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = LukasNotebook
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::eebb:887c:2d8c:9968/64
IP6.GATEWAY:                            --


SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
A1-D74BA9                     <MAC 'A1-D74BA9' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
HUAWEI-E5180-E6D9             <MAC 'HUAWEI-E5180-E6D9' [AC3]>  Infra  4     2427 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Wlan123                       <MAC 'Wlan123' [AC2]>  Infra  2     2417 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
WLAN-395445                   <MAC 'WLAN-395445' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Kali-420                      <MAC 'Kali-420' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
A1-de6999                     <MAC 'A1-de6999' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
tica                          <MAC 'tica' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  14      &#9602;___  WPA1       no        
HP-Print-45-LaserJet Pro MFP  <MAC 'HP-Print-45-LaserJet Pro MFP' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  10      &#9602;___  WEP        no        


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


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/eduroam-074fed69-4355-4f76-baf0-cb9809778f4f]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:uni:;
[wifi] mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:lukas:;
[wifi] mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WLAN-395445]] (600 root)
[connection] id=WLAN-395445 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=WLAN-395445
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WLAN-395444]] (600 root)
[connection] id=WLAN-395444 | type=wifi | permissions=user:lukas:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=WLAN-395444
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


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


phy#0 (self-managed)
country 00: DFS-UNSET
    (2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
    (2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
    (2447 - 2472 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    (2457 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-80MHZ, NO-160MHZ, PASSIVE-SCAN
    (5170 - 5190 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5190 - 5210 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5210 - 5230 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5230 - 5250 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5250 - 5270 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5270 - 5290 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5290 - 5310 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5310 - 5330 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5490 - 5510 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5510 - 5530 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5530 - 5550 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5550 - 5570 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5570 - 5590 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5590 - 5610 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5610 - 5630 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5630 - 5650 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5650 - 5670 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5670 - 5690 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5690 - 5710 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5710 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5735 - 5755 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5755 - 5775 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5775 - 5795 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5795 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ, PASSIVE-SCAN


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'WLAN-395445' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"WLAN-395445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000084e14a6a
                    Extra: Last beacon: 328ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Wlan123' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Wlan123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000a87680af4ff
                    Extra: Last beacon: 884ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HUAWEI-E5180-E6D9' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-E5180-E6D9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f149205d0
                    Extra: Last beacon: 756ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'A1-D74BA9' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"A1-D74BA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fbcb3d70d4
                    Extra: Last beacon: 608ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'A1-de6999' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"A1-de6999"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a8d2203c2f
                    Extra: Last beacon: 392ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Kali-420' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Kali-420"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f37b9131b1
                    Extra: Last beacon: 952ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'tica' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"tica"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c43890891f
                    Extra: Last beacon: 684ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HP-Print-45-LaserJet Pro MFP' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-45-LaserJet Pro MFP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a3b7fc142
                    Extra: Last beacon: 660ms ago


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.13.0-21-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     EBD7611E6805E2BDE8304CC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
name:           iwlmvm
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.13.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.13.0-21-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-8265-33.ucode
firmware:       iwlwifi-8000C-33.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0--33.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--33.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--33.ucode
firmware:       iwlwifi-Qu-a0-hr-a0--33.ucode
srcversion:     339D7D3BD0DD2A9C7FE616F
depends:        cfg80211
intree:         Y
name:           iwlwifi
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
filename:       /lib/modules/4.13.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
swcrypto: 0
uapsd_disable: 3


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[123960.260940] wlp1s0: disassociated from <MAC 'WLAN-395445' [AC1]> (Reason: 3=DEAUTH_LEAVING)
[123960.363043] wlp1s0: failed to remove key (1, <MAC address>) from hardware (-22)
[123963.951106] wlp1s0: authenticate with <MAC 'WLAN-395445' [AC1]>
[123963.957018] wlp1s0: send auth to <MAC 'WLAN-395445' [AC1]> (try 1/3)
[123964.010417] wlp1s0: send auth to <MAC 'WLAN-395445' [AC1]> (try 2/3)
[123964.065803] wlp1s0: send auth to <MAC 'WLAN-395445' [AC1]> (try 3/3)
[123964.128966] wlp1s0: authentication with <MAC 'WLAN-395445' [AC1]> timed out
[123975.688413] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[123976.616823] wlp1s0: authenticate with <MAC 'WLAN-395445' [AC1]>
[123976.622127] wlp1s0: send auth to <MAC 'WLAN-395445' [AC1]> (try 1/3)
[123976.627079] wlp1s0: authenticated
[123976.631127] wlp1s0: associate with <MAC 'WLAN-395445' [AC1]> (try 1/3)
[123976.638357] wlp1s0: RX AssocResp from <MAC 'WLAN-395445' [AC1]> (capab=0x431 status=0 aid=1)
[123976.639831] wlp1s0: associated
[123976.639900] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[123976.784630] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=44406 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[123976.899853] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=44411 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[123976.909154] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=51 TOS=0x00 PREC=0x00 TTL=255 ID=44412 PROTO=UDP SPT=5355 DPT=5355 LEN=31 
[123977.079755] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=44443 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[123977.079853] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=51 TOS=0x00 PREC=0x00 TTL=255 ID=44444 PROTO=UDP SPT=5355 DPT=5355 LEN=31 
[123977.267778] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=51 TOS=0x00 PREC=0x00 TTL=255 ID=44473 PROTO=UDP SPT=5355 DPT=5355 LEN=31 
[123978.033028] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=fe80:0000:0000:0000:eebb:887c:2d8c:9968 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=79 TC=0 HOPLIMIT=255 FLOWLBL=183299 PROTO=UDP SPT=5355 DPT=5355 LEN=39  (repeated 3 times)
[123981.067868] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=57 TOS=0x00 PREC=0x00 TTL=255 ID=45144 PROTO=UDP SPT=5355 DPT=5355 LEN=37 
[123981.068129] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=57 TOS=0x00 PREC=0x00 TTL=255 ID=45145 PROTO=UDP SPT=5355 DPT=5355 LEN=37 
[123981.068304] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=56 TOS=0x00 PREC=0x00 TTL=255 ID=45146 PROTO=UDP SPT=5355 DPT=5355 LEN=36 
[123981.330210] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28 DST=224.0.0.252 LEN=57 TOS=0x00 PREC=0x00 TTL=255 ID=45157 PROTO=UDP SPT=5355 DPT=5355 LEN=37 
[123981.992266] [UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=fe80:0000:0000:0000:eebb:887c:2d8c:9968 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=71 TC=0 HOPLIMIT=255 FLOWLBL=183299 PROTO=UDP SPT=5355 DPT=5355 LEN=31  (repeated 7 times)


########## wireless info END ############



```

---

### Post by praseodym on 2017-12-30
Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
and reboot

---

### Post by Hadaka on 2017-12-30
Hi, here are a few things that may be the cause of your drops..

Power Managemen is on...it should be off.
wlp1s0    IEEE 802.11  ESSID:"WLAN-395445"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN-395445' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management on
          Link Quality=55/70  Signal level=-55 dBm  
Please do..  
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Country Code is unset.
Region: Europe/Berlin (based on set time zone)
country 00: DFS-UNSET
Please copy and paste
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
Driver paramater is currently set to 0
[iwlwifi]
11n_disable: 0
Please do..
```
echo "options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
IPv6-set to auto.
[[/etc/NetworkManager/system-connections/WLAN-395445]] (600 root)
'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=WLAN-395445
[ipv4] method=auto
[ipv6] method=auto
*Please See attached to set to IGNORE..
[ATTACH=CONFIG]277973[/ATTACH]

UFW blocks..
[UFW BLOCK] IN=wlp1s0 OUT= MAC= SRC=192.168.43.28
please check your ufw settings..
May be nothing..while not recomended you can turn off logging with..
```
sudo ufw logging off
```

---

### Post by lukas-buehrer on 2017-12-30
so heres my new wifi txt, i think i did it all, possible did this [COLOR=#000000][FONT=&quot]echo "options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf a few times too often, because it just made a new line in the terminal, but i think it worked.


```
[/FONT][/COLOR]

########## wireless info START ##########


Report from: 31 Dec 2017 01:58 CET +0100


Booted last: 31 Dec 2017 00:00 CET +0100


Script from: 05 Dec 2017 03:13 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful


##### kernel ############################


Linux 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 11: ignoring bad line starting with 'echo'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 14: ignoring bad line starting with 'echo'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 16: ignoring bad line starting with 'echo'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 19: ignoring bad line starting with 'echo'


01:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5110]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 0bda:57cb Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 062a:5918 Creative Labs 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                385024  0
mac80211              778240  1 iwlmvm
iwlwifi               249856  1 iwlmvm
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
cfg80211              610304  3 iwlmvm,iwlwifi,mac80211
sparse_keymap          16384  1 asus_wmi
wmi                    24576  1 asus_wmi
video                  40960  3 asus_wmi,int3406_thermal,i915


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF1]> brd <MAC address>
    inet 192.168.43.28/24 brd 192.168.43.255 scope global dynamic wlp1s0
       valid_lft 2835sec preferred_lft 2835sec
    inet6 fe80::<IP6 'wlp1s0' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"WLAN-395445"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN-395445' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:82   Missed beacon:0


##### route #############################


default via 192.168.43.1 dev wlp1s0 proto static metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 
192.168.43.0/24 dev wlp1s0 proto kernel scope link src 192.168.43.28 metric 600 


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       772     1  0 01:45 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.13.0-21-generic
GENERAL.FIRMWARE-VERSION:               29.610311.0
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            1500
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
GENERAL.CONNECTION:                     WLAN-395445
GENERAL.CON-UUID:                       aa16779a-4b7b-4e9b-95b6-2c9c3b4a6805
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   aa16779a-4b7b-4e9b-95b6-2c9c3b4a6805 | WLAN-395445
IP4.ADDRESS[1]:                         192.168.43.28/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.28
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1514684738
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = LukasNotebook
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp1s0' [IF1]>/64
IP6.GATEWAY:                            --


SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
WLAN-395445                   <MAC 'WLAN-395445' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2       yes     * 
A1-D74BA9                     <MAC 'A1-D74BA9' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Kali-420                      <MAC 'Kali-420' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
HUAWEI-E5180-E6D9             <MAC 'HUAWEI-E5180-E6D9' [AC5]>  Infra  5     2432 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
Wlan123                       <MAC 'Wlan123' [AC4]>  Infra  2     2417 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
A1-de6999                     <MAC 'A1-de6999' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
TMOBILE-77196                 <MAC 'TMOBILE-77196' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        
HP-Print-45-LaserJet Pro MFP  <MAC 'HP-Print-45-LaserJet Pro MFP' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  9       &#9602;___  WEP        no        


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


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/eduroam-074fed69-4355-4f76-baf0-cb9809778f4f]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:uni:;
[wifi] mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:lukas:;
[wifi] mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WLAN-395445]] (600 root)
[connection] id=WLAN-395445 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=WLAN-395445
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/WLAN-395444]] (600 root)
[connection] id=WLAN-395444 | type=wifi | permissions=user:lukas:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=WLAN-395444
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


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


phy#0 (self-managed)
country 00: DFS-UNSET
	(2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
	(2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
	(2447 - 2472 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
	(2457 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-80MHZ, NO-160MHZ, PASSIVE-SCAN
	(5170 - 5190 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5190 - 5210 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5210 - 5230 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5230 - 5250 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5250 - 5270 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5270 - 5290 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5290 - 5310 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5310 - 5330 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5490 - 5510 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5510 - 5530 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5530 - 5550 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5550 - 5570 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5570 - 5590 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5590 - 5610 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5610 - 5630 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5630 - 5650 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5650 - 5670 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5670 - 5690 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5690 - 5710 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5710 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5735 - 5755 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5755 - 5775 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5775 - 5795 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
	(5795 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
	(5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ, PASSIVE-SCAN


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'WLAN-395445' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"WLAN-395445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000434084506
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Kali-420' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Kali-420"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f72ab486e2
                    Extra: Last beacon: 6356ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TMOBILE-77196' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"TMOBILE-77196"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000f23d8c11198
                    Extra: Last beacon: 6324ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Wlan123' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Wlan123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000a8b172fcee7
                    Extra: Last beacon: 6224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HUAWEI-E5180-E6D9' [AC5]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-E5180-E6D9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012c3b8659b
                    Extra: Last beacon: 6112ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'A1-D74BA9' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"A1-D74BA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ff7a608c87
                    Extra: Last beacon: 5932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'HP-Print-45-LaserJet Pro MFP' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-45-LaserJet Pro MFP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002deaa406fa
                    Extra: Last beacon: 6000ms ago
          Cell 08 - Address: <MAC 'A1-de6999' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"A1-de6999"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ac81472187
                    Extra: Last beacon: 5664ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.13.0-21-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     EBD7611E6805E2BDE8304CC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
name:           iwlmvm
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.13.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.13.0-21-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-8265-33.ucode
firmware:       iwlwifi-8000C-33.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0--33.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--33.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--33.ucode
firmware:       iwlwifi-Qu-a0-hr-a0--33.ucode
srcversion:     339D7D3BD0DD2A9C7FE616F
depends:        cfg80211
intree:         Y
name:           iwlwifi
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
filename:       /lib/modules/4.13.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-21-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
11n_disable: 8
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
swcrypto: 0
uapsd_disable: 3


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
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=8
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=8
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=8
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=8


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    5.750002] iwlwifi: unknown parameter '|' ignored
[    5.750004] iwlwifi: unknown parameter 'sudo' ignored
[    5.750005] iwlwifi: unknown parameter 'tee' ignored
[    5.750007] iwlwifi: unknown parameter '-a' ignored
[    5.750016] iwlwifi: unknown parameter '/etc/modprobe' ignored
[    5.750019] iwlwifi: unknown parameter '|' ignored
[    5.750020] iwlwifi: unknown parameter 'sudo' ignored
[    5.750021] iwlwifi: unknown parameter 'tee' ignored
[    5.750023] iwlwifi: unknown parameter '-a' ignored
[    5.750025] iwlwifi: unknown parameter '/etc/modprobe' ignored
[    5.750027] iwlwifi: unknown parameter '|' ignored
[    5.750028] iwlwifi: unknown parameter 'sudo' ignored
[    5.750029] iwlwifi: unknown parameter 'tee' ignored
[    5.750030] iwlwifi: unknown parameter '-a' ignored
[    5.750033] iwlwifi: unknown parameter '/etc/modprobe' ignored
[    5.849915] iwlwifi 0000:01:00.0: loaded firmware version 29.610311.0 op_mode iwlmvm
[    5.924054] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    5.954226] iwlwifi 0000:01:00.0: base HW address: <MAC 'wlp1s0' [IF1]>
[    6.029963] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.161070] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    6.833407] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[   11.691769] wlp1s0: authenticate with <MAC 'WLAN-395445' [AC1]>
[   11.699267] wlp1s0: send auth to <MAC 'WLAN-395445' [AC1]> (try 1/3)
[   11.804301] wlp1s0: send auth to <MAC 'WLAN-395445' [AC1]> (try 2/3)
[   11.819410] wlp1s0: authenticated
[   11.824277] wlp1s0: associate with <MAC 'WLAN-395445' [AC1]> (try 1/3)
[   11.859120] wlp1s0: RX AssocResp from <MAC 'WLAN-395445' [AC1]> (capab=0x431 status=0 aid=5)
[   11.862040] wlp1s0: associated
[   11.862178] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready


########## wireless info END ############


[COLOR=#000000][FONT=&quot]
```[/FONT][/COLOR][COLOR=#000000][/COLOR]

---

### Post by Hadaka on 2017-12-30
hi, please post the output of..
```
cat [COLOR=#000000][FONT=&quot]/etc/modprobe.d/iwlwifi.conf[/FONT][/COLOR]
```
Thanks

---

### Post by lukas-buehrer on 2017-12-31
hi, here is the output


```
[FONT=monospace][COLOR=#000000]# /etc/modprobe.d/iwlwifi.conf[/COLOR]
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf


echo options iwlwifi 11n_disable=8
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf

echo options iwlwifi 11n_disable=8
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=8
options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf

echo options iwlwifi 11n_disable=8

[/FONT]
```
i guess i went a bit too overboard with that :)

---

### Post by Hadaka on 2017-12-31
Hi,this command..
```
# echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Does the following..echo's.. options iwlwifi 11n_disable=8.. to the screen AND appends to the file..
/etc/modprobe.d/iwlwifi.conf...-a=append...  tee..just like a plumbing T allows both things to happen at once.
..echo to the screeen..append the file. Let's clean up that file before we continue. Please do..
```
sudo sed -i '/11n/ d' /etc/modprobe.d/iwlwifi.conf
```
This deletes any line that has..11n and doesnt start with a #
Then re enter so it only has ONE entry. Please do..
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Then do and Post the output of..
```
cat /etc/modprobe.d/iwlwifi.conf
```
Thanks

---

### Post by lukas-buehrer on 2017-12-31
output:
```
[FONT=monospace][COLOR=#000000] /etc/modprobe.d/iwlwifi.conf[/COLOR]
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211




options iwlwifi 11n_disable=8

[/FONT]
```

i think it looks good now,

thank you very much :)

---

### Post by Hadaka on 2017-12-31
Great !..ok it looks like the only thing that didnt take was setting
the country code...#Europe/Berlin, Let's try again a little differently
Please do..
```
sudo iw reg set DE
sudo sed -i 's/REGDOMAIN=.*/REGDOMAIN=DE/' /etc/default/crda
```
Then please do and post..
```
iw reg get
cat /etc/default/crda
```
Thanks.

---


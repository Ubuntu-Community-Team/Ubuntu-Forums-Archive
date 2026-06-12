---
title: "following a wireless network troubleshooter and i fall over at the first step"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by jon106 on 2015-12-12
Using ver15.10 in terminal type nm-tool and i get message no command.

what am i doing wrong? please help me

thanks

---

### Post by steeldriver on 2015-12-12
Hello and welcome to the forums

It looks like nm-tool has been dropped from the network-manager package. You should be able to do everything it used to do using nmcli although it may take some getting used to.

What are you trying to troubleshoot and what guide are you following? if it's online, please share the link

---

### Post by jon106 on 2015-12-12
this one [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-initial-check.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-initial-check.html)

---

### Post by Bucky Ball on 2015-12-12
Welcome. If you're having issues, open a terminal and, for a start, issue this command (if you have a USB wireless dongle, plug it in first):

```
sudo lshw -C network
```

Post the output back here between code tags, please (see the last link in my signature).

If it is USB, please also give the output, again with it plugged in, of this:

```
lsusb
```

> **steeldriver said:**
> What are you trying to troubleshoot ... ?

+1. Let us know what the problem is, what you've tried, and where you are now. Have a read of the [*Networking and Wireless* sticky]("http://ubuntuforums.org/showthread.php?t=370108"). :)

---

### Post by jon106 on 2015-12-12
I can't get on to the network via the wifi FYI i can boot in to windows and go straight onto the network/internet via the wifi etc
[COLOR=#000000]```
[/COLOR]*-network              
       description:Wireless interface
       product:PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: IntelCorporation
       physical id: 0
       bus info:pci@0000:06:00.0
       logical name:wlp6s0
       version: 61
       serial:00:1d:e0:0b:d4:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list ethernet physical wireless
       configuration:broadcast=yes driver=iwl4965 driverversion=4.2.0-19-genericfirmware=228.61.2.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources:irq:32 memory:fa000000-fa001fff
  *-network
       description:Ethernet interface
       product: 88E8036 PCI-E Fast EthernetController
       vendor: MarvellTechnology Group Ltd.
       physical id: 0
       bus info:pci@0000:08:00.0
       logical name:enp8s0
       version: 16
       serial:00:1a:80:24:ba:6a
       size: 100Mbit/s
       capacity:100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pmvpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt100bt-fd autonegotiation
       configuration:autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=fulllatency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s

       resources:irq:29 memory:fc000000-fc003fff ioport:6000(size=256)[COLOR=#000000]
```[/COLOR]

---

### Post by Bucky Ball on 2015-12-13
Click on the network icon and 'Edit', and edit the wireless entry, if there is one. Change the IPv6 setting on the IPv6 tab to 'ignore' for now.  and reboot, please. In 'Wifi Security' tab, make sure you have the correct security setup and security key for your router/access point. 

Save changes, pull out ethernet cable and reboot. Click the network icon when you are back at the desktop. Do you see any available networks or are you offered any? If not, please run the wirelessinfoscript in my signature and we'll get more details. Thanks.

Your wireless looks to be set up fine with the correct driver in your previous output so don't think that's the issue. We'll keep digging.

---

### Post by jon106 on 2015-12-13
not ran the wireless info script yet but a quick update (have done the ignore and reboot) on reboot 

It states "wifi networks available" "use the network menu to connect........"  when I go to "system settings" > "wireless" > it shows last used never strength excellent and has a connect button when I click this nothing happens, also I used to have a network status symbol on the top tool bar this has been missing ever since the start of my issues.

---

### Post by Bucky Ball on 2015-12-13
You don't go to System Settings when you get 'wireless networks available'. Just click the wireless icon and you should see a list of available networks when you click it. Connect to yours (you will need the security key). 

Don't tweak your wireless setup by editing. Everything's working fine.

---

### Post by jon106 on 2015-12-13
```
########## wireless info START ##########
 
Report from: 13 Dec 2015 11:48 GMT +0000
 
Booted last: 13 Dec 2015 00:00 GMT +0000
 
Script from: 27 Sep 2015 00:34 UTC +0000
 
##### release ###########################
 
Distributor ID:            Ubuntu
Description:     Ubuntu15.10
Release:           15.10
Codename:      wily
 
##### kernel ############################
 
Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC2015 x86_64 x86_64 x86_64 GNU/Linux
 
Parameters: ro, quiet, splash, vt.handoff=7
 
##### desktop ###########################
 
Ubuntu
 
##### lspci #############################
 
06:00.0 Network controller [0280]: Intel CorporationPRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
            Subsystem:Intel Corporation PRO/Wireless 4965 AG or AGN [8086:1101]
            Kerneldriver in use: iwl4965
 
08:00.0 Ethernet controller [0200]: Marvell Technology GroupLtd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16)
            Subsystem:Sony Corporation Device [104d:9005]
            Kerneldriver in use: sky2
 
##### lsusb #############################
 
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. KingstonDataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 007 Device 005: ID 044e:3012 Alps Electric Co., Ltd
Bus 007 Device 004: ID 044e:3013 Alps Electric Co., Ltd
Bus 007 Device 003: ID 044e:3010 Alps Electric Co., LtdBluetooth Adapter
Bus 007 Device 002: ID 044e:3011 Alps Electric Co., Ltd
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd VisualCommunication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
 
##### PCMCIA card info ##################
 
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
 
##### rfkill ############################
 
0: hci0: Bluetooth
            Softblocked: no
            Hardblocked: no
1: phy0: Wireless LAN
            Softblocked: no
            Hardblocked: no
 
##### lsmod #############################
 
iwl4965              114688  0
iwlegacy             102400  1 iwl4965
mac80211             733184  2 iwl4965,iwlegacy
cfg80211             548864  3iwl4965,iwlegacy,mac80211
mxm_wmi                16384 1 nouveau
wmi                   20480  2 mxm_wmi,nouveau
 
##### interfaces ########################
 
auto lo
iface lo inet loopback
 
##### ifconfig ##########################
 
enp8s0    Linkencap:Ethernet  HWaddr <MAC 'enp8s0'[IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr:fe80::<IP6 'enp8s0' [IF]>/64 Scope:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RXbytes:35556 (35.5 KB)  TX bytes:13366(13.3 KB)
          Interrupt:16
 
wlp6s0    Linkencap:Ethernet  HWaddr <MAC 'wlp6s0'[IF]>  
          UP BROADCASTMULTICAST  MTU:1500  Metric:1
          RX packets:0errors:0 dropped:0 overruns:0 frame:0
          TX packets:33errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RX bytes:0(0.0 B)  TX bytes:7254 (7.2 KB)
 
##### iwconfig ##########################
 
lo        no wirelessextensions.
 
enp8s0    no wirelessextensions.
 
wlp6s0    IEEE802.11abgn  ESSID:off/any  
         Mode:Managed  Access Point:Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off  Fragment thr:off
          PowerManagement:off
          
 
##### route #############################
 
Kernel IP routing table
Destination    Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0        192.168.1.1     0.0.0.0         UG   100    0        0 enp8s0
169.254.0.0    0.0.0.0         255.255.0.0     U    1000   0        0 enp8s0
192.168.1.0    0.0.0.0         255.255.255.0   U    100    0        0 enp8s0
 
##### resolv.conf #######################
 
nameserver 127.0.1.1
 
##### network managers ##################
 
Installed:
 
            NetworkManager
 
Running:
 
root       585     1  011:37 ?        00:00:00/usr/sbin/NetworkManager --no-daemon
 
##### NetworkManager info ###############
 
GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell TechnologyGroup Ltd.
GENERAL.PRODUCT:                       88E8036 PCI-E FastEthernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp8s0'[IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                           /sys/devices/pci0000:00/0000:00:1c.4/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                      7e834f4b-a4ac-4b40-a9d4-e78327528e47
GENERAL.CON-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS:/org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7e834f4b-a4ac-4b40-a9d4-e78327528e47 | Wiredconnection 1
IP4.ADDRESS[1]:                         192.168.1.4/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst =169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers =1
DHCP4.OPTION[2]:                        requested_domain_search= 1
DHCP4.OPTION[3]:                        requested_time_offset =1
DHCP4.OPTION[4]:                        requested_domain_name =1
DHCP4.OPTION[5]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                       requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1450093687
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address =192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu= 1
DHCP4.OPTION[12]:                       requested_subnet_mask =1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.4
DHCP4.OPTION[16]:                       subnet_mask =255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope= 1
DHCP4.OPTION[18]:                       requested_static_routes= 1
DHCP4.OPTION[19]:                       domain_name_servers =192.168.1.1
DHCP4.OPTION[20]:                      requested_domain_name_servers = 1
DHCP4.OPTION[21]:                      requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                      requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number =192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier =192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp8s0'[IF]>/64
IP6.GATEWAY:                            
 
GENERAL.DEVICE:                         wlp6s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 4965 AG orAGN [Kedron] Network Connection (PRO/Wireless 4965 AG or AGN)
GENERAL.DRIVER:                         iwl4965
GENERAL.DRIVER-VERSION:                 4.2.0-19-generic
GENERAL.FIRMWARE-VERSION:               228.61.2.24
GENERAL.HWADDR:                        <MAC 'wlp6s0'[IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant isnow available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlp6s0
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS:/org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ab3bb3d5-da5f-4726-a4dd-04c1666d9558 | Wi-Ficonnection
 
SSID  BSSID  MODE CHAN  FREQ  RATE SIGNAL  BARS  SECURITY ACTIVE  *
 
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
 
[[/etc/NetworkManager/system-connections/Wi-Fi connection]](600 root)
[connection] id=Wi-Fi connection | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=TALKTALK-CFBC20
[ipv4] method=auto
[ipv6] method=ignore
 
##### iw reg get ########################
 
Region: Europe/London (based on set time zone)
 
country 00: DFS-UNSET
            (2402 - 2472@ 40), (N/A, 20), (N/A)
            (2457 - 2482@ 40), (N/A, 20), (N/A), NO-IR
            (2474 - 2494@ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
            (5170 - 5250@ 80), (N/A, 20), (N/A), NO-IR
            (5250 - 5330@ 80), (N/A, 20), (0 ms), DFS, NO-IR
            (5490 - 5730@ 160), (N/A, 20), (0 ms), DFS, NO-IR
            (5735 - 5835@ 80), (N/A, 20), (N/A), NO-IR
            (57240 -63720 @ 2160), (N/A, 0), (N/A)
 
##### iwlist channels ###################
 
lo        no frequency information.
 
enp8s0    no frequencyinformation.
 
wlp6s0    32 channelsin total; available frequencies :
          Channel 01 :2.412 GHz
          Channel 02 :2.417 GHz
          Channel 03 :2.422 GHz
          Channel 04 :2.427 GHz
          Channel 05 :2.432 GHz
          Channel 06 :2.437 GHz
          Channel 07 :2.442 GHz
          Channel 08 :2.447 GHz
          Channel 09 :2.452 GHz
          Channel 10 :2.457 GHz
          Channel 11 :2.462 GHz
          Channel 12 : 2.467GHz
          Channel 13 :2.472 GHz
          Channel 36 :5.18 GHz
          Channel 40 :5.2 GHz
          Channel 44 :5.22 GHz
          Channel 48 :5.24 GHz
          Channel 52 :5.26 GHz
          Channel 56 :5.28 GHz
          Channel 60 :5.3 GHz
          Channel 64 :5.32 GHz
          Channel 100 :5.5 GHz
          Channel 104 :5.52 GHz
          Channel 108 :5.54 GHz
          Channel 112 :5.56 GHz
          Channel 116 :5.58 GHz
          Channel 120 :5.6 GHz
          Channel 124 :5.62 GHz
          Channel 128 :5.64 GHz
          Channel 132 :5.66 GHz
          Channel 136 :5.68 GHz
          Channel 140 :5.7 GHz
 
##### iwlist scan #######################
 
lo        Interfacedoesn't support scanning.
 
enp8s0    Interface doesn'tsupport scanning.
 
Channel occupancy:
 
      1   APs on  Frequency:2.412 GHz (Channel 1)
      3   APs on  Frequency:2.437 GHz (Channel 6)
      1   APs on  Frequency:2.442 GHz (Channel 7)
      2   APs on  Frequency:2.452 GHz (Channel 9)
      1   APs on  Frequency:5.18 GHz (Channel 36)
 
wlp6s0    Scancompleted :
          Cell 01 -Address: <MAC 'VM816287-2G' [AC1]>
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=47/70  Signal level=-63dBm  
                   Encryption key:on
                   ESSID:"VM816287-2G"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                             9 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=0000019da65f83d8
                   Extra: Last beacon: 20ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) :PSK
          Cell 02 -Address: <MAC 'VM816287-2G' [AC2]>
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=44/70  Signal level=-66dBm  
                   Encryption key:on
                   ESSID:"VM816287-2G"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                             9 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=0000019d2293e83c
                   Extra: Last beacon: 20ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 -Address: <MAC 'TALKTALK-CFBC20' [AC3]>
                   Channel:9
                   Frequency:2.452 GHz (Channel 9)
                   Quality=70/70  Signal level=-40dBm  
                    Encryptionkey:on
                   ESSID:"TALKTALK-CFBC20"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                             18 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                   Extra:tsf=000000018456bf32
                   Extra: Last beacon: 20ms ago
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
          Cell 04 -Address: <MAC 'VM816287-5G' [AC4]>
                   Channel:36
                   Frequency:5.18 GHz (Channel 36)
                   Quality=31/70  Signal level=-79dBm  
                   Encryption key:on
                   ESSID:"VM816287-5G"
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                             36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=0000019d2308f737
                    Extra: Last beacon: 20ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
          Cell 05 -Address: <MAC 'SKY189FD' [AC5]>
                   Channel:1
                   Frequency:2.412 GHz (Channel 1)
                   Quality=28/70  Signal level=-82dBm  
                   Encryption key:on
                   ESSID:"SKY189FD"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=0000085dfb1a0c8f
                    Extra: Last beacon: 20ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
          Cell 06 - Address:<MAC 'DIRECT-Fd-BRAVIA' [AC6]>
                   Channel:9
                   Frequency:2.452 GHz (Channel 9)
                   Quality=46/70  Signal level=-64dBm  
                   Encryption key:on
                   ESSID:"DIRECT-Fd-BRAVIA"
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                             36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=00000002f1340761
                   Extra: Last beacon: 20ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
          Cell 07 -Address: <MAC 'VM365453-2G' [AC7]>
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=28/70  Signal level=-82dBm  
                   Encryption key:on
                   ESSID:"VM365453-2G"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                             9 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=000000f52e2e3180
                    Extra: Last beacon: 2172ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
          Cell 08 -Address: <MAC 'virginmedia6843786' [AC8]>
                    Channel:7
                   Frequency:2.442 GHz (Channel 7)
                   Quality=24/70  Signal level=-86dBm  
                   Encryption key:on
                   ESSID:"virginmedia6843786"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=0000002576b891aa
                    Extra:Last beacon: 20ms ago
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
 
##### module infos ######################
 
[iwl4965]
filename:      /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:      iwlwifi-4965-2.ucode
license:        GPL
author:        Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:       in-tree:
description:   Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:    F710AC566CC7F26364D2D3E
depends:       iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:      4.2.0-19-generic SMP mod_unload modversions
signer:         Buildtime autogenerated kernel key
sig_key:       36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:          swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:          queues_num:number of hw queues. (int)
parm:           11n_disable:disable11n functionality (int)
parm:          amsdu_size_8K:enable 8K amsdu size (default 0 [disabled]) (int)
parm:          fw_restart:restart firmware in case of error (int)
 
[iwlegacy]
filename:      /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:        Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:       in-tree:
description:   iwl-legacy: common functions for 3945 and 4965
srcversion:    B4C063DEBD9D98330C307A9
depends:       mac80211,cfg80211
intree:         Y
vermagic:      4.2.0-19-generic SMP mod_unload modversions
signer:         Buildtime autogenerated kernel key
sig_key:       36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:          led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:          bt_coex_active:enable wifi/bluetooth co-exist (bool)
 
[mac80211]
filename:      /lib/modules/4.2.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE802.11 subsystem
srcversion:    065F4A11FE84275F51A59F2
depends:       cfg80211
intree:         Y
vermagic:      4.2.0-19-generic SMP mod_unload modversions
signer:         Buildtime autogenerated kernel key
sig_key:       36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:          minstrel_vht_only:Use only VHT rates when VHT is supported by sta.(bool)
parm:          max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting(reason 4). (int)
parm:          max_probe_tries:Maximum probe tries before disconnecting (reason 4).(int)
parm:          beacon_loss_count:Number of beacon intervals before we decide beacon waslost. (int)
parm:           probe_wait_ms:Maximumtime(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:          ieee80211_default_rc_algo:Default rate control algorithm for mac80211 touse (charp)
 
[cfg80211]
filename:      /lib/modules/4.2.0-19-generic/kernel/net/wireless/cfg80211.ko
description:   wireless configuration support
license:        GPL
author:        Johannes Berg
srcversion:    1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:      4.2.0-19-generic SMP mod_unload modversions
signer:         Buildtime autogenerated kernel key
sig_key:       36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:          ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable40MHz support in the 2.4GHz band (bool)
 
##### module parameters #################
 
[iwl4965]
11n_disable: 0
amsdu_size_8K: 0
fw_restart: 1
queues_num: 0
swcrypto: 0
 
[iwlegacy]
bt_coex_active: Y
led_mode: 0
 
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
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi |xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
 
[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en
 
##### rc.local ##########################
 
exit 0
 
##### pm-utils ##########################
 
##### udev rules ########################
 
grep: /etc/udev/rules.d/*net*.rules: No such file ordirectory
 
##### dmesg #############################
 
[   11.607773]ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   11.609619] iwl49650000:06:00.0 wlp6s0: renamed from wlan0
[   25.221761] IPv6:ADDRCONF(NETDEV_UP): wlp6s0: link is not ready (repeated 2 times)
[   25.465275] IPv6:ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   25.467701] sky20000:08:00.0 enp8s0: enabling interface
[   25.467783] IPv6:ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   26.109050] IPv6:ADDRCONF(NETDEV_UP): wlp6s0: link is not ready (repeated 2 times)
[  163.315037] wlp6s0:Trigger new scan to find an IBSS to join (repeated 3 times)
[  168.343041] wlp6s0:Creating new IBSS network, BSSID <MAC address>
[  168.377472] iwl49650000:06:00.0: Unable to find TIM Element in beacon (repeated 2 times)
[  168.388860] IPv6:ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[  197.628570] wlp6s0:No active IBSS STAs - trying to scan for other IBSS networks with same SSID(merge)
[  214.311852] IPv6:ADDRCONF(NETDEV_UP): wlp6s0: link is not ready (repeated 9 times)
[  631.209344] sky20000:08:00.0 enp8s0: Link is up at 100 Mbps, full duplex, flow control both
[  631.209861] IPv6:ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready
 

########## wireless info END ############
```

---

### Post by jon106 on 2015-12-13
I don't have a wireless icon

---

### Post by Bucky Ball on 2015-12-13
Network icon. Not wireless icon. It should look like a couple of little televisions. I'm not using Ubuntu's Unity desktop so not sure where it would be. Exactly the same icon that tells you when you have ethernet connected. It probably just looks different with ethernet unconnected.

When you clicked the network icon and followed the instructions I gave to edit the wireless connection. Click that icon again and you should see a list of available networks. If it really has vanished, try running:

> sudo apt-get install network-manager-gnome

You may need to reboot or logout for it to appear. 

Your wireless appears to be working fine.

> It states "wifi networks available" "use the network menu to connect........"

---


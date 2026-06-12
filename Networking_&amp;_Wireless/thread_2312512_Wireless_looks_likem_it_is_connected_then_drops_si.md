---
title: "Wireless looks likem it is connected then drops signal"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by reb682 on 2016-02-04
I have Ububtu 15.10 on a HP presario A900 Laptop. I can click on the wifi connection and the antenna icon starts pulsating as if it is connected. It will do that for a short while then quit. If I try to go online to a browser it all so quits. I have upgraded this laptop from Windows to linux and am up date on the kernel.Could I be needing a newer driver? Thanks for any help


The wireless card I now have is 01:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by Hadaka on 2016-02-05
Hi, from a working wired connection open a terminal
ctrl/alt/t then copy and paste one line at a time..
```
sudo apt-get update
echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
remove wired connection,boot and test wireless
thanks.

---

### Post by reb68-l on 2016-02-06
After reading and studying the problem of not getting the wireless to work I now think it is because of the following: I had Vista on this laptop. I changed to Ubuntu. I tried to pull up BIOS to see if wireless was on but do not get bios. Some reading leads me to need to change drivers from the Vista. to the linux drivers. If you agree please tell me haw. I read about a wrapper and I am confused.  I have a HP presario 900 with Ubuntu 15.10 runiung. Any help or suggestions are appreciated. Thank you.

---

### Post by Hadaka on 2016-02-06
Hi, the windows wifi drivers are part of the windows operating system
and generally do not have any effect on the Ununtu linux wireless drivers.
Does your wired connection function correctly? if yes then open a terminal
ctrl/alt/t then copy and past..
```
lspci -nnk | grep -iA2 net
rfkill list all
```
post the output of those 2 commands.
thanks.

---

### Post by reb682 on 2016-02-06
richard@richard-Compaq-Presario-A900-Notebook-PC:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
    Kernel driver in use: 8139too
richard@richard-Compaq-Presario-A900-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
richard@richard-Compaq-Presario-A900-Notebook-PC:~$

---

### Post by Hadaka on 2016-02-06
Hi, did you do the commands given you in this post?
[http://ubuntuforums.org/showthread.php?t=2312512](http://ubuntuforums.org/showthread.php?t=2312512)
if not, from a working wired connection copy and paste
one line at a time..
```
sudo apt-get update
echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k

```
please do not post multiple threads for the same problem.
thanks.

---

### Post by howefield on 2016-02-06
Threads merged.

---

### Post by reb682 on 2016-02-06
I apologize for the double entries. I thought that having the vista was a separate problem.  I rebooted and opened without the cable connection I can click on the Wifi and it will pulsate for 30 seconds and then turn off and meanwhile the browser or mailer will say cannot connect.

I went in the Bios and the one for Kubuntu on my Desktop look like a bios but the one on the laptop (Ubuntu) looks entirely different. I did not change anything. 

Thank you

---

### Post by Hadaka on 2016-02-06
OK, I still am curious if you ran those commands and did they
make a diffference?? Please connect your ubuntu computer to
a wired working internet connection. then go here..
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
run the wireless script then post the **wireless-info.txt** file it creates
in your home directory.
thanks.

---

### Post by reb682 on 2016-02-06
The wireless info txt is in my home directory. Can you retrieve it from there? as added info my wifi thread  name is "ATT6801" this is a new one that ATT set up in trying to help me a while back. The previous one I had was "Edna 1". Also my HP printer has a Wifi connection named "HP-Print-0C-Officejet 4630" 

I hope this helps.
Thank You.

---

### Post by Hadaka on 2016-02-06
OK, again,I am curious and am still awaiting an answer as to the commands that i asked you to run.
yes/no?? as far as the wireless-info.txt in your home directory, please post it here. Open a terminal
ctrl/alt/t then from your home directory do..
```
cat wireless-info.txt
```
copy and paste the output here..
thanks.

---

### Post by reb682 on 2016-02-06
My Wifi name is ATT6801, My Printer Wifi is HP-Print-0C-Officejet 4630

```
richard@richard-Compaq-Presario-A900-Notebook-PC:~$ cat wireless-info.txt

########## wireless info START ##########

Report from: 06 Feb 2016 15:49 EST -0500

Booted last: 06 Feb 2016 00:00 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:48:15 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 001 Device 004: ID 04f2:b057 Chicony Electronics Co., Ltd integrated USB webcam
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03f Logitech, Inc. M-BT85 [UltraX Optical Mouse]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 139264  0
ath                    24576  1 ath5k
mac80211              659456  1 ath5k
cfg80211              483328  3 ath,ath5k,mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s1    Link encap:Ethernet  HWaddr <MAC 'enp2s1' [IF]>  
          inet addr:192.168.1.236  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6662988 (6.6 MB)  TX bytes:773809 (773.8 KB)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:21255 (21.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s1    no wireless extensions.

wlp1s0    IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thrff   Fragment thrff
          Power Managementff
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp2s1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       585     1  0 14:57 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (Presario C700)
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/enp2s1
GENERAL.IP-IFACE:                       enp2s1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       d95adfed-7a62-4c5c-9ce0-b0060749e371
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d95adfed-7a62-4c5c-9ce0-b0060749e371 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.236/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.1.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_host_name = 1
DHCP4.OPTION[8]:                        host_name = richard-Compaq-Presario-A900-Notebook-PC
DHCP4.OPTION[9]:                        expiry = 1454875263
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       next_server = 192.168.1.254
DHCP4.OPTION[13]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.254
DHCP4.OPTION[17]:                       ip_address = 192.168.1.236
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[21]:                       dhcp_lease_time = 86400
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[23]:                       requested_domain_name_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express) (AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.2.0-27-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,2,0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d76962fc-a2be-493b-ad7b-6cc4ddf8c606 | ATT6801
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   153f3cf7-1980-43e9-9dc6-4277563e8d47 | HOME-1F0C
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   32432389-b424-4472-ac1c-8262af32fe99 | dixie
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   0a0f13d1-e595-4fd4-b7fc-509e5a94c71d | Edna1

SSID                        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
HP-Print-0C-Officejet 4630  <MAC 'HP-Print-0C-Officejet 4630' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
HOME-1F0C                   <MAC 'HOME-1F0C' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
HOME-FAE2                   <MAC 'HOME-FAE2' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
xfinitywifi                 <MAC 'xfinitywifi' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  --         no        
ATT6801                     <MAC 'ATT6801' [AC2]>  Infra  9     2452 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WEP        no        
xfinitywifi                 <MAC 'xfinitywifi' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  --         no        
--                          <MAC '' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
dixie                       <MAC 'dixie' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/ATT6801]] (600 root)
[connection] id=ATT6801 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=ATT6801
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dixie]] (600 root)
[connection] id=dixie | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=dixie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Edna1]] (600 root)
[connection] id=Edna1 | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Edna1
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-1F0C]] (600 root)
[connection] id=HOME-1F0C | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=HOME-1F0C
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

enp2s1    no frequency information.

wlp1s0    11 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s1    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'HP-Print-0C-Officejet 4630' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption keyn
                    ESSID:"HP-Print-0C-Officejet 4630"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000167a53e66ef
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT6801' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption keyn
                    ESSID:"ATT6801"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000173fd30c66
                    Extra: Last beacon: 72ms ago
          Cell 03 - Address: <MAC 'HOME-1F0C' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption keyn
                    ESSID:"HOME-1F0C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c29a2b586
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption keyff
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c29a2d0e9
                    Extra: Last beacon: 72ms ago
          Cell 05 - Address: <MAC 'HOME-FAE2' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption keyn
                    ESSID:"HOME-FAE2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000089705df9ad4
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption keyn
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014c29a2fa52
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'xfinitywifi' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption keyff
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000089705dfb9a9
                    Extra: Last beacon: 72ms ago
          Cell 08 - Address: <MAC 'dixie' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption keyn
                    ESSID:"dixie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000063a65a6d0ce
                    Extra: Last beacon: 408ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Cowart PC' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption keyn
                    ESSID:"Cowart PC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005dc8c28ab
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     771FA960E4882771F544E8B
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        F7:19:76:C3:42:AD:96:98:48:67:9D:F6:B3:80:57:34:9C:23:91:CB
sig_hashalgo:   sha512
parm:           nohwcryptisable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        F7:19:76:C3:42:AD:96:98:48:67:9D:F6:B3:80:57:34:9C:23:91:CB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FBF6EA073A00B4F3836226E
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        F7:19:76:C3:42:AD:96:98:48:67:9D:F6:B3:80:57:34:9C:23:91:CB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        F7:19:76:C3:42:AD:96:98:48:67:9D:F6:B3:80:57:34:9C:23:91:CB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N

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

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=1

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

[   13.487061] ath: EEPROM indicates we should expect a direct regpair map
[   13.487064] ath: Country alpha2 being used: 00
[   13.487066] ath: Regpair used: 0x64
[   13.538284] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   13.541453] ath5k 0000:01:00.0 wlp1s0: renamed from wlan0
[   22.404451] IPv6: ADDRCONF(NETDEV_UP): enp2s1: link is not ready
[   22.404627] 8139too 0000:02:01.0 enp2s1: link down
[   22.404715] IPv6: ADDRCONF(NETDEV_UP): enp2s1: link is not ready
[   22.407907] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[   65.024674] wlp1s0: authenticate with <MAC 'ATT6801' [AC2]>
[   65.034104] wlp1s0: send auth to <MAC 'ATT6801' [AC2]> (try 1/3)
[   65.035525] wlp1s0: authenticated
[   65.035774] ath5k 0000:01:00.0 wlp1s0: disabling HT/VHT due to WEP/TKIP use
[   65.036486] wlp1s0: associate with <MAC 'ATT6801' [AC2]> (try 1/3)
[   65.038574] wlp1s0: RX AssocResp from <MAC 'ATT6801' [AC2]> (capab=0x431 status=0 aid=2)
[   65.038690] wlp1s0: associated
[   65.038731] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  110.032901] wlp1s0: deauthenticating from <MAC 'ATT6801' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  131.817529] wlp1s0: authenticate with <MAC 'ATT6801' [AC2]>
[  131.828934] wlp1s0: send auth to <MAC 'ATT6801' [AC2]> (try 1/3)
[  131.830582] wlp1s0: authenticated
[  131.831681] ath5k 0000:01:00.0 wlp1s0: disabling HT/VHT due to WEP/TKIP use
[  131.832223] wlp1s0: associate with <MAC 'ATT6801' [AC2]> (try 1/3)
[  131.834322] wlp1s0: RX AssocResp from <MAC 'ATT6801' [AC2]> (capab=0x431 status=0 aid=2)
[  131.834442] wlp1s0: associated
[  177.034707] wlp1s0: deauthenticating from <MAC 'ATT6801' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  186.573348] wlp1s0: authenticate with <MAC 'ATT6801' [AC2]>
[  186.582590] wlp1s0: send auth to <MAC 'ATT6801' [AC2]> (try 1/3)
[  186.584372] wlp1s0: authenticated
[  186.585316] ath5k 0000:01:00.0 wlp1s0: disabling HT/VHT due to WEP/TKIP use
[  186.588293] wlp1s0: associate with <MAC 'ATT6801' [AC2]> (try 1/3)
[  186.590468] wlp1s0: RX AssocResp from <MAC 'ATT6801' [AC2]> (capab=0x431 status=0 aid=2)
[  186.590591] wlp1s0: associated
[  232.043032] wlp1s0: deauthenticating from <MAC 'ATT6801' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  245.085753] 8139too 0000:02:01.0 enp2s1: link up, 100Mbps, full-duplex, lpa 0x45E1
[  245.085793] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s1: link becomes ready
[  245.351284] 8139too 0000:02:01.0 enp2s1: link down
[  247.004624] 8139too 0000:02:01.0 enp2s1: link up, 100Mbps, full-duplex, lpa 0x45E1

########## wireless info END ############

richard@richard-Compaq-Presario-A900-Notebook-PC:~$ 
```
rinter is

---

### Post by Hadaka on 2016-02-06
Hi please open a terminal ctrl/alt/t and then copy and paste..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Then your wireless report showed this..
```
#ath5k 0000:01:00.0 wlp1s0: disabling HT/VHT due to WEP/TKIP use
#wlp1s0: associate with <MAC 'ATT6801' 
```
Its saying it doesnt like the TKIP and WEP setting you have in your router
for your ATT6801 connection.
so you need to change the configuration in your router to WAP2 AES  no TKIP.
also, untill you get your wifi straightened out i would suggest you turn off your
wireless printer
thanks.

---

### Post by reb682 on 2016-02-06
I changed it to "WPA2-PSK (AES) and it is working now. I had to ket the Network Key off the back of the modem.I also had the choice of Mixed "WPA/WPA2" but I stayed with what works unless you tell me there is an advantage going to the Mixed.

Thank you very much. You know I have been trying to find a solution to this for quite some time. Thank you again and all the others at this forum that tried to help me.
This old man will go right to sleep tonight and not lay trying to figure this out.

Do you mark it solved or is there a place I have to do it?

---

### Post by Hadaka on 2016-02-06
Fantastic ! to mark your thread solved sign in go to your first post,
look for and click **TOOLS **and then click [B]SOLVED
thanks!
[/B]

---


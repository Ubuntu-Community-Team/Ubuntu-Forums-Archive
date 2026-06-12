---
title: "HELP!!!! Toshiba L745-S4210 issue with RTL8188CE v.16.**"
date: 2016-12-08
forum: Networking &amp; Wireless
---

### Post by jcrodz on 2016-12-08
Hello All,

I have seen this issue with Realtek wifi and I have tried the solutions found to no success. I have tried installing the modified driver from [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver) but it seems to me that is still looking at the default driver.

My problem is that the wifi is either slowing down or the browser will say no connection even tho the icon is on full signal. Then every so many minutes it will drop one bar, disconnect, and reconnect. I never had this issue with v. 13** to v14** but I stopped using this computer for a while, not that I am using again I updated the OS and it will not work. Really appreciate any help, its my only computer and I am using for online school. Please help, thank you


:~$ modinfo rtlwifi
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     81DBE78DD4871E3EC5F2E9D
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions

---

### Post by mörgæs on 2016-12-10
Hi, welcome to the fora.

You don't have to add 'HELP!!!!' to the title. Everybody here needs help so there is no point. 

In order to see more of your system please read the sticky notes and post the required output.

---

### Post by jcrodz on 2016-12-10
Thank you for the reply, had to go back to windows.

---

### Post by mörgæs on 2016-12-11
I hope it was not because of networking problems. They are often possible to solve.

Let us know when you want to try Ubuntu again. People here are still ready to help.

---

### Post by jcrodz on 2016-12-14
I had Ubuntu before v12 and 13, once it went to 14 the issues with networking started but at that time I started using a work computer and the other laptop was just stored. Since I no longer had the work computer I had to get back to it, I was hoping to find a fix for the laptop but due to my online school I needed an immediate solution. I searched and searched and searched and nothing. Maybe in a couple of weeks I can do a dual boot and try again, I would rather have Linux on my machine. I didnt try Mint either because I was the issues posted on that as well. Seems to be directly related to the realtek driver, while wired I have no issues is just the wifi connection. I tried different routers to ensure that it was not the router settings.

I will return, where should I post or how should I recall this posting? thank you,

---

### Post by mörgæs on 2016-12-15
When you get back please reuse this thread and post the output required in post 2.

---

### Post by jcrodz on 2016-12-23
I cannot paste the output because it says that i dont have a security token, cannot attach the file either.

---

### Post by mörgæs on 2016-12-24
Could be a problem with the forum software. Try again after some hours.

---

### Post by praseodym on 2016-12-25
Lets try

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot.

---

### Post by jcrodz on 2016-12-28
see atachment

---

### Post by praseodym on 2016-12-28
Hi,

sorry, have a problem opening the file. Can you please c/p the content to the forum in CODE-tags? Thank you

---

### Post by jcrodz on 2016-12-29
I am trying but it gives me to Security Token error since yesterday.

---

### Post by howefield on 2016-12-29
> **jcrodz said:**
> I am trying but it gives me to Security Token error since yesterday.

Pastebin the content and post the link to it...

---

### Post by jcrodz on 2016-12-29
Here is the link to me google doc. [https://docs.google.com/a/jcrodz.com/document/d/1apDupz2Vhg09nvmBkeW_X12XjLRj7InaIZn6ei2qkJA/edit?usp=sharing](https://docs.google.com/a/jcrodz.com/document/d/1apDupz2Vhg09nvmBkeW_X12XjLRj7InaIZn6ei2qkJA/edit?usp=sharing)

---

### Post by QIII on 2016-12-29
Hello!

Please use pastebin.  Believe it or not, not everyone has a Google account.

---

### Post by praseodym on 2016-12-29
Change the country setting to US:

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot and change the channel to "1" in your router

---

### Post by jcrodz on 2016-12-29
```
########## wireless info START ##########


Report from: 28 Dec 2016 14:52 EST -0500


Booted last: 28 Dec 2016 00:00 EST -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8181]
	Kernel driver in use: rtl8192ce


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Toshiba America Info Systems AR8152 v2.0 Fast Ethernet [1179:fcd0]
	Kernel driver in use: atl1c


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:b003 Alcor Micro Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8192ce              57344  0
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        53248  1 rtl8192ce
rtlwifi                77824  3 rtl_pci,rtl8192c_common,rtl8192ce
mac80211              737280  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 toshiba_acpi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2899174 (2.8 MB)  TX bytes:848881 (848.8 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:"BrUjO"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC '' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:160   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       902     1  0 14:41 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188CE 802.11b/g/n WiFi Adapter
GENERAL.DRIVER:                         rtl8192ce
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     BrUjO
GENERAL.CON-UUID:                       d6513e45-5df8-4d6d-81ca-1ee0a9f44bac
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   07a1d6a0-a2f1-45bd-9980-b16dc7598288 | BrUjO_DeUx
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   d6513e45-5df8-4d6d-81ca-1ee0a9f44bac | BrUjO
IP4.ADDRESS[1]:                         192.168.0.107/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1482961298
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.107
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1 0.0.0.0
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8152 v2.0 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0/net/enp3s0
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


SSID                            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                              <MAC '' [AC19]>  Infra  1     2412 MHz  54 Mbit/s  100     ?_?¦  WPA1 WPA2  no        
--                              <MAC '' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  100     ?_?¦  WPA1 WPA2  no        
BrUjO                           <MAC '' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  100     ?_?¦  WPA2       yes     * 
--                              <MAC '' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  87      ?_?¦  --         no        
HP-Print-C9-Officejet 4630      <MAC 'HP-Print-C9-Officejet 4630' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  87      ?_?¦  WPA2       no        
BrUjO                           <MAC '' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  84      ?_?¦  WPA2       yes     * 
BrUjO_DeUx                      <MAC 'BrUjO_DeUx' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  84      ?_?¦  WPA1       no        
xfinitywifi                     <MAC 'xfinitywifi' [AC22]>  Infra  6     2437 MHz  54 Mbit/s  60      ?_?_  --         no        
Meranikula2                     <MAC 'Meranikula2' [AC24]>  Infra  6     2437 MHz  54 Mbit/s  60      ?_?_  WPA1 WPA2  no        
REDFOX                          <MAC 'REDFOX' [AN10]>  Infra  8     2447 MHz  54 Mbit/s  54      ?___  WPA2       no        
xfinitywifi                     <MAC 'xfinitywifi' [AC25]>  Infra  6     2437 MHz  54 Mbit/s  50      ?___  --         no        
--                              <MAC '' [AC33]>  Infra  6     2437 MHz  54 Mbit/s  50      ?___  WPA1 WPA2  no        
DIRECT-roku-308                 <MAC 'DIRECT-roku-308' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  47      ?___  WPA2       no        
--                              <MAC '' [AC34]>  Infra  6     2437 MHz  54 Mbit/s  47      ?___  WPA1 WPA2  no        
--                              <MAC '' [AC21]>  Infra  6     2437 MHz  54 Mbit/s  47      ?___  WPA1 WPA2  no        
HP-Print-61-Officejet Pro 6830  <MAC 'HP-Print-61-Officejet Pro 6830' [AC23]>  Infra  6     2437 MHz  54 Mbit/s  47      ?___  WPA2       no        
RockChalk-2.4                   <MAC 'RockChalk-2.4' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  47      ?___  WPA2       no        
--                              <MAC '' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  47      ?___  WPA1 WPA2  no        
Number1                         <MAC 'Number1' [AC32]>  Infra  6     2437 MHz  54 Mbit/s  44      ?___  WPA1 WPA2  no        
xfinitywifi                     <MAC 'xfinitywifi' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  40      ?___  --         no        
--                              <MAC '' [AC13]>  Infra  11    2462 MHz  54 Mbit/s  40      ?___  WPA1 WPA2  no        
--                              <MAC '--' [AN22]>  Infra  1     2412 MHz  54 Mbit/s  34      ?___  WPA2       no        
--                              <MAC '--' [AN23]>  Infra  1     2412 MHz  54 Mbit/s  34      ?___  WPA2       no        
brady2.4                        <MAC 'brady2.4' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  34      ?___  WPA1 WPA2  no        
xfinitywifi                     <MAC 'xfinitywifi' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  34      ?___  --         no        
--                              <MAC '' [AC18]>  Infra  11    2462 MHz  54 Mbit/s  34      ?___  WPA1 WPA2  no        
--                              <MAC '' [AC20]>  Infra  11    2462 MHz  54 Mbit/s  34      ?___  WPA1 WPA2  no        
--                              <MAC '' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  34      ?___  WPA1 WPA2  no        
xfinitywifi                     <MAC 'xfinitywifi' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  30      ?___  --         no        
NETGEAR80                       <MAC 'NETGEAR80' [AN30]>  Infra  11    2462 MHz  54 Mbit/s  30      ?___  WPA2       no        
J.A.R.V.I.S.                    <MAC 'J.A.R.V.I.S.' [AC15]>  Infra  11    2462 MHz  54 Mbit/s  30      ?___  WPA2       no        
Huskernet                       <MAC 'Huskernet' [AC16]>  Infra  2     2417 MHz  54 Mbit/s  27      ?___  WPA2       no        
--                              <MAC '--' [AN33]>  Infra  4     2427 MHz  54 Mbit/s  27      ?___  --         no        
xfinitywifi                     <MAC 'xfinitywifi' [AC27]>  Infra  11    2462 MHz  54 Mbit/s  27      ?___  --         no        
Oblander WiFi                   <MAC 'Oblander WiFi' [AC26]>  Infra  11    2462 MHz  54 Mbit/s  24      ?___  WPA2       no        
Koreans2687                     <MAC 'Koreans2687' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  20      ?___  WPA2       no        


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


[[/etc/NetworkManager/system-connections/BrUjO]] (600 root)
[connection] id=BrUjO | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=BrUjO
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/BrUjO_DeUx]] (600 root)
[connection] id=BrUjO_DeUx | type=wifi | permissions=user:jcrodz:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=BrUjO_DeUx
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


enp3s0    no frequency information.


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      8   APs on   Frequency:2.437 GHz (Channel 6)
      22   APs on   Frequency:2.462 GHz (Channel 11)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC '' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003136a21d9
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"BrUjO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002eb77b826
                    Extra: Last beacon: 670200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003136a2232
                    Extra: Last beacon: 88ms ago
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0
```

---

### Post by wildmanne39 on 2016-12-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jcrodz on 2016-12-29
It won't let me use tags, it tells me about a missing security token.

---

### Post by wildmanne39 on 2016-12-29
Then use pastebin in the future and post the link here.
[http://pastebin.com/](http://pastebin.com/)
Thanks

---

### Post by wildmanne39 on 2016-12-29
Did the code praseodym posted for you to run help with the issue you are having if not please run the wireless script again and be sure to include all of the output because the one you posted here is missing a lot of information.

---

### Post by jcrodz on 2016-12-29
Unfortunately problem continues, please see link with new output. Thank you [http://pastebin.com/1Xg6D8Rs](http://pastebin.com/1Xg6D8Rs)

---

### Post by wildmanne39 on 2016-12-29
You have a lot of networks in your area so I am sure your device is roaming. Go into your router and set the channel to 4 or 8 this means taking your channel settings off of auto and see if that helps, there is a lot of networks on the same channel as yours. 

There is one other thing we can try that usually helps with that driver but we will do that as a last resort.

---

### Post by jcrodz on 2016-12-29
It was on 11 which was the furthest of the other channels, I changed to 1 per the other directions. I will change back to 8 and retry.

---

### Post by wildmanne39 on 2016-12-29
This is the reason I say changing the channel may help.
```
Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      8   APs on   Frequency:2.437 GHz (Channel 6)
      22   APs on   Frequency:2.462 GHz (Channel 11)

```
The more you have on the same channel the more interference you will have.

Also it may help to set a static mac address if you do not take this computer to different locations.

---

### Post by jcrodz on 2016-12-29
The problem continues, if I want to reinstate all default settings, so i can troubleshoot better can it be done with commands or do I need to reinstall the OS? I have made so many changes based on my findings that maybe some of these are counterfixing the issue. Rather start fresh. Thank you.

---

### Post by wildmanne39 on 2016-12-29
We can see all the settings in the information from the script, we are just making small changes at a time, reinstalling will not fix your issue but you can if you want too.

I suggest we keep working on it a little longer sometimes it is a matter of changing the driver but I would go into the router and change 802.11bgn to 802.11bg that usually fixes the issue when coupled with driver parameters.
```
echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
Edit: I would remove the previous parameter by:
```
sudo -H gedit etc/modprobe.d/rtl8192ce.conf
```
remove one line:
[COLOR="#FF0000"]options rtl8192ce swlps=0 ips=0[/COLOR]
close and save gedit then reboot.

---

### Post by jcrodz on 2016-12-29
The router does not have bg only, has N, GN, or BGN, I changed to BGN and processed the commands. I will test it out now like this. Thank you again,

---

### Post by wildmanne39 on 2016-12-29
I edited the above post to include the directions to remove the previous parameters which is probably a good idea but you can wait and see how the connection does.

---

### Post by jcrodz on 2016-12-29
issue continues, it works well for the first few minutes after a reboot or a change, then it goes from full to 3 bars, and I get the error that there is no internet, the wen it goes to full signal again it works. It keeps cycling that way.

---

### Post by jcrodz on 2017-01-04
Anymore suggestions that I could try? Thank you

---

### Post by wildmanne39 on 2017-01-04
Let's try to set a fixed Mac Address:
```
sudo iwlist scan
```
will show your mac address then go into network manger, choose Edit Connections then click on the Wireless tab. Find your network name in the list and click on Edit then put the mac address from sudo iwlist scan  into the BSSID column and save then reboot.
Does that help?

---

### Post by jcrodz on 2017-01-05
Same issue, this is so frustrating. Thanks for the help.

---

### Post by wildmanne39 on 2017-01-05
Remove the driver you installed, or if you do not know how to do it for sure post the directions you used for installing it.
Then do:
```
sudo apt-get install -y git build-essential
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```
What for errors.
Reboot

When you have a kernel upgrade you will have to do:
```
cd rtlwifi_new
make clean
make
sudo make install

```

---

### Post by jcrodz on 2017-01-05
Its the native driver, below is my built-in info. What I was thinking was to make it all default as I have done several changes. Is the best way to do so a clean install or is there a way to default all the settings? Thank you,

```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b4)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a4)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)



```

---

### Post by wildmanne39 on 2017-01-05
If you reinstall then we have to start all over and we have not made any changes that will hurt the performance of your wifi, install the driver that I posted in my last post then reboot, if you have secure boot on go into the bios and turn it off before installing the driver.
Thanks

---

### Post by jcrodz on 2017-01-09
I completed the steps, the driver being replaced is the same from the update. The step about the MAC address has reduced the issue significantly so I will mark as solved. I truly believe it is a driver issue as when I switched to win 7 on the dual boot there are no issues with the wifi. 

I appreciate your help. Thank you again,

---

### Post by wildmanne39 on 2017-01-14
Your welcome and I am glad it is working.

---


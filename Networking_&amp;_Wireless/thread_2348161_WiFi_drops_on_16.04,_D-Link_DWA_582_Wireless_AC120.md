---
title: "WiFi drops on 16.04, D-Link DWA 582 Wireless AC1200 Dual band PCI-e dual band adapter"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by ks12 on 2017-01-01
Hello, 
I have a new DualBoot Ubuntu 16.04 64 bit, Windows 10 machine that I use for deep learning.
The motherboard is a MSI Z170A Gaming Pro Carbon motherboard. 
On the windows side I get full connection strength upload speeds of ~10-15MBs download and ~3MBs upload using the ookla speedtest, consistent with my plan (max 16MBs).
On the Ubuntu side I get max 3MBs download and about 0.4MBs upload speed if that, but normally the connection dies when I upload anything or just like that. 
I found this out when I tried committing about 3Mb to my github repo. I have tried many times since, but the connection always  dies out during the commit.
Uploads are a consistent way of ending my internet connection. 

I get usually only 2 to 3 bars as on the Wifi icon as connection strength. All other computers  in the house (iMac and MacbookPro 2011) and mobile phones even when they are further away from the router 
get all bars as connection strength and reproduce the windows 10 connection speed quite accurately. But even when I have 4 bars connection strength on the Ubuntu side, the connection drops suddenly.

Things I have tried/ruled out /observed:

1. I have used  my Phone as a local WiFI Hotspot instead of my router. Result: the connection keeps dropping as before.
2. Changed WiFi adapter (twice!). I used to have a different Wifi adapter from TP-Link as opposed to the D-Link Wireless AC1200 DUal Band PCI-e Adapter, model DWA 582 I have now. 
First I swapped  the TP-Link adapter for one of the same make. Didn't help. Then I changed to the D-Link one. Now I am here.
3. I tried 2 different PCI-e slots on the motherboard (no difference, the connection still drops).
4. When the connection is dead usually 3-4 bars get shown as connection strength, but I cannot even connect to the WiFi router by typing 10.0.0.138 in the browser window.
5. I have manually set the IPv6 Settings Method to 'Ignore', no change.
 
I  have attached the output of 
```

lspci -nnk
./wireless-info

```

I'd be glad for any help. I am out of ideas now.

---

### Post by praseodym on 2017-01-01
Change the encryption mode in your router to pure WPA2-AES (CCMP) and a fixed channel

---

### Post by ks12 on 2017-01-01
Thanks I tried it out. Nothing has changed though. 
 I switched the channel from 6 to 1, choice of channel to manual and used WPA2-PSK for encryption.
Speed test upload still works at about 0.4-0.6 MBs while committing to github securely ends my connection after about a minute.

Below is the summary of my Technicolor TG670router configuration 

[HTML]Wireless Access Point - TNCAPE22575
Configuration
WLAN Enable:Yes
Interface Enabled:Yes
Power Reduction Enabled:No
Physical Address:08:76:ff:e2:25:75
Network Name (SSID):TNCAPE22575
Interface Type:802.11b/g/n
Actual Speed [Mbps]:5.5
Band:2.4GHz
Channel Selection:Manual
Region:Europe
Channel:1
Allow multicast from Broadband Network:Yes
WMM:Enabled
Security
WPS Enabled:Yes
Broadcast Network Name:Yes
Allow New Devices:New stations are allowed (automatically)
Security Mode:WPA-PSK
WPA-PSK Preshared Key:<key-as-printed-on-router>
WPA-PSK Encryption:AES
WPA-PSK Version:WPA2[/HTML]

---

### Post by wildmanne39 on 2017-01-01
Let's see if it helps turning power save mode off:
```
echo "options rtl8821ae fwlps=N" | sudo tee -a /etc/modprobe.d/rtl8821ae.conf
```
Reboot

---

### Post by ks12 on 2017-01-01
@[COLOR=#000000]wildmanne39
Thanks, tried out your snippet and rebooted, but nothing changed unfortunately. 
Note: my /etc/modprobe.d/rtl8821ae.conf is empty apart from the line that got echoed into it by the snippet.
[/COLOR][COLOR=#000000][FONT=&quot]

[/FONT][/COLOR]

---

### Post by wildmanne39 on 2017-01-01
We are going to install the latest driver, that should fix your issue, with an internet connection do:
```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtlwifi_new.git
```
```
cd rtlwifi-new
make
sudo make install
```
Reboot

This installs the driver for the current Kernel version only, when there is an upgrade to the kernel you have to do:
```
cd rtlwifi-new
make clean
make
sudo make install
```

One of the main reasons we change drivers is so you can set the following parameter that changes which antenna is being used so please do:
```
sudo -H gedit /etc/modprobe.d/rtl8821ae.conf
```
enter your password, when the file opens remove [COLOR="#FF0000"]options rtl8821ae fwlps=N[/COLOR] then add [COLOR="#FF0000"]options rtl8723be ant_sel=2[/COLOR]
then save and close gedit.
Reboot

---

### Post by ks12 on 2017-01-02
@wildmanne39
Thanks a lot for dealing with this, I followed your instructions. New driver is successfully installed and on speedtest the upload speed is now ~5-8x faster, i.e 3Mbps, download ~7-8Mbps. Hooray! However, these speeds only apply if the test finishes.
The Wifi connection still disappears frequently with the connection bars nevertheless showing that I am connected. I have to manually click on disconnect, wait about 30 seconds until Chrome gets shortly unresponsive and I get the message that I am disconnected. I then click on my WiFI network to reconnect. 
This happens also when I commit to github. If I let ```
ping google.com
``` run in a separate tab,  sometimes within seconds after ```
git push origin master
``` no packages come back. Other times it takes up to a minute for the pings to die. Nothing similar happens during git pull.
Just then the connection died when I tried to connect to my wifi router by typing its IP in the browser. The connection disappears all of a sudden, but the status bars don't care and still show 3 out of 4 bars. This is the weird thing. I thought if I see a connection I should at least be able to connect to the router, but No.
Any ideas what might be going on?

---

### Post by wildmanne39 on 2017-01-02
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by ks12 on 2017-01-02
Thank you +1. Here is the output of the current run of the wireless-info script.
```



########## wireless info START ##########


Report from: 02 Jan 2017 21:41 CET +0100


Booted last: 02 Jan 2017 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Ethernet Connection (2) I219-V [1462:7a12]
    Kernel driver in use: e1000e


05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter [10ec:8812] (rev 01)
    Subsystem: D-Link System Inc RTL8812AE 802.11ac PCIe Wireless Network Adapter [1186:3305]
    Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1a7c:0068 Evoluent VerticalMouse 3
Bus 001 Device 002: ID 0079:0002 DragonRise Inc. 
Bus 001 Device 007: ID 8644:800e Intenso GmbG 
Bus 001 Device 006: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 005: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


mxm_wmi                16384  0
rtl8821ae             225280  0
btcoexist             167936  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF1]>  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:df300000-df320000 


wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF3]>  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp5s0' [IF3]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92566221 (92.5 MB)  TX bytes:17910657 (17.9 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp0s31f6  no wireless extensions.


docker0   no wireless extensions.


wlp5s0    IEEE 802.11abgn  ESSID:"TNCAPE22575"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'TNCAPE22575' [AC1]>   
          Bit Rate=130 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:22   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    600    0        0 wlp5s0
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 docker0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       998     1  0 20:36 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       61b1f5d5-fcad-45e6-a5b0-db0f8c6e1d57
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   61b1f5d5-fcad-45e6-a5b0-db0f8c6e1d57 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8812AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TNCAPE22575 2
GENERAL.CON-UUID:                       e223c5fc-054a-4a41-9f4b-5f9c6e7f3c4c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     130 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e223c5fc-054a-4a41-9f4b-5f9c6e7f3c4c | TNCAPE22575 2
IP4.ADDRESS[1]:                         10.0.0.2/24
IP4.GATEWAY:                            10.0.0.138
IP4.DNS[1]:                             10.0.0.138
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1483473123
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.0.0.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 10.0.0.138
DHCP4.OPTION[19]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 10.0.0.138
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 10.0.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 10.0.0.138
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp5s0' [IF3]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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


SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
TNCAPE22575  <MAC 'TNCAPE22575' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2      yes     * 


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


[[/etc/NetworkManager/system-connections/TNCAPE22575 2]] (600 root)
[connection] id=TNCAPE22575 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=TNCAPE22575
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/TNCAPE22575]] (600 root)
[connection] id=TNCAPE22575 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TNCAPE22575
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


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


enp0s31f6  no frequency information.


docker0   no frequency information.


wlp5s0    32 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s31f6  Interface doesn't support scanning.


docker0   Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'TNCAPE22575' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TNCAPE22575"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014ae4ec3a5
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B435D5267F2688C985B95CB
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     19B89B411F940E4D0BCB623
depends:        mac80211,rtlwifi
vermagic:       4.4.0-57-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C9A49AFB21144B711489EA0
depends:        mac80211,cfg80211
vermagic:       4.4.0-57-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
swenc: N
swlps: N


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


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8723be ant_sel=2


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    6.918937] wlp5s0: authenticated
[    6.921448] wlp5s0: associate with <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[    6.924855] wlp5s0: RX AssocResp from <MAC 'TNCAPE22575' [AC1]> (capab=0x411 status=0 aid=4)
[    6.925038] wlp5s0: associated
[    6.925071] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[  560.760036] wlp5s0: deauthenticating from <MAC 'TNCAPE22575' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  588.852484] wlp5s0: authenticate with <MAC 'TNCAPE22575' [AC1]>
[  593.675544] wlp5s0: send auth to <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[  593.677826] wlp5s0: authenticated
[  593.678785] wlp5s0: associate with <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[  593.683609] wlp5s0: RX AssocResp from <MAC 'TNCAPE22575' [AC1]> (capab=0x411 status=0 aid=4)
[  593.683828] wlp5s0: associated
[  874.353225] wlp5s0: deauthenticating from <MAC 'TNCAPE22575' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  906.564779] wlp5s0: authenticate with <MAC 'TNCAPE22575' [AC1]>
[  907.484189] wlp5s0: send auth to <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[  907.487112] wlp5s0: authenticated
[  907.487461] wlp5s0: associate with <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[  907.490892] wlp5s0: RX AssocResp from <MAC 'TNCAPE22575' [AC1]> (capab=0x411 status=0 aid=4)
[  907.491084] wlp5s0: associated
[ 1914.961588] wlp5s0: deauthenticated from <MAC 'TNCAPE22575' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 1915.084878] wlp5s0: authenticate with <MAC 'TNCAPE22575' [AC1]>
[ 1915.085578] wlp5s0: send auth to <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[ 1915.087169] wlp5s0: authenticated
[ 1915.088663] wlp5s0: associate with <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[ 1915.092092] wlp5s0: RX AssocResp from <MAC 'TNCAPE22575' [AC1]> (capab=0x411 status=0 aid=4)
[ 1915.092312] wlp5s0: associated
[ 3032.030274] rtlwifi: AP off, try to reconnect now
[ 3032.030328] wlp5s0: Connection to AP <MAC 'TNCAPE22575' [AC1]> lost
[ 3035.047568] wlp5s0: authenticate with <MAC 'TNCAPE22575' [AC1]>
[ 3035.048279] wlp5s0: send auth to <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[ 3035.050668] wlp5s0: authenticated
[ 3035.054219] wlp5s0: associate with <MAC 'TNCAPE22575' [AC1]> (try 1/3)
[ 3035.057619] wlp5s0: RX AssocResp from <MAC 'TNCAPE22575' [AC1]> (capab=0x411 status=0 aid=4)
[ 3035.057813] wlp5s0: associated


########## wireless info END ############

```

---

### Post by jeremy31 on 2017-01-02
Let's disable the powersave that is enabled by network manager
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

And run the command wildmanne39 posted in post #4

---

### Post by ks12 on 2017-01-02
@jeremy31: thanks. 
I followed your instructions, executed the command wildmanne39 posted and rebooted (it became unresponsive after >sudo reboot  up so I had to push the on/off button). 
Unfortunately no improvement in the WiFi behavior. "git push" kills my network connection consistently and after reconnecting I just lost connection while typing this message

To rule out me doing something stupid I double-checked the content of my /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

[connection] 
wifi.powersave = 2

```

as well as of  /etc/modprobe.d/rtl8821ae.conf which now reads
```

options rtl8723be ant_sel=2
options rtl8821ae fwlps=N

```

---

### Post by jeremy31 on 2017-01-03
We can change the one file back just in case it conflicts somehow with the fwlps
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by ks12 on 2017-01-03
@jeremy31 
thanks heaps for your help.
I changed wifi.powersafe back and forth between 2 and 3 (where it is now), rebooted each time and checked the connection. 

No significant difference:
* uploading a 3MB dummy image to github still safely kills my connection. Just then running the speedtest did. 
* When the speedtest runs through, the measured speed fluctuates wildly between 
0.8 Mbps and occasionally up to 5 Mbps, upload  maxes out (rather rarely) at 0.8 Mbps. (however, to be taken with a grain of salt: 
the speedtest still shows a connection for some time, when "ping google.com" is already all silent). 
* I also tried switching the channel on the router back to 6 from 1, but no change. 

If I hadn't switched the WiFI Adapter two times already, I'd probably try buying a new one, but as it is I am dumbfounded.

---

### Post by dwayne-e on 2017-06-27
I had a very similar problem as ks12 - Ubuntu 16.04 with a D-Link AC-1200 that would drop connections within minutes.

 I tried turning the power save mode off as suggested by @wildmanne39 in #4 and disabling the powersave enabled by network manager as suggested by @jeremy31 in #10. I'm not sure if it was the latter or a combination, but that did the trick. Both 2.4GHz and 5Ghz bands have been working flawlessly all day, 5G delivering expected speeds.

Leaving this here as a note to anyone with a similar problem that this worked, and to thank both posters for their help![COLOR=#000000]
[/COLOR]

---


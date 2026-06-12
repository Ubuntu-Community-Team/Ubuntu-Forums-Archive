---
title: "Internet Connection"
date: 2017-08-30
forum: Networking &amp; Wireless
---

### Post by mimi-magusin on 2017-08-30
Hi! 

There's many posts like this, but I'm just not sure which apply to me, so I will try again:

I got a dual boot (Windows 10 & Ubuntu 16.04) and have troubles with the wifi connection. It worked fine for a couple of days, but today, it disconnects every 5-10 minutes  or doesn't load webpages (even though it tells me it is connected in the menu in the right top corner). Other devices don't  have problems on the same network. Sometimes I just have to disconnect and connect manually, but more often it says 'device is not ready' (for a very long time)  and I have to reboot the computer to make it work again.

I updated and upgraded in the terminal (and rebooted), and switched off the energy save options in the windows network manager, it didn't help yet. I read it might have something to do with the fact that i have a 'realtek 8821 AE wireless LAN 802.11 ac' , but I don't understand the topics. Would anyone know what to do? If you need more info please let me know!

Many thanks in advance!
Mimi

---

### Post by slickymaster on 2017-08-30
Moved to the **Networking & Wireless** sub-forum

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself.

---

### Post by mimi-magusin on 2017-08-30
Thanks for the reply! Do I paste the text of the wireless info script into the terminal?

---

### Post by slickymaster on 2017-08-30
> **mimi-magusin said:**
> Thanks for the reply! Do I paste the text of the wireless info script into the terminal?

In your Ubuntu box, and using a wired connection, open a terminal window (Ctrl+Alt+T) and run the following```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by mimi-magusin on 2017-08-30
Thank you! I think I managed. The file was to big to attach so I put it in paste bin. Can you acces it through this link? [https://pastebin.com/XDn0tzf4](https://pastebin.com/XDn0tzf4)

---

### Post by slickymaster on 2017-08-30
Yes, the link is accessible.

Now, please be patient and one of our N&W gurus will soon provide you the help you need.

---

### Post by mimi-magusin on 2017-08-30
This is it as well:


```
########## wireless info START ##########
 
Report from: 30 Aug 2017 16:10 CEST +0200
 
Booted last: 30 Aug 2017 00:00 CEST +0200
 
Script from: 25 Mar 2017 07:04 UTC +0000
 
##### release ###########################
 
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:   xenial
 
##### kernel ############################
 
Linux 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 
Parameters: ro, quiet, splash, vt.handoff=7
 
##### desktop ###########################
 
Ubuntu
 
##### lspci #############################
 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:388a]
    Kernel driver in use: r8169
 
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821ae
 
##### lsusb #############################
 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:210f Acer, Inc
Bus 001 Device 003: ID 0bda:0821 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
##### PCMCIA card info ##################
 
##### rfkill ############################
 
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
 
##### lsmod #############################
 
rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                73728  2 rtl_pci,rtl8821ae
mac80211              782336  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              602112  2 mac80211,rtlwifi
ideapad_laptop         28672  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    16384  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop
 
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
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47818 (47.8 KB)  TX bytes:47818 (47.8 KB)
 
wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:172.16.29.213  Bcast:172.16.31.255  Mask:255.255.252.0
          inet6 addr: fe80::574d:497c:7341:357f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2278573 (2.2 MB)  TX bytes:263050 (263.0 KB)
 
##### iwconfig ##########################
 
enp1s0    no wireless extensions.
 
lo        no wireless extensions.
 
wlp2s0    IEEE 802.11  ESSID:"Codaisseur"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'Codaisseur' [AN4]>  
          Bit Rate=200 Mb/s   Tx-Power=30 dBm  
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0
 
##### route #############################
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.28.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
172.16.28.0     0.0.0.0         255.255.252.0   U     600    0        0 wlp2s0
 
##### resolv.conf #######################
 
nameserver 127.0.1.1
search localdomain
 
##### network managers ##################
 
Installed:
 
    NetworkManager
    Wicd
 
Running:
 
root       787     1  0 16:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
 
##### NetworkManager info ###############
 
GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.10.0-33-generic
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
GENERAL.CONNECTION:                     Codaisseur
GENERAL.CON-UUID:                       8c8c0dea-baa2-40a4-93f0-bfee7b5fde4e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     200 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   47a1aaf9-6a80-4393-a63d-37008926fb76 | Brand Ambassadors
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   8c8c0dea-baa2-40a4-93f0-bfee7b5fde4e | Codaisseur
IP4.ADDRESS[1]:                         172.16.29.213/22
IP4.GATEWAY:                            172.16.28.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.16.28.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1504188508
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 172.16.28.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 172.16.29.213
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = localdomain
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 172.16.31.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 172.16.28.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.252.0
DHCP4.OPTION[26]:                       network_number = 172.16.28.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.16.28.1
IP6.ADDRESS[1]:                         fe80::574d:497c:7341:357f/64
IP6.GATEWAY:                            
 
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
 
SSID                         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  *
Codaisseur                   <MAC 'Codaisseur' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Codaisseur                   <MAC 'Codaisseur' [AN2]>  Infra  44    5220 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
LP Staf                      <MAC 'LP Staf' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Codaisseur                   <MAC 'Codaisseur' [AN4]>  Infra  44    5220 MHz  54 Mbit/s  78      &#9602;&#9604;&#9606;_  WPA2       yes     *
--                           <MAC '--' [AN5]>  Infra  10    2457 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2       no        
Codaisseur                   <MAC 'Codaisseur' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2       no        
LP Amsterdam                 <MAC 'LP Amsterdam' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
--                           <MAC '--' [AN8]>  Infra  100   5500 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2       no        
ramdihal-advocaten           <MAC 'ramdihal-advocaten' [AN9]>  Infra  3     2422 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
--                           <MAC '--' [AN10]>  Infra  13    2472 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
TP-LINK_4F8EBE               <MAC 'TP-LINK_4F8EBE' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
Brand Ambassadors            <MAC 'Brand Ambassadors' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
--                           <MAC '--' [AN13]>  Infra  2     2417 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
DIRECT-EF-HP Officejet 5740  <MAC 'DIRECT-EF-HP Officejet 5740' [AN14]>  Infra  8     2447 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
dirk                         <MAC 'dirk' [AN15]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        
Eijsink70530                 <MAC 'Eijsink70530' [AN16]>  Infra  1     2412 MHz  11 Mbit/s  40      &#9602;&#9604;__  WEP        no        
 
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
 
[[/etc/NetworkManager/system-connections/Codaisseur]] (600 root)
[connection] id=Codaisseur | type=wifi | permissions=user:mimi:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Codaisseur
[ipv4] method=auto
[ipv6] method=auto
 
[[/etc/NetworkManager/system-connections/Brand Ambassadors]] (600 root)
[connection] id=Brand Ambassadors | type=wifi | permissions=user:mimi:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Brand Ambassadors
[ipv4] method=auto
[ipv6] method=auto
 
[[/etc/NetworkManager/system-connections/ZiggoE8561CB]] (600 root)
[connection] id=ZiggoE8561CB | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ZiggoE8561CB
[ipv4] method=auto
[ipv6] method=auto
 
[[/etc/NetworkManager/system-connections/Ziggo03783]] (600 root)
[connection] id=Ziggo03783 | type=wifi | permissions=user:mimi:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Ziggo03783
[ipv4] method=auto
[ipv6] method=auto
 
##### iw reg get ########################
 
Region: Europe/Amsterdam (based on set time zone)
 
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
 
enp1s0    no frequency information.
 
lo        no frequency information.
 
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
          Current Frequency:5.22 GHz (Channel 44)
 
##### iwlist scan #######################
 
enp1s0    Interface doesn't support scanning.
 
wlp2s0    Failed to read scan data : Resource temporarily unavailable
 
lo        Interface doesn't support scanning.
 
##### module infos ######################
 
[rtl8821ae]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE <wlanfae@realtek.com>
srcversion:     7035D4BEF647A4E63CBD578
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload
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
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming  <chaoming_li@realsil.com.cn>
srcversion:     B93F82B28F7945C22514E4D
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload
 
[rtlwifi]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming  <chaoming_li@realsil.com.cn>
srcversion:     884DE3F31278351A45DA409
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload
 
[mac80211]
filename:       /lib/modules/4.10.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
 
[cfg80211]
filename:       /lib/modules/4.10.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
 
[    2.025257] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[    2.025259] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_config.bin
[    2.039196] bluetooth hci0: Direct firmware load for rtl_bt/rtl8821a_config.bin failed with error -2
[    2.039200] Bluetooth: hci0: Failed to load rtl_bt/rtl8821a_config.bin
[    2.039203] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[    2.094758] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[    2.094763] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[    2.120657] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.120906] rtlwifi: rtlwifi: wireless switch is on
[    2.241352] rtl8821ae 0000:02:00.0 wlp2s0: renamed from wlan0
[    3.777936] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[    4.044125] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.061764] r8169 0000:01:00.0 enp1s0: link down
[    4.061820] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.140987] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   10.290223] wlp2s0: authenticate with <MAC 'Codaisseur' [AN4]>
[   10.293480] wlp2s0: send auth to <MAC 'Codaisseur' [AN4]> (try 1/3)
[   10.299310] wlp2s0: authenticated
[   10.303447] wlp2s0: associate with <MAC 'Codaisseur' [AN4]> (try 1/3)
[   10.308586] wlp2s0: RX AssocResp from <MAC 'Codaisseur' [AN4]> (capab=0x411 status=0 aid=23)
[   10.309863] wlp2s0: associated
[   10.310192] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
 
########## wireless info END ############
```

---

### Post by mimi-magusin on 2017-08-30
ok, thank you! :)

---

### Post by slickymaster on 2017-08-31
bumping this one for the OP benefit.

@mimi-magusin:
It is appropriate to bump a thread (by simply adding a new post with the word "bump") if you do not get a reply in a reasonable amount of time. We have relaxed the 24 hour restriction on bumping. A 12 hour bump will expose your thread to a different group of people somewhere in the world.

---

### Post by praseodym on 2017-08-31
The ESSID is available both in the 2,4 and 5 GHz region. Maybe roaming disconnects?! Chose the MAC address of the better AP and add it in the BSSID field in the network manager applet. To show them:
```

sudo iwlist scan
```
when it works

---

### Post by johndough2 on 2017-09-01
Hi

I noticed that too.

You have more than 1 channel 44 in use it seems...

Codaisseur                   <MAC 'Codaisseur' [AN2]>  Infra  44    5220 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Codaisseur                   <MAC 'Codaisseur' [AN4]>  Infra  44    5220 MHz  54 Mbit/s  78      &#9602;&#9604;&#9606;_  WPA2       yes     * 

so it may be that you could be jumping between the active line 2 and the inactive but stronger line 1.

As  praseodym suggests, a tidy up.

---


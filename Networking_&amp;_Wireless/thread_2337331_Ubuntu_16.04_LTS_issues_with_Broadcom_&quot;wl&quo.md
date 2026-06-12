---
title: "Ubuntu 16.04 LTS issues with Broadcom &quot;wl&quot; WLAN driver (BCM43142 [14e4:4365])"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by occasionalbicyclist on 2016-09-16
The wife just got a new HP Ultrabook that we immediately installed Ubuntu 16.04 on.

However the Broadcom wireless driver (**wl**) for the WLAN card (**BCM43142 [14e4:4365]**) delivered via the **bcmwl-kernel-source** package, seems to be somewhat... unstable.

It is possible to see WLAN networks, and then to connect them. However when connected, the ping response time is often very high and we also often see high packet loss. Browsing and downloading are also affected.
This can sometimes be improved by disabling power management on the interface ([FONT=courier new]sudo iwconfig wlp1s0 power off[FONT=arial])
[/FONT][/FONT]
We have tried different versions of Ubuntu (14.04, 15.10 and 16.10) without any noticeable difference. We have also tried downgrading the kernel (*4.2.0-42, 4.2.8, 3.13.0-24, 3.13.0-37*) and tried different versions of the bcmwl-kernel-source package (*6.30.223.248+bdcom-0ubuntu8_amd64, 6.30.223.248+bdcom-0ubuntu7_amd64, 6.30.223.141+bdcom-0ubuntu2_amd64*).
All to no avail...

Does anyone have any ideas of what else we can try?



**Driver and Kernel version:**
```

user@notebook1:~$ uname -a
Linux notebook1 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

user@notebook1:~$ dpkg -s bcmwl-kernel-source
Package: bcmwl-kernel-source
[...]
Version: 6.30.223.248+bdcom-0ubuntu8
```

**Hardware:**
```

user@notebook1:~$ lspci -nn
[...]
01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```

**Example of high pings and packet loss:**
```

user@notebook1:~$ ping -c 20 10.0.0.138
PING 10.0.0.138 (10.0.0.138) 56(84) bytes of data.
64 bytes from 10.0.0.138: icmp_seq=5 ttl=63 time=1146 ms
64 bytes from 10.0.0.138: icmp_seq=6 ttl=63 time=157 ms
64 bytes from 10.0.0.138: icmp_seq=8 ttl=63 time=1184 ms
64 bytes from 10.0.0.138: icmp_seq=9 ttl=63 time=183 ms
64 bytes from 10.0.0.138: icmp_seq=10 ttl=63 time=3.95 ms
64 bytes from 10.0.0.138: icmp_seq=12 ttl=63 time=133 ms
64 bytes from 10.0.0.138: icmp_seq=15 ttl=63 time=2.35 ms
64 bytes from 10.0.0.138: icmp_seq=16 ttl=63 time=3.39 ms
64 bytes from 10.0.0.138: icmp_seq=18 ttl=63 time=294 ms
64 bytes from 10.0.0.138: icmp_seq=19 ttl=63 time=169 ms
64 bytes from 10.0.0.138: icmp_seq=20 ttl=63 time=122 ms

--- 10.0.0.138 ping statistics ---
20 packets transmitted, 11 received, 45% packet loss, time 19064ms
rtt min/avg/max/mdev = 2.356/309.200/1184.189/412.446 ms, pipe 2
```

---

### Post by wildmanne39 on 2016-09-16
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by occasionalbicyclist on 2016-09-17
Thanks for the reply Wild Man.

Please find output of script below:

```


########## wireless info START ##########


Report from: 17 Sep 2016 09:56 CEST +0200


Booted last: 17 Sep 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 002: ID 05c8:0389 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wl                   6365184  0
cfg80211              565248  1 wl
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          inet addr:192.168.88.182  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp1s0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1872 errors:0 dropped:0 overruns:0 frame:37628
          TX packets:1998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1136489 (1.1 MB)  TX bytes:519401 (519.4 KB)
          Interrupt:17 


##### iwconfig ##########################


lo        no wireless extensions.


wlp1s0    IEEE 802.11abg  ESSID:"crashbandicoot"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'crashbandicoot' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.88.200  0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.88.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2829     1  0 09:49 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
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
GENERAL.CONNECTION:                     crashbandicoot
GENERAL.CON-UUID:                       25ec13e0-fca0-4b22-ab3f-2ee17c7d4ac1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   25ec13e0-fca0-4b22-ab3f-2ee17c7d4ac1 | crashbandicoot
IP4.ADDRESS[1]:                         192.168.88.182/24
IP4.GATEWAY:                            192.168.88.200
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.88.200
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.88.200
DHCP4.OPTION[5]:                        ip_address = 192.168.88.182
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.88.200
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.88.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.88.200
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1474141918
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = laptop1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.88.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.88.200
DHCP4.OPTION[29]:                       ntp_servers = 192.168.88.200
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp1s0' [IF1]>/64
IP6.GATEWAY:                            


SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
UPC1353929      <MAC 'UPC1353929' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2         no        
UPC Wi-Free     <MAC 'UPC Wi-Free' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 802.1X  no        
UPC2686074      <MAC 'UPC2686074' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
UPC Wi-Free     <MAC 'UPC Wi-Free' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2 802.1X       no        
UPC Wi-Free     <MAC 'UPC Wi-Free' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X  no        
UPC2344851      <MAC 'UPC2344851' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
crashbandicoot  <MAC 'crashbandicoot' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2              yes     * 
UPC1622292      <MAC 'UPC1622292' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        


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


[[/etc/NetworkManager/system-connections/crashbandicoot]] (600 root)
[connection] id=crashbandicoot | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=crashbandicoot
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/deathstar]] (600 root)
[connection] id=deathstar | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=deathstar
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


country AT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.437 GHz (Channel 6)


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'crashbandicoot' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"crashbandicoot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC1353929' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"UPC1353929"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'UPC Wi-Free' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'UPC2686074' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UPC2686074"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'UPC Wi-Free' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[wl]
filename:       /lib/modules/4.4.0-36-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


sleep 10
iwconfig wlp1s0 power off


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/power_off] (755 root)
/sbin/iwconfig wlp1s0 power off


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[  173.125468] wl 0000:01:00.0 wlp1s0: renamed from wlan0
[  173.217598] wlp1s0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[  173.231673] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  450.898719] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############



```

---

### Post by praseodym on 2016-09-17
The 248 driver is too old, try this one:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```

---

### Post by occasionalbicyclist on 2016-09-19
thanks @praseodym for the tipp. We downloaded and successfully installed the driver you recommended.
This driver definitely performs better than the other drivers, but it still has occasional periods of unexpected high pings and ping loss.

is this normal behavior with these broadcom chipsets on linux? or should we be seeing better performance than this?

Thanks again for the help

---

### Post by 7dEfOk4AgU on 2016-09-19
I am currently managing a project to deploy 150 desktops and 100 laptops. The laptops have similar WiFi chips to these and Ubuntu is being troublesome. Ethernet is no issue by WiFi is just a pain and could be a deal breaker

---

### Post by wildmanne39 on 2016-09-19
@mikeb42 Please start your own thread and do not hijack someone else's, please click on the wireless script in my signature and follow the directions for running the script and posting the results in your new thread.

I will try to help with one wifi but if you need a lot of different laptops working that do not have the exact hardware with the exact same issue you may want to check into professional support from Canonical.
Thanks

---

### Post by 7dEfOk4AgU on 2016-09-19
Apologies, I thought you would keep similar issues in the same area.

---

### Post by occasionalbicyclist on 2016-09-26
Sorry to bump this thread, but does anyone have any ideas of improving the performance of this WLAN chipset under linux / ubuntu?

BR

---

### Post by Hadaka on 2016-09-26
Hi, the bcmwl-kernel-source "wl" driver  for (BCM43142 [14e4:4365]) is correct.
you have ignored IPv6 and have your power management set to "Off", you also
have installed the updated wl driver that praseodym suggested. Your country code
is set correctly also. Other than changing your current wifi channel from Ch. 6 to Ch. 1 or 11
you are probably getting the best performance from that wifi card as you are going to get.
you are currently operating in the 2.4 GHz range and the broadcom wl driver at present does
not operate in the 5 GHz mode. Jermy31 was working on a fix for this but i do not know if one
has yet to be found. Perhaps he will chime in and bring us up to date on any progress or  fix.
About the best suggest I can think of at this time is to replace the broadcom card with an intel
that is compatible with your machine and will run on  2.4 or 5 GHz.

---

### Post by amipengyou on 2016-09-29
Hi, 
1/ sorry but english is not my native language.
2/ i have the same problem with the same card on Ubuntu 16.04
i have read and use the process by Wild Man (thank you for your help) but it seems, the driver don't upgrade.
i have write in purple all actions on terminal.
and disable UEFI secure boot for upgrade driver.
thanks[ATTACH]271410[/ATTACH][ATTACH]271411[/ATTACH][ATTACH]271412[/ATTACH]

---

### Post by amipengyou on 2016-09-29
It is OK !!
i have wifi now.
UEFI disappointed me...
i disable Secure Boot control and enable launch CSM.
Thank you all !!!

---

### Post by Leon A on 2016-12-01
You are not alone.  We have deployed hundreds of laptops in African classrooms, and I am still fighting connection drop out issues with the BCM43142 cards.  I've tried every (I think) tip found on this forum.  At times they will connect and ping the AP router 100% for long periods of time, then suddenly start showing ping times of thousands of ms and eventually stop with destination unreachable.  Usually disabling networking, then re-enable {or toggling Airplane mode on/off} will reset and run clean again, but sometimes it takes reboot. 
I have the advantage of testing the exact hardware with Win8 before we wipe the drive and install Lubuntu 15.10 (previously ran 14.04LTS, have also tried 16.04 which seems even worse) and they run clean in Windows, so I know the hardware is capable of running cleanly. One thing I found in the similar versions that use a RTL8732be card is that the netbooks have only one antenna cable, so one port of the card is empty.  The default RTL driver can't change to the correct port so you have to install a patched driver or physically move the antenna cable on the WiFi card.  But I don't find any BCM drivers that give the option to select antenna 2. [ I did find a note mentioning a new BCM driver has been submitted with antenna selection enabled, but it won't be incorporated into Debian until kernel 4.7 or so, and we are currently still back on kernel 4.4]. I also suspect it may have something to do with buffers filling up or firewall overloading, but none of the suggestions found so far help.
Hopefully this will help you and others understand the extent of the problem and maybe some smart person out there will develop a working driver.

---


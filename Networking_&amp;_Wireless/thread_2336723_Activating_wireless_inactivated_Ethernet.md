---
title: "Activating wireless inactivated Ethernet"
date: 2016-09-10
forum: Networking &amp; Wireless
---

### Post by 78plus on 2016-09-10
I inactivated the internal Broadcom wireless device in my old Dell Vostro 1700 notebook by turning it off in the BIOS, and then executed the code listed in westie457's input to thread 2117798; i.e., 

sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl

I then plugged a Ralink 802.11 Wireless LAN Card into one of the Vostro's USB ports and was immediately able to connect to the Internet wirelessly. However, as the thread warned, the code had side effects. I would appreciate help in un-blacklisting ssb and doing whatever else is necessary to reestablish Ethernet connectivity because I haven't been able to locate the post mentioned in item #10 in the aforementioned thread.

---

### Post by wildmanne39 on 2016-09-10
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by 78plus on 2016-09-10
Thank you! This is my first attempt to wrap text in CODE boxes and I hope it works. And if I was't clear initially, my wireless is working but my Ethernet connection has been rendered inert. I'd like to get it working again in case I take the computer somewhere that doesn't have wireless service.
```



########## wireless info START ##########


Report from: 10 Sep 2016 21:26 EDT -0400


Booted last: 10 Sep 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell BCM4401-B0 100Base-TX [1028:0229]
    Kernel modules: b44


##### lsusb #############################


Bus 002 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 002: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


mac80211              737280  1 mt7601u
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
cfg80211              565248  2 mac80211,mt7601u
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
mxm_wmi                16384  1 nouveau
video                  40960  3 dell_wmi,nouveau,dell_laptop
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF1]>' [IF1]>  
          inet addr:10.0.0.174  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:346:c100:2138::2161/128 Scope:Global
          inet6 addr: 2601:346:c100:2138:f528:2cf5:80ef:6363/64 Scope:Global
          inet6 addr: 2601:346:c100:2138:cf50:298a:1a04:8476/64 Scope:Global
          inet6 addr: fe80::81ff:33d2:68fa:d8d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:940659 (940.6 KB)  TX bytes:223022 (223.0 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlx<IF from MAC [IF1]>  IEEE 802.11bgn  ESSID:"HOME-4457-2.4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'HOME-4457-2.4' [AC1]>   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:94   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF1]>
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx<IF from MAC [IF1]>


##### resolv.conf #######################


nameserver 127.0.1.1
search hsd1.fl.comcast.net


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2456     1  0 21:17 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         148f
GENERAL.PRODUCT:                        7601
GENERAL.DRIVER:                         mt7601u
GENERAL.DRIVER-VERSION:                 4.4.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/net/wlx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HOME-4457-2.4
GENERAL.CON-UUID:                       91e1c51c-cd5b-42a2-b012-54b2f26bb5a9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     39 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   91e1c51c-cd5b-42a2-b012-54b2f26bb5a9 | HOME-4457-2.4
IP4.ADDRESS[1]:                         10.0.0.174/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.fl.comcast.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 10.0.0.174
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 10.0.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 10.0.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 10.0.0.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.fl.comcast.net
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1474161471
DHCP4.OPTION[21]:                       host_name = bill-Vostro-1700
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.0.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
IP6.ADDRESS[1]:                         2601:346:c100:2138::2161/128
IP6.ADDRESS[2]:                         2601:346:c100:2138:f528:2cf5:80ef:6363/64
IP6.ADDRESS[3]:                         2601:346:c100:2138:cf50:298a:1a04:8476/64
IP6.ADDRESS[4]:                         fe80::81ff:33d2:68fa:d8d4/64
IP6.GATEWAY:                            fe80::f44b:2aff:fe19:445a
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:de:cc:3c:5d:5b:38:bb:c:a8:7a:a3:a8:1b:d2:2c:51
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        rebind = 483840
DHCP6.OPTION[5]:                        max_life = 604800
DHCP6.OPTION[6]:                        preferred_life = 604800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1473523465
DHCP6.OPTION[10]:                       dhcp6_status_code = success All addresses were assigned.
DHCP6.OPTION[11]:                       ip6_address = 2601:346:c100:2138::2161
DHCP6.OPTION[12]:                       ip6_prefixlen = 64
DHCP6.OPTION[13]:                       renew = 302400
DHCP6.OPTION[14]:                       starts = 1473523465
DHCP6.OPTION[15]:                       iaid = 06:22:67:90
DHCP6.OPTION[16]:                       dhcp6_server_id = 0:1:0:1:1f:55:23:65:6:cf:50:4:46:31


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
xfinitywifi    <MAC 'xfinitywifi' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
--             <MAC '' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
HOME-4457-2.4  <MAC 'HOME-4457-2.4' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 


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


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=HOME-4457-5
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-4457-2.4]] (600 root)
[connection] id=HOME-4457-2.4 | type=wifi | permissions=user:bill:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=HOME-4457-2.4
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


wlx<IF from MAC [IF1]>  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)


wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'HOME-4457-2.4' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"HOME-4457-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f6566a33b0
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xfinitywifi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f6569db180
                    Extra: Last beacon: 132ms ago
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f6569db180
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


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


lp


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
blacklist b44
install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl ; modprobe --ignore-install b44


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   17.820976] wlx<IF from MAC [IF1]>: associated
[   17.821060] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF1]>: link becomes ready


########## wireless info END ############

```

---

### Post by wildmanne39 on 2016-09-10
Please do:
```
sudo -H gedit /etc/modprobe.d/blacklist-bcm43.conf
```
then put # in front of [COLOR="#0000CD"]blacklist ssb[/COLOR] and [COLOR="#0000CD"]blacklist b44[/COLOR]
Then save and close gedit and reboot.

---

### Post by 78plus on 2016-09-10
Thanks for the prompt reply. I followed your instructions but to my surprise, there are no "blacklist ssb" or "blacklist b44" entries in "blacklist.conf." However, there is a "blacklist eth1394" entry that is not commented out. The text ahead of it indicates that eth1394 causes problems by causing extra connections. Far be it from me to question that information so I left that entry as is, but it does arouse my curiosity.

---

### Post by wildmanne39 on 2016-09-10
I edited the above post I put the wrong file name,  sorry about that.

---

### Post by 78plus on 2016-09-11
No worries; thanks again! I edited "blacklist-bcm43.conf" and can now switch between wireless and Ethernet. I have learned a lot from this thread and am now headed out to discover what modprobe, et cetera, are all about. One concern, however: The first line in "blacklist-bcm43.conf" is a comment stating:
```

#Warning: This file is generated by bcmwl. All changes to this file will be lost.

```
Apparently bcmwl does not run during boot-up, Having seen the warning, I went back into the file after re-booting and the changes were not lost. When might bcmwl regenerate the file and un-blacklist ssb and b44?

---

### Post by wildmanne39 on 2016-09-11
If you run this command again the changes will be lost:
```
 sudo apt-get install bcmwl-kernel-source
```
it automatically blacklists b44 and ssb.

You should not have ran that command since you turned off your wireless device in the bios, plus it may not even use that driver anyway it might use the b43.

That command has nothing to do with your wireless usb device working it must work out of the box.

---

### Post by 78plus on 2016-09-11
Thanks again. I shall be so guided.

---


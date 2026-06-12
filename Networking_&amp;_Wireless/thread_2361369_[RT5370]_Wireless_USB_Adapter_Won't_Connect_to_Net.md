---
title: "[RT5370] Wireless USB Adapter Won't Connect to Networks"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by lucas7bm on 2017-05-15
Hello, guys!
Well, I'm having this problem since the version 16 of ubuntu, I guess (maybe since the latest version of network-manager, I don't know).
Until last week, I was using Elementary OS Loki on my computer, but this weekend I've decided to install Ubuntu Budgie (**really cool flavour, until now! I recommend**)

Well, the problem that I'm having now is the same that I've had on Elementary. I didn't use elementary for some time and I only discovered the problem a few days before this weekend.

Here it is: my adaptater (Link One L1-AW1Un) always worked fine in both Linux and Windows - in the older versions of ubuntu and other distros that I've tried.
But now, and I don't know why, it's not working anymore *just on linux*.
I'm able to see the networks normally, and even try to connect to them (it asks for a password and so on), but then it just takes a long time before it shows "You are disconnected".
I'm using a cable connection right now to post this thread.

I've tried to put rt2800usb driver into modprobe's blacklist and then compile the Ralink RT5370's driver manually, but I just can't do it (some compile errors that I haven't found out there yet).
So, I've decided to get back to the start and just ask if someone had the same problem and could give me a little light.

I used @varunendra's Wireless Script, so it can maybe help you all with helping me :(
And I really appreciate any help you can provide.

**This is the Wireless Script output:**

```

########## wireless info START ##########


Report from: 15 May 2017 18:46 -03 -0300


Booted last: 15 May 2017 00:00 -03 -0300


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


##### kernel ############################


Linux 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Budgie Desktop


##### lspci #############################


01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo QCA8172 Fast Ethernet [17aa:3804]
    Kernel driver in use: alx


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 174f:147b Syntek 
Bus 003 Device 002: ID 17ef:604d Lenovo 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
mac80211              782336  3 rt2800lib,rt2x00lib,rt2x00usb
cfg80211              602112  2 rt2x00lib,mac80211
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    16384  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.107  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::f59e:1b67:f059:d9a0  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 9870  bytes 7829660 (7.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9648  bytes 1509106 (1.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 340  bytes 24984 (24.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 340  bytes 24984 (24.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlxc83a35c4a272: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp1s0    no wireless extensions.


lo        no wireless extensions.


wlxc83a35c4a272  IEEE 802.11  ESSID:off/any  
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


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       954     1  0 18:40 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8172 Fast Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
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
GENERAL.CONNECTION:                     Conexão cabeada 1
GENERAL.CON-UUID:                       7151ead5-54e1-3c6a-86cd-24dbbbcad3e0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7151ead5-54e1-3c6a-86cd-24dbbbcad3e0 | Conexão cabeada 1
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
DHCP4.OPTION[10]:                       expiry = 1494891649
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
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::f59e:1b67:f059:d9a0/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlxc83a35c4a272
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.10.0-20-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/net/wlxc83a35c4a272
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c3c8553b-2a7f-469b-8193-55baf49c5019 | Rep. U.R.C.A


SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Rep. U.R.C.A          <MAC 'Rep. U.R.C.A' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Rep. U.R.C.A. T       <MAC 'Rep. U.R.C.A. T' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
Oi WiFi Fon           <MAC 'Oi WiFi Fon' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  --         no        
Celina                <MAC 'Celina' [AN4]>  Infra  7     2442 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        
Rede Alfenas EdTFBsD  <MAC 'Rede Alfenas EdTFBsD' [AN5]>  Infra  2     2417 MHz  2 Mbit/s   15      &#9602;___  --         no        
Natane_1              <MAC 'Natane_1' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        


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


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Rep. U.R.C.A]] (600 root)
[connection] id=Rep. U.R.C.A | type=wifi | permissions=user:lucas:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Rep. U.R.C.A
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


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


##### iwlist channels ###################


enp1s0    no frequency information.


lo        no frequency information.


wlxc83a35c4a272  14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz


##### iwlist scan #######################


enp1s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlxc83a35c4a272  Scan completed :
          Cell 01 - Address: <MAC 'Rep. U.R.C.A' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Rep. U.R.C.A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dfe13ad424
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Rep. U.R.C.A. T' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Rep. U.R.C.A. T"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a767aae40
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Natane_1' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Natane_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001455f3d3a2
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.10.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9D2505A653507F57F0E0D31
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.10.0-20-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.10.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FCC1D8BB13093044D2B993D
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-20-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-20-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-20-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6FCDB39CB1DCCA0C9A450B2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-20-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0ADFC23D0B6BCD6916160E7
depends:        
intree:         Y
vermagic:       4.10.0-20-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
nohwcrypt: N


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


[   22.224130] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   22.252354] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   22.455091] rt2800usb 1-1.2:1.0 wlxc83a35c4a272: renamed from wlan0
[   26.872204] IPv6: ADDRCONF(NETDEV_UP): wlxc83a35c4a272: link is not ready
[   26.872238] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   26.935744] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[   27.199597] IPv6: ADDRCONF(NETDEV_UP): wlxc83a35c4a272: link is not ready (repeated 4 times)
[   53.963215] wlxc83a35c4a272: authenticate with <MAC 'Rep. U.R.C.A' [AC1]>
[   53.991691] wlxc83a35c4a272: send auth to <MAC 'Rep. U.R.C.A' [AC1]> (try 1/3)
[   54.095053] wlxc83a35c4a272: send auth to <MAC 'Rep. U.R.C.A' [AC1]> (try 2/3)
[   54.097040] wlxc83a35c4a272: authenticated
[   60.363421] wlxc83a35c4a272: authenticate with <MAC 'Rep. U.R.C.A' [AC1]>
[   60.415056] wlxc83a35c4a272: send auth to <MAC 'Rep. U.R.C.A' [AC1]> (try 1/3)
[   60.417319] wlxc83a35c4a272: authenticated
[   67.273697] wlxc83a35c4a272: authenticate with <MAC 'Rep. U.R.C.A' [AC1]>
[   67.325070] wlxc83a35c4a272: send auth to <MAC 'Rep. U.R.C.A' [AC1]> (try 1/3)
[   67.327074] wlxc83a35c4a272: authenticated
[   74.651023] wlxc83a35c4a272: authenticate with <MAC 'Rep. U.R.C.A' [AC1]>
[   74.698313] wlxc83a35c4a272: send auth to <MAC 'Rep. U.R.C.A' [AC1]> (try 1/3)
[   74.700308] wlxc83a35c4a272: authenticated
[   78.882672] IPv6: ADDRCONF(NETDEV_UP): wlxc83a35c4a272: link is not ready (repeated 2 times)


########## wireless info END ############

```

---

### Post by jeremy31 on 2017-05-16
You are probably having issues because of the MAC randomization being enabled in Network Manager in 17.04, see [https://askubuntu.com/a/905019/300665](https://askubuntu.com/a/905019/300665)

---

### Post by lucas7bm on 2017-05-16
Wow, I really didn't thought this would work.
Actually, it was the first thing that I've tried, when I was using the Live CD before installing.
I don't know what could change and make it work now, but I'm glad something did! Haha
Sorry for posting about something simple like this. Thank you, Jeremy!

---

### Post by uRock on 2017-08-26
Thanks jeremy31. I knew it'd be a simple conf edit, but had no clue ubuntu was doing the MAC randomization.

Just in case something happens to the information in the Ask Ubuntu page, here's what was done;

In terminal run```
gksu gedit /etc/NetworkManager/NetworkManager.conf
```then add the following information to the file,```
[device]
wifi.scan-rand-mac-address=no
``` and save it. Then run this command to restart Network Manager using,```
sudo service network-manager restart
```

---


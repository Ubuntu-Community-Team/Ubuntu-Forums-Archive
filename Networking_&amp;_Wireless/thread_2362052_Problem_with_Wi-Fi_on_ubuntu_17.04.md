---
title: "Problem with Wi-Fi on ubuntu 17.04"
date: 2017-05-23
forum: Networking &amp; Wireless
---

### Post by peeeoolo on 2017-05-23
Hello I can't connect to internet with the wi-fi but the ethernet works just fine.

I ran this script that I found online with all the info you may need 

Thank you for the help already 

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info




```
########## wireless info START ##########


Report from: 23 May 2017 19:52 CEST +0200


Booted last: 23 May 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


##### kernel ############################


Linux 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2211]
    Kernel driver in use: r8169


09:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName:  
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 001 Device 003: ID 064e:9320 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes


##### lsmod #############################


hp_wmi                 16384  0
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              602112  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
sparse_keymap          16384  2 intel_hid,hp_wmi
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::c3dc:7720:9692:f52c  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1914  bytes 1689938 (1.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1851  bytes 327243 (327.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 532  bytes 81995 (81.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 532  bytes 81995 (81.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


wlo1      IEEE 802.11  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thro: ff   Fragment thro: off
          Power Management: off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       876     1  0 19:48 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6fbea5a9-2b12-3b5c-8d5d-4224871e482e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6fbea5a9-2b12-3b5c-8d5d-4224871e482e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             4.4.8.8
IP4.DOMAIN[1]:                          homenet.telecomitalia.it
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        vendor_unknown_3561 = 4:6:30:30:31:33:43:38:5:d:33:33:31:30:32:49:30:33:39:31:33:37:36:6:d:41:47:20:42:61:73:69:63:20:57:69:46:69
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       host_name = paolo-HP-250-G3-Notebook-PC-002
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       expiry = 1495583376
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       next_server = 192.168.1.1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = homenet.telecomitalia.it
DHCP4.OPTION[20]:                       ip_address = 192.168.1.6
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       routers = 192.168.1.1
DHCP4.OPTION[26]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_lease_time = 21600
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::c3dc:7720:9692:f52c/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.10.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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
wifi.scan-rand-mac-address=0


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HTC Portable Hotspot EF3E]] (600 root)
[connection] id=HTC Portable Hotspot EF3E | type=wifi | permissions=user: Paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HTC Portable Hotspot EF3E
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ASL2 WIFI FREE]] (600 root)
[connection] id=ASL2 WIFI FREE | type=wifi | permissions=user: Paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ASL2 WIFI FREE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Telecom-89638141]] (600 root)
[connection] id=Telecom-89638141 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Telecom-89638141
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


global
country IT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp8s0    no frequency information.


wlo1      13 channels in total; available frequencies :
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp8s0    Interface doesn't support scanning.


wlo1      Interface doesn't support scanning : Network is down


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     CCF6F7B3B8BA388CA3C00E8
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     91B04FCFBB684DAA51C0B02
depends:        rt2x00mmio,rt2800lib,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     966397E660CE70DBEF65135
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     AB545181182AC142E08EA5F
depends:        rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     25AD08C8BBFD528CC9B45E2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
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


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   13.237638] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   13.245690] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   15.504158] rt2800pci 0000:09:00.0 wlo1: renamed from wlan0
[   38.547426] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready


########## wireless info END ############
```

---

### Post by howefield on 2017-05-23
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by wildmanne39 on 2017-05-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the en

---

### Post by wildmanne39 on 2017-05-23
You have a typo in the file where you added:
```
 wifi.scan-rand-mac-[COLOR="#FF0000"]adress[/COLOR]=0
```
should be address=0

Then do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Thanks

---

### Post by peeeoolo on 2017-05-23
```


options rt2800pci nohwcrypt=y


rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211


insmod /lib/modules/4.10.0-21-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko nohwcrypt=y 



```


Here you go

---

### Post by wildmanne39 on 2017-05-23
That looks good, you did run the first command with the echo at the beginning right?

Did you correct the typo in that file?

---

### Post by peeeoolo on 2017-05-23
Yep i corrected it and rebooted the system but it doesn't work

---

### Post by wildmanne39 on 2017-05-23
Please run the wireless script again so we can see if the changes stuck.
Thanks

---

### Post by peeeoolo on 2017-05-23
```

########## wireless info START ##########


Report from: 23 May 2017 21:02 CEST +0200


Booted last: 23 May 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty


##### kernel ############################


Linux 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################




08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2211]
	Kernel driver in use: r8169


09:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName:  
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 001 Device 003: ID 064e:9320 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
hp_wmi                 16384  0
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              602112  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
sparse_keymap          16384  2 intel_hid,hp_wmi
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::c3dc:7720:9692:f52c  prefixlen 64  scopeid 0x20<link>
        ether 34:64:a9:79:ee:ab  txqueuelen 1000  (Ethernet)
        RX packets 109  bytes 61647 (61.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 168  bytes 20293 (20.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 455  bytes 83124 (83.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 455  bytes 83124 (83.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 38:b1:db:4e:b1:17  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################




nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       856     1  0 20:59 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         34:64:A9:79:EE:AB
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6fbea5a9-2b12-3b5c-8d5d-4224871e482e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6fbea5a9-2b12-3b5c-8d5d-4224871e482e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             4.4.8.8
IP4.DOMAIN[1]:                          homenet.telecomitalia.it
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        vendor_unknown_3561 = 4:6:30:30:31:33:43:38:5:d:33:33:31:30:32:49:30:33:39:31:33:37:36:6:d:41:47:20:42:61:73:69:63:20:57:69:46:69
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       host_name = paolo-HP-250-G3-Notebook-PC-002
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       expiry = 1495587721
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       next_server = 192.168.1.1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = homenet.telecomitalia.it
DHCP4.OPTION[20]:                       ip_address = 192.168.1.6
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       routers = 192.168.1.1
DHCP4.OPTION[26]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_lease_time = 21600
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::c3dc:7720:9692:f52c/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.10.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         38:B1:DB:4E:B1:17
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 




SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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
wifi.scan-rand-mac-address=0


##### NetworkManager profiles ###########


```

---

### Post by wildmanne39 on 2017-05-23
Please let us see the rest of the file, I think you may have a hardblock, make sure your switch is turn on for wifi or it may be a key combination.  I will be leaving soon for a few hours.

---

### Post by peeeoolo on 2017-05-23
Yeah sorry this should be it ```



########## wireless info START ##########


Report from: 23 May 2017 21:21 CEST +0200


Booted last: 23 May 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty


##### kernel ############################


Linux 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2211]
	Kernel driver in use: r8169


09:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName:  
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 001 Device 003: ID 064e:9320 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              602112  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
hp_wmi                 16384  0
sparse_keymap          16384  2 intel_hid,hp_wmi
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::c3dc:7720:9692:f52c  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 135489  bytes 197459825 (197.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 71729  bytes 6027875 (6.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1007  bytes 186212 (186.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1007  bytes 186212 (186.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       856     1  0 20:59 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6fbea5a9-2b12-3b5c-8d5d-4224871e482e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6fbea5a9-2b12-3b5c-8d5d-4224871e482e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             4.4.8.8
IP4.DOMAIN[1]:                          homenet.telecomitalia.it
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        vendor_unknown_3561 = 4:6:30:30:31:33:43:38:5:d:33:33:31:30:32:49:30:33:39:31:33:37:36:6:d:41:47:20:42:61:73:69:63:20:57:69:46:69
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       host_name = paolo-HP-250-G3-Notebook-PC-002
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       expiry = 1495587803
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       next_server = 192.168.1.1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = homenet.telecomitalia.it
DHCP4.OPTION[20]:                       ip_address = 192.168.1.6
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       routers = 192.168.1.1
DHCP4.OPTION[26]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_lease_time = 21600
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::c3dc:7720:9692:f52c/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.10.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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
wifi.scan-rand-mac-address=0


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HTC Portable Hotspot EF3E]] (600 root)
[connection] id=HTC Portable Hotspot EF3E | type=wifi | permissions=user:paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HTC Portable Hotspot EF3E
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ASL2 WIFI FREE]] (600 root)
[connection] id=ASL2 WIFI FREE | type=wifi | permissions=user:paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ASL2 WIFI FREE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Telecom-89638141]] (600 root)
[connection] id=Telecom-89638141 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Telecom-89638141
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


global
country IT: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp8s0    no frequency information.


wlo1      13 channels in total; available frequencies :
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


##### iwlist scan #######################


wlo1      Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


enp8s0    Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CCF6F7B3B8BA388CA3C00E8
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     91B04FCFBB684DAA51C0B02
depends:        rt2x00mmio,rt2800lib,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     966397E660CE70DBEF65135
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AB545181182AC142E08EA5F
depends:        rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     25AD08C8BBFD528CC9B45E2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: Y


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


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=y


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   30.900487] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   30.908527] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   30.914645] rt2800pci 0000:09:00.0 wlo1: renamed from wlan0
[   39.971132] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  333.297640] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[  333.305632] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[  333.315667] rt2800pci 0000:09:00.0 wlo1: renamed from wlan0
[  333.354492] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready


########## wireless info END ############

```

---

### Post by jeremy31 on 2017-05-23
Since wildmanne39 is still absent, I would suggest trying
```
echo "blacklist hp-wmi" | sudo tee /etc/modprobe.d/hp-wmi.conf
```
Reboot

---

### Post by wildmanne39 on 2017-05-24
Hopefully jeremy31's command will take care of the hardblock, when you went into network manger and changed the settings to match the screenshots, on your wired connection and possibly your wifi also you typed 4.4.8.8 and it should be 8.8.4.4 for the second dns server.

Thanks jeremy, it took longer to get back then I thought it would.

---

### Post by peeeoolo on 2017-05-24
I changed the DNS on the wired connection but on the wirless one were fine. I run the commad mentioned before and rebooted, thins don't work anyway and here there is the result of the script ```

########## wireless info START ##########


Report from: 24 May 2017 14:50 CEST +0200


Booted last: 24 May 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty


##### kernel ############################


Linux 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2211]
	Kernel driver in use: r8169


09:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName:  
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 001 Device 003: ID 064e:9320 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              602112  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::c3dc:7720:9692:f52c  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2376  bytes 1853961 (1.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2441  bytes 466673 (466.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 832  bytes 121082 (121.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 832  bytes 121082 (121.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp8s0    no wireless extensions.


lo        no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       850     1  0 14:45 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6fbea5a9-2b12-3b5c-8d5d-4224871e482e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6fbea5a9-2b12-3b5c-8d5d-4224871e482e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             4.4.8.8
IP4.DOMAIN[1]:                          homenet.telecomitalia.it
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        vendor_unknown_3561 = 4:6:30:30:31:33:43:38:5:d:33:33:31:30:32:49:30:33:39:31:33:37:36:6:d:41:47:20:42:61:73:69:63:20:57:69:46:69
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       host_name = paolo-HP-250-G3-Notebook-PC-002
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       expiry = 1495651571
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       next_server = 192.168.1.1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = homenet.telecomitalia.it
DHCP4.OPTION[20]:                       ip_address = 192.168.1.6
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       routers = 192.168.1.1
DHCP4.OPTION[26]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_lease_time = 21600
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::c3dc:7720:9692:f52c/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.10.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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
wifi.scan-rand-mac-address=0


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HTC Portable Hotspot EF3E]] (600 root)
[connection] id=HTC Portable Hotspot EF3E | type=wifi | permissions=user:paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HTC Portable Hotspot EF3E
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ASL2 WIFI FREE]] (600 root)
[connection] id=ASL2 WIFI FREE | type=wifi | permissions=user:paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ASL2 WIFI FREE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Telecom-89638141]] (600 root)
[connection] id=Telecom-89638141 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Telecom-89638141
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


global
country IT: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp8s0    no frequency information.


lo        no frequency information.


wlo1      13 channels in total; available frequencies :
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


##### iwlist scan #######################


enp8s0    Interface doesn't support scanning.


wlo1      Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CCF6F7B3B8BA388CA3C00E8
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     91B04FCFBB684DAA51C0B02
depends:        rt2x00mmio,rt2800lib,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     966397E660CE70DBEF65135
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AB545181182AC142E08EA5F
depends:        rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     25AD08C8BBFD528CC9B45E2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: Y


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


[/etc/modprobe.d/hp-wmi.conf]
blacklist hp-wmi


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=y


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   30.590672] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   30.598717] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   30.725644] rt2800pci 0000:09:00.0 wlo1: renamed from wlan0
[   40.371265] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready


########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-05-24
Have you tried turning the wifi on with the switch? or key combination? it is hardblocked and it usually means the switch is off.

---

### Post by peeeoolo on 2017-05-24
It was indeed the switch it just didn't show the airplane icon... and now I feel stupid

Thank you for your time :)

---

### Post by peeeoolo on 2017-05-24
Ok nope it wasn't that. I rebooted and it went back to not working I've tried to put the switch on and off a dozen times but nothing

---

### Post by wildmanne39 on 2017-05-24
It may not be the same issue, please run the wireless script, and try to make sure it is turned on when you do other wise we can not tell what is is wrong.
Thanks

---

### Post by peeeoolo on 2017-05-24
Here you go I've tried to switch it on but I've no idea how this works, I've also tried to reset the BIOS options to default because it was suggested in a thread about hard switch that gave problem. this is the new output```




########## wireless info START ##########


Report from: 24 May 2017 22:21 CEST +0200


Booted last: 24 May 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty


##### kernel ############################


Linux 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2211]
	Kernel driver in use: r8169


09:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName:  
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 001 Device 003: ID 064e:9320 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              602112  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::c3dc:7720:9692:f52c  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 24870  bytes 30259044 (30.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16268  bytes 2166278 (2.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2027  bytes 443923 (443.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2027  bytes 443923 (443.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp8s0    no wireless extensions.


lo        no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       825     1  0 21:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6fbea5a9-2b12-3b5c-8d5d-4224871e482e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6fbea5a9-2b12-3b5c-8d5d-4224871e482e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             8.8.4.4
IP4.DOMAIN[1]:                          homenet.telecomitalia.it
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        vendor_unknown_3561 = 4:6:30:30:31:33:43:38:5:d:33:33:31:30:32:49:30:33:39:31:33:37:36:6:d:41:47:20:42:61:73:69:63:20:57:69:46:69
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       host_name = paolo-HP-250-G3-Notebook-PC-002
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       expiry = 1495678440
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       next_server = 192.168.1.1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = homenet.telecomitalia.it
DHCP4.OPTION[20]:                       ip_address = 192.168.1.6
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       routers = 192.168.1.1
DHCP4.OPTION[26]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_lease_time = 21600
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::c3dc:7720:9692:f52c/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.10.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/wlo1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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
wifi.scan-rand-mac-address=0


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HTC Portable Hotspot EF3E]] (600 root)
[connection] id=HTC Portable Hotspot EF3E | type=wifi | permissions=user:paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HTC Portable Hotspot EF3E
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ASL2 WIFI FREE]] (600 root)
[connection] id=ASL2 WIFI FREE | type=wifi | permissions=user:paolo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ASL2 WIFI FREE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Telecom-89638141]] (600 root)
[connection] id=Telecom-89638141 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Telecom-89638141
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


global
country IT: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp8s0    no frequency information.


lo        no frequency information.


wlo1      13 channels in total; available frequencies :
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


##### iwlist scan #######################


wlo1      Interface doesn't support scanning : Network is down


enp8s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CCF6F7B3B8BA388CA3C00E8
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     91B04FCFBB684DAA51C0B02
depends:        rt2x00mmio,rt2800lib,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00pci]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     966397E660CE70DBEF65135
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00mmio]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AB545181182AC142E08EA5F
depends:        rt2x00lib
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-21-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     25AD08C8BBFD528CC9B45E2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-21-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: Y


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


[/etc/modprobe.d/hp-wmi.conf]
blacklist hp-wmi


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=y


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   27.092390] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   27.100428] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   27.359910] rt2800pci 0000:09:00.0 wlo1: renamed from wlan0
[   34.661313] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready


########## wireless info END ############

```

---

### Post by wildmanne39 on 2017-05-24
Right now it is hardblocked, please do:
```
 sudo rm /etc/modprobe.d/hp-wmi.conf

```
Reboot the computer then if wifi does not come on push the key or switch one time only to turn it on.

---

### Post by peeeoolo on 2017-05-25
Yesterday I mounted an ssd in my laptop and I installed ubuntu 16.04 on the ssd. At first after the installation everything was working fine but now after a couple of reboots It can't connect again... I post the picture of the wifi settings of the new system to give you an idea

[http://i65.tinypic.com/6enl94.jpg](http://i65.tinypic.com/6enl94.jpg)

---

### Post by wildmanne39 on 2017-05-25
The image gives me no information, what we need to see is the information from the wireless script, you did this new install instead of doing what I asked in my last post?

---

### Post by peeeoolo on 2017-05-25
Yes I did but it didn't help

---


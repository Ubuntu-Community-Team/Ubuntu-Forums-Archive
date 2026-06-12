---
title: "Failing to create connectivity between ubuntu and wifi-ethernet"
date: 2017-10-01
forum: Networking &amp; Wireless
---

### Post by frequencyg on 2017-10-01
Hello,
I just installed 17.04 after taking a loong break since 9.04 version. I had the same problems with kali linux but managed to solve them.I got a 2800rt usb card attached to the vbox from the device list but i still can not search for wifi. It was bridged and i could connect online like using a ethernet cable.But after a reboot it wont to it either.I got it updated as well.If anyone can help it would be great. Also i run a cmmand to show me the usbs connected to the machine and i could see my usb card!

---

### Post by wildmanne39 on 2017-10-01
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by frequencyg on 2017-10-02
Hello,
there you go  [http://paste.ubuntu.com/25659953/](http://paste.ubuntu.com/25659953/)

---

### Post by wildmanne39 on 2017-10-02
The usb card is not showing up in the file you posted, at the time of running the script the device was not captured by the guest, please make sure the device is captured and run the wireless script again and make sure your ethernet connection is not connected.

Thanks

---

### Post by frequencyg on 2017-10-06
How is gonna upload when i do not have any internet access on the machine whatsoever with the wifi card?

---

### Post by wildmanne39 on 2017-10-06
You already have the script on your computer just run this command:
```
./wireless-info
```

---

### Post by frequencyg on 2017-10-07
```
########## wireless info START ##########


Report from: 07 Oct 2017 13:04 EEST +0300


Booted last: 07 Oct 2017 00:00 EEST +0300


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


##### kernel ############################


Linux 4.10.0-35-generic #39-Ubuntu SMP Wed Sep 13 07:46:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
    Kernel driver in use: e1000


##### lsusb #############################


Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s3: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 42  bytes 3172 (3.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 42  bytes 3172 (3.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx000da31c1131: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp0s3    no wireless extensions.


lo        no wireless extensions.


wlx000da31c1131  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2483     1  0 13:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx000da31c1131
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.10.0-35-generic
GENERAL.FIRMWARE-VERSION:               0.36
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:06.0/usb1/1-2/1-2:1.0/net/wlx000da31c1131
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


GENERAL.DEVICE:                         enp0s3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82540EM Gigabit Ethernet Controller (PRO/1000 MT Desktop Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 7.3.21-k8-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.0/net/enp0s3
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
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BMW MOTOSPORT
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Athens (based on set time zone)


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


enp0s3    no frequency information.


lo        no frequency information.


wlx000da31c1131  14 channels in total; available frequencies :
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


wlx000da31c1131  Interface doesn't support scanning : Device or resource busy


enp0s3    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     9D2505A653507F57F0E0D31
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     B8A74E3557508C7071429BD
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
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


rt2800usb


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


[  105.346284] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  106.252997] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[  106.322888] rt2800usb 1-2:1.0 wlx000da31c1131: renamed from wlan0
[  106.339698] IPv6: ADDRCONF(NETDEV_UP): wlx000da31c1131: link is not ready
[  106.339722] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  106.398323] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  112.381841] IPv6: ADDRCONF(NETDEV_UP): wlx000da31c1131: link is not ready (repeated 5 times)


########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-10-07
Please do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb 
```
Then post the output of:
```
dpkg -l | grep linux-image
```

---

### Post by wildmanne39 on 2017-10-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by frequencyg on 2017-10-11
```

#[COLOR=#000000][FONT=&amp]########## wireless info START ##########[/FONT][/COLOR]

Report from: 07 Oct 2017 13:04 EEST +0300


Booted last: 07 Oct 2017 00:00 EEST +0300


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


##### kernel ############################


Linux 4.10.0-35-generic #39-Ubuntu SMP Wed Sep 13 07:46:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
    Kernel driver in use: e1000


##### lsusb #############################


Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s3: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 42  bytes 3172 (3.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 42  bytes 3172 (3.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx000da31c1131: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp0s3    no wireless extensions.


lo        no wireless extensions.


wlx000da31c1131  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2483     1  0 13:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx000da31c1131
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.10.0-35-generic
GENERAL.FIRMWARE-VERSION:               0.36
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:06.0/usb1/1-2/1-2:1.0/net/wlx000da31c1131
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


GENERAL.DEVICE:                         enp0s3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82540EM Gigabit Ethernet Controller (PRO/1000 MT Desktop Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 7.3.21-k8-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.0/net/enp0s3
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
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BMW MOTOSPORT
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Athens (based on set time zone)


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


enp0s3    no frequency information.


lo        no frequency information.


wlx000da31c1131  14 channels in total; available frequencies :
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


wlx000da31c1131  Interface doesn't support scanning : Device or resource busy


enp0s3    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
srcversion:     9D2505A653507F57F0E0D31
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
srcversion:     B8A74E3557508C7071429BD
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 


[rt2800lib]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/"), Bartlomiej Zolnierkiewicz
srcversion:     D54345347C7289C8F69F4AC
depends:        mac80211,rt2x00lib
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 


[rt2x00lib]
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
srcversion:     297D0E7AF19B14F6E138EC2
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
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


rt2800usb


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


[  105.346284] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  106.252997] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[  106.322888] rt2800usb 1-2:1.0 wlx000da31c1131: renamed from wlan0
[  106.339698] IPv6: ADDRCONF(NETDEV_UP): wlx000da31c1131: link is not ready
[  106.339722] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  106.398323] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  112.381841] IPv6: ADDRCONF(NETDEV_UP): wlx000da31c1131: link is not ready (repeated 5 times)


########## wireless info END ############


```

---


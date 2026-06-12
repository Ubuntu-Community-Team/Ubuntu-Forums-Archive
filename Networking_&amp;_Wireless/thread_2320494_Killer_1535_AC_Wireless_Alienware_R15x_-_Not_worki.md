---
title: "Killer 1535 AC Wireless Alienware R15x - Not working - Ubuntu 15.10"
date: 2016-04-14
forum: Networking &amp; Wireless
---

### Post by bobbymarshall on 2016-04-14
My Killer 1535 AC Wireless card is showing, "Device not Ready." I have tried every fix from other threads and nothing seems to work. I'll post whatever info is necessary to help. Thank you!

---

### Post by chili555 on 2016-04-14
Please check here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by bobbymarshall on 2016-04-14
Sorry about that. Here you go.
```

########## wireless info START ##########

Report from: 14 Apr 2016 17:09 EDT -0400

Booted last: 14 Apr 2016 00:00 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-35-generic #40-Ubuntu SMP Tue Mar 15 22:15:45 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0a1] (rev 10)
    Subsystem: Device [0707:2400]
    Kernel driver in use: alx

3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1535]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 003: ID 187c:0528 Alienware Corporation 
Bus 001 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             40960  0
ath10k_core           278528  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              745472  1 ath10k_core
dell_wmi               16384  0
cfg80211              557056  3 ath,mac80211,ath10k_core
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau
video                  40960  3 i915,dell_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp59s0   Link encap:Ethernet  HWaddr <MAC 'enp59s0' [IF]>  
          inet addr:192.168.1.236  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp59s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:134846787 (134.8 MB)  TX bytes:3252121 (3.2 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

enp59s0   no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp59s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp59s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp59s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       646     1  0 16:58 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp59s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Sunrise Point-H PCI Express Root Port
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp59s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:3b:00.0/net/enp59s0
GENERAL.IP-IFACE:                       enp59s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f48f51c0-291a-4bde-ad5b-910f418e9644
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f48f51c0-291a-4bde-ad5b-910f418e9644 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.236/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.1.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_host_name = 1
DHCP4.OPTION[8]:                        host_name = bobby-Alienware-15-R2
DHCP4.OPTION[9]:                        expiry = 1460768329
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       next_server = 192.168.1.1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       ip_address = 192.168.1.236
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[21]:                       dhcp_lease_time = 86400
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_domain_name_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp59s0' [IF]>/64
IP6.GATEWAY:                            

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

##### iw reg get ########################

Region: America/Indiana/Indianapolis (based on set time zone)

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

enp59s0   no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp59s0   Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     5EB8A069F322875ED643860
depends:        ath10k_core
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     1374D8F96EF13D559461E8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)

[ath]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
debug_mask: 0
skip_otp: N
uart_print: N

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    5.834090] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[    5.834916] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    6.071264] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[    6.071276] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-pci-168c:003e:1a56:1535.bin failed with error -2
[    6.071278] ath10k_pci 0000:3c:00.0: failed to load spec board file, falling back to generic: -2
[    6.071283] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board.bin failed with error -2
[    6.071284] ath10k_pci 0000:3c:00.0: failed to fetch generic board data: -2
[    6.071286] ath10k_pci 0000:3c:00.0: failed to fetch board file: -2
[    6.071287] ath10k_pci 0000:3c:00.0: could not fetch firmware files (-2)
[    6.071288] ath10k_pci 0000:3c:00.0: could not probe fw (-2)
[   14.321058] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready (repeated 2 times)
[   14.324056] alx 0000:3b:00.0 enp59s0: NIC Up: 100 Mbps Full
[   14.324281] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready

########## wireless info END ############

```

EDIT: I removed the Soft and Hard Block after posting this.
EDIT2: After apt-get dist-upgrade and Rebooting My Ethernet no longer works. O.o

---

### Post by chili555 on 2016-04-14
> Direct firmware load for ath10k/QCA6174/hw3.0/board.bin failed with error -2You can find the firmware here: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb)

Download the file to any convenient place, Desktop, for example and then:```
cd ~/Desktop
sudo -i
dpkg -i linux*.deb
modprobe -r ath10k_pci
modprobe -r ath10k_core
echo "options ath10k_core skip_otp=y" > /etc/modprobe.d/ath10k.conf
modprobe ath10k_pci
exit

```It may take a reboot.

Any improvement?

---

### Post by bobbymarshall on 2016-04-14
No change. Here's the Wireless-info again. after doing what you said.
[ATTACH]268385[/ATTACH]

---

### Post by chili555 on 2016-04-14
Oh, my! There is a big change!> [   45.797721] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   48.797275] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   57.079876] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   60.079422] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   68.362128] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   71.361610] ath10k_pci 0000:3c:00.0: could not suspend target (-11)Yikes!

Will you try to capture the log messages prior to timestamp 48.797275 so we can hopefully see what's happening?```
dmesg | grep ath | less
```Try to see what firmware loads and give us those messages.

I suspect the firmware is not correct for the hardware. I'll be looking for a better source now.

At least the ethernet is back! :) :)

---

### Post by bobbymarshall on 2016-04-14
Thanks so much for helping me. :D

```

[    6.882410] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[    6.883411] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 re
set_mode 0
[    7.084200] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-
0000:3c:00.0.bin failed with error -2
[    7.203440] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/
hw3.0/board-pci-168c:003e:1a56:1535.bin failed with error -2
[    7.203444] ath10k_pci 0000:3c:00.0: failed to load spec board file, falling 
back to generic: -2
[    7.358569] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/
hw3.0/firmware-5.bin failed with error -2
[    7.358575] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QC
A6174/hw3.0/firmware-5.bin': -2
[    9.569567] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff, 1
68c:003e:1a56:1535 fallback) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 htt 3.26 wmi
 4 cal otp max_sta 32
[    9.569571] ath10k_pci 0000:3c:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmo
de 0
[   10.567228] ath10k_pci 0000:3c:00.0: suspend timed out - target pause event n
ever came
[   13.634302] ath: EEPROM regdomain: 0x69
[   13.634304] ath: EEPROM indicates we should expect a direct regpair map
[   13.634305] ath: Country alpha2 being used: 00
[   13.634306] ath: Regpair used: 0x69
[   13.863201] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   23.053228] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   26.052891] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   34.491368] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   37.490902] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   45.773666] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   48.773063] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   57.055742] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   60.055405] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   68.337998] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   71.337522] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   79.628153] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   82.627646] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   90.914493] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[   93.913916] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  102.200648] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  105.200095] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  113.486722] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  116.486378] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  125.064952] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  128.064455] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  136.347176] ath10k_pci 0000:3c:00.0: failed to enable ani by default: -11
[  139.346671] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  147.629430] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  150.628796] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  158.903141] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  161.902520] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  170.189023] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  173.188413] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  181.470933] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  184.470422] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  192.757040] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  195.756634] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  204.039249] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  207.038725] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  215.321435] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  218.320844] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  226.603030] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  229.602508] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  237.884932] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  240.884312] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  249.166816] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  252.166325] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  260.448658] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  263.448261] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  271.730699] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  274.730151] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  283.012865] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  286.012234] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  294.294881] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  297.294410] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  305.576877] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  308.576409] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  316.859035] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  319.858491] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  328.141220] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  331.140604] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  339.423344] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  342.422723] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  350.709407] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  353.708952] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  361.991494] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  364.991066] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
(END)


```

---

### Post by bobbymarshall on 2016-04-14
Chili555, thank you for your support. I actually have fixed it following this guide. [http://www.killernetworking.com/support/knowledge-base/17-linux](http://www.killernetworking.com/support/knowledge-base/17-linux). I installed the new board.bin and firmware-4.bin and it works! I don't know if I'm supposed to mark this SOLVED or if a moderator has to.

---

### Post by slickymaster on 2016-04-14
> **bobbymarshall said:**
> Chili555, thank you for your support. I actually have fixed it following this guide. [http://www.killernetworking.com/support/knowledge-base/17-linux](http://www.killernetworking.com/support/knowledge-base/17-linux). I installed the new board.bin and firmware-4.bin and it works! I don't know if I'm supposed to mark this SOLVED or if a moderator has to.

Yes, please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by chili555 on 2016-04-14
Awesome! Glad it's working.

Have fun!

---

### Post by bobbymarshall on 2016-04-14
Thanks!

---


---
title: "Qualcomm Atheros QCA6174 always has internet speed 1Mb/s, Ubuntu 16.04, Dell XPS-13"
date: 2017-05-03
forum: Networking &amp; Wireless
---

### Post by strange1 on 2017-05-03
I recently noticed that every wireless network I connect to has a speed of 1Mb/s.  To verify that this issue was not with any of the wireless networks, I checked the connection speed for one of them from a friend's laptop and got 86Mb/s (while my laptop said 1Mb/s).

After following the instructions on the thread "Before Posting in Networking and Wireless" I produced the following wireless-info document into Pastebin:

[http://paste.ubuntu.com/24506106/](http://paste.ubuntu.com/24506106/)

Due to my lack of knowledge concerning Ubuntu (I am about 2 weeks into my first install) it is diifficult to discern what exactly the problem is from this document; at this time my best guess is an issue with missing firmware related to the following messages I found within wireless-info document produced on my laptop:

Direct firmware load for ath10k/pre-cal-pci-0000:3a:00.0.bin failed with error -2
Direct firmware load for ath10k/cal-pci-0000:3a:00.0.bin failed with error -2
Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2

Is this missing firmware the problem?  Or is there something else going on?

---

### Post by jeremy31 on 2017-05-03
The wireless script results are not complete but try
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Reboot and see if the speed is better.  The firmware errors are normal as those files don't exist yet

---

### Post by strange1 on 2017-05-03
Thank you for the response!

I entered in the command you gave, but unfortunately am still having the same issue.  I re-ran the wireless script and show the relevant text here (as uploading it to Pastebin results in an incomplete file):

```
########## wireless info START ##########


Report from: 03 May 2017 18:26 EDT -0400


Booted last: 03 May 2017 00:00 EDT -0400


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.8.0-51-generic #54~16.04.1-Ubuntu SMP Wed Apr 26 16:00:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


3a:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:568b Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0
dell_laptop            20480  0
dell_smbios            16384  3 dell_wmi,dell_led,dell_laptop
ath10k_pci             45056  0
ath10k_core           335872  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              761856  1 ath10k_core
cfg80211              581632  3 mac80211,ath,ath10k_core
sparse_keymap          16384  3 dell_wmi,intel_hid,intel_vbtn
wmi                    16384  2 dell_wmi,dell_led
video                  40960  3 dell_wmi,dell_laptop,i915


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:34945 (34.9 KB)  TX bytes:34945 (34.9 KB)


wlp58s0   Link encap:Ethernet  HWaddr <MAC 'wlp58s0' [IF1]>  
          inet addr:35.20.214.27  Bcast:35.20.255.255  Mask:255.255.128.0
          inet6 addr: fe80::e05e:9f42:dd7c:b73d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5633886 (5.6 MB)  TX bytes:574401 (574.4 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlp58s0   IEEE 802.11  ESSID:"MSUnet 3.0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'MSUnet 3.0' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=10 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         35.20.128.1     0.0.0.0         UG    600    0        0 wlp58s0
1.1.1.1         35.20.128.1     255.255.255.255 UGH   600    0        0 wlp58s0
35.20.128.0     0.0.0.0         255.255.128.0   U     600    0        0 wlp58s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp58s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       730     1  0 18:18 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp58s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp58s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:3a:00.0/net/wlp58s0
GENERAL.IP-IFACE:                       wlp58s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MSUnet 3.0
GENERAL.CON-UUID:                       812e6414-9aff-4282-b391-c50d428a6113
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   812e6414-9aff-4282-b391-c50d428a6113 | MSUnet 3.0
IP4.ADDRESS[1]:                         35.20.214.27/17
IP4.GATEWAY:                            35.20.128.1
IP4.ROUTE[1]:                           dst = 1.1.1.1/32, nh = 35.20.128.1, mt = 600
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             35.8.2.7
IP4.DNS[2]:                             35.8.2.41
IP4.WINS[1]:                            35.8.2.25
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = dynamic-eolsen1-msu.edu-2
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1493864347
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 14400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 35.20.214.27
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 35.20.128.1
DHCP4.OPTION[20]:                       broadcast_address = 35.20.255.255
DHCP4.OPTION[21]:                       domain_name_servers = 35.8.2.7 35.8.2.41
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       netbios_name_servers = 35.8.2.25
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.128.0
DHCP4.OPTION[27]:                       network_number = 35.20.128.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 1.1.1.1
IP6.ADDRESS[1]:                         fe80::e05e:9f42:dd7c:b73d/64
IP6.GATEWAY:             

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


wlp58s0   32 channels in total; available frequencies :
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
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      8   APs on   Frequency:2.412 GHz (Channel 1)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:5.2 GHz (Channel 40)
      3   APs on   Frequency:5.32 GHz (Channel 64)

##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     8DB6E266EF9D63EC5C2B007
depends:        ath10k_core
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     663DAB23AD4CFA103833EE1
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-51-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
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


[    3.574015] ath10k_pci 0000:3a:00.0: enabling device (0000 -> 0002)
[    3.578942] ath10k_pci 0000:3a:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    3.856359] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:3a:00.0.bin failed with error -2
[    3.856366] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/cal-pci-0000:3a:00.0.bin failed with error -2
[    3.856589] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.856591] ath10k_pci 0000:3a:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.857552] ath10k_pci 0000:3a:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    3.857553] ath10k_pci 0000:3a:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.857992] ath10k_pci 0000:3a:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    3.921353] ath10k_pci 0000:3a:00.0: board_file api 2 bmi_id N/A crc32 6fc88fe7
[    6.052124] ath10k_pci 0000:3a:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    6.137277] ath: EEPROM regdomain: 0x69
[    6.137278] ath: EEPROM indicates we should expect a direct regpair map
[    6.137280] ath: Country alpha2 being used: 00
[    6.137281] ath: Regpair used: 0x69
[    6.219155] ath10k_pci 0000:3a:00.0 wlp58s0: renamed from wlan0
[    6.270722] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready (repeated 3 times)
[   17.562689] wlp58s0: authenticate with <MAC 'MSUnet 3.0' [AC1]>
[   17.611502] wlp58s0: send auth to <MAC 'MSUnet 3.0' [AC1]> (try 1/3)
[   17.619150] wlp58s0: authenticated
[   17.622926] wlp58s0: associate with <MAC 'MSUnet 3.0' [AC1]> (try 1/3)
[   17.628088] wlp58s0: RX AssocResp from <MAC 'MSUnet 3.0' [AC1]> (capab=0x421 status=0 aid=9)
[   17.631115] wlp58s0: associated
[   17.631152] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes ready
[   17.633378] ath: EEPROM regdomain: 0x8348
[   17.633379] ath: EEPROM indicates we should expect a country code
[   17.633380] ath: doing EEPROM country->regdmn map search
[   17.633380] ath: country maps to regdmn code: 0x3a
[   17.633381] ath: Country alpha2 being used: US
[   17.633381] ath: Regpair used: 0x3a
[   17.633382] ath: regdomain 0x8348 dynamically updated by country IE
[   17.720186] wlp58s0: Limiting TX power to 10 dBm as advertised by <MAC 'MSUnet 3.0' [AC1]>


########## wireless info END ############
```




If more information is needed please let me know.

---

### Post by Demask on 2017-05-04
The displayed connection speed may not reflect your actual connection speed, the wiki-page for the XPS (9360) on Arch linux wiki mentions the same issue [https://wiki.archlinux.org/index.php/Dell_XPS_13_(9360)#Wireless](https://wiki.archlinux.org/index.php/Dell_XPS_13_(9360)#Wireless).

---

### Post by 23senick on 2017-05-06
When using web browser, downloads etc, does it actually appear slow and perform badly?  I've noticed this feature on many ubuntu/hardware variants, in my case it seemed to reflect the "resting" speed which I guess may save battery on laptops. Try opening the connection information, then open something else that requires downloads (eg update manager).  On my Chromebook it instantly jumps to 144Mb/s.

---

### Post by jeremy31 on 2017-05-06
You may have to find a place closer to the access point as your signal strength is about 50% and the access point is limiting your transmit power

---


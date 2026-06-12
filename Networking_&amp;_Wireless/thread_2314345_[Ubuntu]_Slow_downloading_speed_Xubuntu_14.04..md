---
title: "[Ubuntu] Slow downloading speed Xubuntu 14.04."
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by zubin3 on 2016-02-20
Hello community,
I have done a fresh install of Xubuntu 14.04 and I'm getting slow download speed than what I used to get on my previous Ubuntu 14.04 install.
I get <100Kbps on my current installation of Xubuntu, whereas I'm still getting my regular ~500Kbps on my Windows. (Triple boot)

Here's the output from the wireless debugging script:
```
########## wireless info START ##########

Report from: 20 Feb 2016 17:57 IST +0530


Booted last: 19 Feb 2016 12:40 IST +0530


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell Device [1028:05ea]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:4462]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 003 Device 006: ID 0c45:64ad Microdia 
Bus 003 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 009: ID 04f3:0034 Elan Microelectronics Corp. 
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: dell-rbtn: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


iwlmvm                278528  0 
mac80211              712704  1 iwlmvm
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
iwlwifi               188416  1 iwlmvm
cfg80211              524288  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 dell_led,dell_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:192.168.82.1  Bcast:192.168.82.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.168.1  Bcast:172.16.168.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet8' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2504880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2354197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1818720674 (1.8 GB)  TX bytes:589068350 (589.0 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


vmnet1    no wireless extensions.


vmnet8    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"NoAccess"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'NoAccess' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:55  Invalid misc:512   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0
172.16.168.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.82.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1


##### resolv.conf #######################


nameserver 10.0.0.1
nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       936     1  0 Feb19 ?        00:00:07 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [NoAccess] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *NoAccess:       Infra, <MAC 'NoAccess' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA


  IPv4 Settings:
    Address:         10.0.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             10.0.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


Sorry, try again.
[[/etc/NetworkManager/system-connections/NoAccess]] (600 root)
[connection] id=NoAccess | type=802-11-wireless
[802-11-wireless] ssid=NoAccess | mac-address=<MAC 'wlan0' [IF]> | mtu=1500
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


vmnet1    no frequency information.


vmnet8    no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


vmnet1    Interface doesn't support scanning.


vmnet8    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NoAccess' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"NoAccess"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004bd0df53b
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4375FD8600770B0C2A7E11D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.19.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     B470AF663F8CCFC606AA966
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.19.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


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


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[34837.903119] bridge-wlan0: attached
[45100.388181] bridge-wlan0: disabling the bridge
[45100.408918] bridge-wlan0: down
[45100.408933] bridge-wlan0: detached
[45143.192112] wlan0: authenticate with <MAC 'NoAccess' [AC1]>
[45143.194569] wlan0: send auth to <MAC 'NoAccess' [AC1]> (try 1/3)
[45143.196343] wlan0: authenticated
[45143.196444] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[45143.199385] wlan0: associate with <MAC 'NoAccess' [AC1]> (try 1/3)
[45143.202024] wlan0: RX AssocResp from <MAC 'NoAccess' [AC1]> (capab=0x411 status=0 aid=2)
[45143.203526] wlan0: associated
[45143.224329] bridge-wlan0: device is wireless, enabling SMAC
[45143.224331] bridge-wlan0: up
[45143.226242] bridge-wlan0: attached
[56757.660919] wlan0: deauthenticated from <MAC 'NoAccess' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[56758.282326] bridge-wlan0: disabling the bridge
[56758.287463] bridge-wlan0: down
[56758.287470] bridge-wlan0: detached
[56758.295996] wlan0: authenticate with <MAC 'NoAccess' [AC1]>
[56758.297612] wlan0: send auth to <MAC 'NoAccess' [AC1]> (try 1/3)
[56758.299377] wlan0: authenticated
[56758.299505] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[56758.303470] wlan0: associate with <MAC 'NoAccess' [AC1]> (try 1/3)
[56758.306117] wlan0: RX AssocResp from <MAC 'NoAccess' [AC1]> (capab=0x411 status=0 aid=2)
[56758.307146] wlan0: associated
[56758.906165] bridge-wlan0: device is wireless, enabling SMAC
[56758.906168] bridge-wlan0: up
[56758.906173] bridge-wlan0: attached


########## wireless info END ############



```

Any fixes would be much appreciated. :)
Thanks.

---

### Post by praseodym on 2016-02-20
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```
If it is not enough, also deactivate the queue:
```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot. I strongly recommend changing the router encryption to WPA2-AES (CCMP), not WPA (TKIP) which is based on WEP and can be easily cracked. Password needs to have 8 characters then

---

### Post by zubin3 on 2016-02-21
Thank you praseodym, for the reply. 

Changing the power management and deactivating the queue has certainly helped in getting the speed back. Though, I'm still getting ~200KBps, and tested with the same download from my other LinuxMint / Windows install, they still get the same ~500KBps. 

Any other fix that you can see for it?

Yes, thank you for the advice. I'm actually pentesting on my home router, and like you said, it's easier to break WPA! :p

---


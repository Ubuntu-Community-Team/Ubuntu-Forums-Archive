---
title: "Wifi issue on Lenovo ideapad yoga 2 13 running 14.10 dualboot"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by karnik2 on 2014-12-04
Windows 8.1 and ubuntu 14.10 dual boot;
 Intel n7260 wifi adapter;
 driver = iwlwifi;
 driverversion = 3.1.0-25-generic; 
firmware = 25.222.99.0;

I'm getting a solid wifi connection on Win 8.1 but when I switch to Ubuntu it's a pain. The connection is very weak for the first few minutes and then goes dead before I have to reboot the device.
This is my first experience with Ubuntu and I've fallen in love with it already. But without a proper wifi connection I might have to stick to Win 8.1 :
I'm low on time, help would be much appreciated!

---

### Post by wildmanne39 on 2014-12-04
Please use normal fonts.
Thanks

---

### Post by jeremy31 on 2014-12-04
I would suggest using the wireless script, link is in Wild Man's signature line and use code tags, also in the sig

---

### Post by karnik2 on 2014-12-04
```


########## wireless info START ##########


Report from: 05 Dec 2014 09:00 IST +0530


Booted last: 05 Dec 2014 08:58 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic


##### kernel ############################


Linux 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 5986:054a Acer, Inc 
Bus 002 Device 003: ID 04f3:0304 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                217988  0 
mac80211              660592  1 iwlmvm
iwlwifi               182909  1 iwlmvm
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
cfg80211              510218  3 iwlwifi,mac80211,iwlmvm
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:755926 (755.9 KB)  TX bytes:163981 (163.9 KB)


##### iwconfig ##########################


virbr0    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ACT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ACT' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [ACT] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *ACT:            Infra, <MAC 'ACT' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[[/etc/NetworkManager/system-connections/ACT]] (600 root)
[connection] id=ACT | type=802-11-wireless
[802-11-wireless] ssid=ACT | bssid=<MAC 'ACT' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR12]] (600 root)
[connection] id=NETGEAR12 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR12 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country IN: DFS-UNSET
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5735 - 5835 @ 40), (N/A, 20)


##### iwlist channels ###################


virbr0    no frequency information.


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)


virbr0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ACT' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ACT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009061ae8c
                    Extra: Last beacon: 27396ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.16.0-25-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     745EC36274968E8B9763DF1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.16.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     47858A8653B88C1F785045F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.16.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
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
probe_wait_ms: 500


[iwlwifi]
11n_disable: 2
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
wd_disable: 1


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=2


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


[/etc/modprobe.d/rtlwifi.conf]
options rtl8723be swenc=1


##### rc.local ##########################


echo 322 > /sys/class/backlight/intel_backlight/brightness
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   18.929120] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[   18.941132] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.707064] wlan0: authenticate with <MAC 'ACT' [AC1]>
[   19.709105] wlan0: send auth to <MAC 'ACT' [AC1]> (try 1/3)
[   19.710977] wlan0: authenticated
[   19.711863] wlan0: associate with <MAC 'ACT' [AC1]> (try 1/3)
[   19.720049] wlan0: RX AssocResp from <MAC 'ACT' [AC1]> (capab=0x431 status=0 aid=1)
[   19.722348] wlan0: associated
[   19.722377] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  119.206913] wlan0: authenticate with <MAC 'ACT' [AC1]>
[  119.209325] wlan0: send auth to <MAC 'ACT' [AC1]> (try 1/3)
[  119.342326] wlan0: send auth to <MAC 'ACT' [AC1]> (try 2/3)
[  119.347188] wlan0: authenticated
[  119.349529] wlan0: associate with <MAC 'ACT' [AC1]> (try 1/3)
[  119.453650] wlan0: associate with <MAC 'ACT' [AC1]> (try 2/3)
[  119.471162] wlan0: RX AssocResp from <MAC 'ACT' [AC1]> (capab=0x431 status=0 aid=1)
[  119.472075] wlan0: associated
[  119.472129] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  121.236834] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[  121.248693] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  122.471536] wlan0: authenticate with <MAC 'ACT' [AC1]>
[  122.473932] wlan0: send auth to <MAC 'ACT' [AC1]> (try 1/3)
[  122.475621] wlan0: authenticated
[  122.477515] wlan0: associate with <MAC 'ACT' [AC1]> (try 1/3)
[  122.481396] wlan0: RX AssocResp from <MAC 'ACT' [AC1]> (capab=0x431 status=0 aid=1)
[  122.491292] wlan0: associated
[  122.491320] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

I'm sorry for being so unclear initially, I'm only a day old in this world of ubuntu.

---

### Post by karnik2 on 2014-12-05
Would re installing with a older version of ubuntu help?

---

### Post by jeremy31 on 2014-12-05
A few things to try.  If you can change the router security settings to WPA2-AES only, do it as you are running a mixed mode now.  In terminal  ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` the last line says ```
options iwlwifi 11n_disable=2
``` change it to be```
options iwlwifi 11n_disable=8
``` save and exit program then in terminal```
sudo iwconfig wlan0 power off
```
reboot and see if things are better

---

### Post by karnik2 on 2014-12-05
It's still as unstable as it was. :/

---

### Post by jeremy31 on 2014-12-05
I would try Ubuntu 14.04 as it is a long term support version where 14.10 will only be supported until the middle of next year if you are lucky

---

### Post by karnik2 on 2014-12-05
I also notice that when I'm closer to the router, the connection is very stable. Does that mean this is a hardware issue? But I have no such issues on win 8.1

---

### Post by jeremy31 on 2014-12-05
Might be a driver issue as I have no reception issues with my 7260 wifi cards, but I am not using 14.10

---

### Post by karnik2 on 2014-12-05
Okay, will try 14.04 and let you know!

---

### Post by karnik2 on 2014-12-05
IT WORKS!

As soon as I installed 14.04 I got a huge update (294MB) which included a network management update too.

Once that got done, I've been getting a stable connection.

I really hope the 14.10 issue gets solved soon.
Thanks anyway!

---

### Post by jeremy31 on 2014-12-05
> **karnik2 said:**
> IT WORKS!

As soon as I installed 14.04 I got a huge update (294MB) which included a network management update too.

Once that got done, I've been getting a stable connection.

I really hope the 14.10 issue gets solved soon.
Thanks anyway!

Strange as I downloaded the 14.10 64 bit ISO and was able to connect to my wifi using WPA, WPA2, and even using TKIP.  The only way I couldn't connect was if I set my router up to not broadcast SSID.  But the 7260 card I have is a different version than yours but they use the same modules

---

### Post by karnik2 on 2014-12-05
And now the problem is back :/

I'm having a very slow and unstable connection again.

---

### Post by jeremy31 on 2014-12-06
Can you get the results from ```
lshw -C network
```
I found a few bug reports and this [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1398171](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1398171) but it might take some time for it to be available

---

### Post by karnik2 on 2014-12-06
*-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 6b
       serial: 28:b2:bd:ca:f7:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-40-generic firmware=22.24.8.0 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:61 memory:b0400000-b0401fff

---


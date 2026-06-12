---
title: "Installing RT5370 USB Adapter 14.04 64bit"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by Nico_Janow on 2015-01-28
The instructions for older versions haven't worked for me.  I used [COLOR=#000000]driver 2.6.1.3, but get the following make error:[/COLOR]
```

[COLOR=#000000]^[/COLOR]
[COLOR=#000000]/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:[/COLOR]
[COLOR=#000000]/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.c:1141:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’[/COLOR]
[COLOR=#000000]pOSFSInfo->fsuid = current_fsuid();[/COLOR]
[COLOR=#000000]^[/COLOR]
[COLOR=#000000]/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.c:1142:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’[/COLOR]
[COLOR=#000000]pOSFSInfo->fsgid = current_fsgid();[/COLOR]
[COLOR=#000000]^[/COLOR]
[COLOR=#000000]make[2]: *** [/home/nico/newrt5370/nrt5370/os/linux/../../os/linux/rt_linux.o] Error 1[/COLOR]
[COLOR=#000000]make[1]: *** [_module_/home/nico/newrt5370/nrt5370/os/linux] Error 2[/COLOR]
[COLOR=#000000]make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-39-generic'[/COLOR]
[COLOR=#000000]make: *** [LINUX] Error 2[/COLOR]

```

[COLOR=#000000]I tried makefile, but got:[/COLOR]

[COLOR=#000000]install: cannot stat ‘rt5572sta.ko’: No such file or directory

I did try booting with the Atheros device removed; no change.   I blacklisted the two RT devices based on an old response of how to get it working.  Other people seem to have gotten the RT5370 working using the RT2800 drivers, but I'm not sure of the process for getting that to work.  Has anyone gotten the RT5370 working under 14.04?  I'm a linux novice, so I may have missed something obvious.



lsusb:

[/COLOR]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


wireless script output:

```



########## wireless info START ##########


Report from: 14 Jan 2015 11:11 MST -0700


Booted last: 14 Jan 2015 10:18 MST -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k_htc              95963  0 
ath9k_common           13551  1 ath9k_htc
ath9k_hw              453856  2 ath9k_common,ath9k_htc
ath                    28698  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              630653  1 ath9k_htc
cfg80211              484040  3 ath,mac80211,ath9k_htc


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


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.20.100  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::6670:2ff:fe0d:6b4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17436605 (17.4 MB)  TX bytes:7697845 (7.6 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"TELUS_Smart_Hub_00"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'TELUS_Smart_Hub_00' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:8240   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.20.1    0.0.0.0         UG    0      0        0 wlan0
192.168.20.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


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


- Device: wlan0  [TELUS_Smart_Hub_00] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           24 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *TELUS_Smart_Hub_00: Infra, <MAC 'TELUS_Smart_Hub_00' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA


  IPv4 Settings:
    Address:         192.168.20.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.20.1


    DNS:             192.168.20.1


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TELUS_Smart_Hub_00 1]] (600 root)
[connection] id=TELUS_Smart_Hub_00 1 | type=802-11-wireless
[802-11-wireless] ssid=TELUS_Smart_Hub_00 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TELUS_Smart_Hub_00]] (600 root)
[connection] id=TELUS_Smart_Hub_00 | type=802-11-wireless
[802-11-wireless] ssid=TELUS_Smart_Hub_00 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Edmonton (based on set time zone)


country CA:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TELUS_Smart_Hub_00' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"TELUS_Smart_Hub_00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ccb0e803
                    Extra: Last beacon: 304ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k_htc]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     76D0CC269ACAA11EA825B93
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


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
blacklist rt2800usb
blacklist rt2870sta


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   15.632453] usb 1-1.1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   15.870481] ath9k_htc 1-1.1:1.0: ath9k_htc: HTC initialized with 33 credits
[   16.146279] ath9k_htc 1-1.1:1.0: ath9k_htc: FW Version: 1.3
[   16.146283] ath: EEPROM regdomain: 0x809c
[   16.146284] ath: EEPROM indicates we should expect a country code
[   16.146285] ath: doing EEPROM country->regdmn map search
[   16.146286] ath: country maps to regdmn code: 0x52
[   16.146287] ath: Country alpha2 being used: CN
[   16.146288] ath: Regpair used: 0x52
[   17.736353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   21.029866] wlan0: authenticate with <MAC 'TELUS_Smart_Hub_00' [AC1]>
[   21.452380] wlan0: send auth to <MAC 'TELUS_Smart_Hub_00' [AC1]> (try 1/3)
[   21.454104] wlan0: authenticated
[   21.454208] ath9k_htc 1-1.1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   21.457870] wlan0: associate with <MAC 'TELUS_Smart_Hub_00' [AC1]> (try 1/3)
[   21.460611] wlan0: RX AssocResp from <MAC 'TELUS_Smart_Hub_00' [AC1]> (capab=0x411 status=0 aid=1)
[   21.470612] wlan0: associated
[   21.470633] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

[COLOR=#000000]

[/COLOR]

---

### Post by chili555 on 2015-01-28
Nico, Nico, Nico!!! Where do I even begin?

What's wrong with the Atheros? It's connected, it works and, aside from one or two things we might tweak, it seems fine. Is that the trouble? It's *TOO* good and you need trouble in your life? Can't you just get a Portuguese girlfriend or a vintage Fiat?

What does this tell us?```
modinfo rt2800usb | grep 5370
```>  I used driver 2.6.1.3, but get the following make error:It is waaaaay too old for your 3.13.0-xx kernel version.

---

### Post by Nico_Janow on 2015-01-29
The problem with the Atheros is an intermittent hardware flaw, probably a cold soldered joint or cracked trace.  It took about ten minutes to get it working right now.  I hope to get the new adapter working before the old one died permanently.  My vintage 85 Toyota gives much less trouble and hardware troubles can generally be fixed with minimal tools.

modinfo rt2800usb  | grep 5370
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*

The driver I tried is the one available on the mediatek site.  I haven't found a newer one.  I expected that the problem is that it was too old.  I'm skeptical that Mediatek will make an effort to update it if I asked politely.  They might just sell my email address.

It looks like my best option it to try getting the rt2800 drivers to work.  Delving into that now...


Okay, I managed to get it working via the rt2800 driver, following instructions that I didn't actually understand, from other threads in this forum.  Learned a bit more along the way, which I guess is the way to go with linux.  Thanks for acknowledging that the rt5370 driver was simply too old, which pointed me in the right direction.


Problem solved: just use the RT2800 driver for the RT5370 device.

---


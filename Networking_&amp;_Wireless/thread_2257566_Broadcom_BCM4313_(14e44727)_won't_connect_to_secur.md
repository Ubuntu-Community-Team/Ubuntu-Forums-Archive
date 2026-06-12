---
title: "Broadcom BCM4313 (14e4:4727) won't connect to secured networks, Ubuntu 14.10"
date: 2014-12-20
forum: Networking &amp; Wireless
---

### Post by mike273 on 2014-12-20
Hello,

I suppose this card has caused countless errors and there have been many threads that deal with them. I've read them, trust me. In the act of final despair I've decided to create my own thread.
I've got a fresh installation of Ubuntu 14.10. Initially the card worked well, right after I installed the proprietary driver 'bcmwl-kernel-source' (I think I couldn't connect to any network on stock driver). However, at some point today (I was installing new packages, getting my system ready to work on) I rebooted the system and ever since then I can't connect to a secure network, the same one I was successfully connected earlier. This wasn't the first reboot, yesterday I restarted my laptop several times.

I've tried following guidelines from this sticky: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
as well as some other guides, all with no results.

This is the output of the info script:

```



########## wireless info START ##########


Report from: 20 Dec 2014 22:57 CET +0100


Booted last: 20 Dec 2014 22:54 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Wistron NeWeb Corp. Device [185f:051a]
    Kernel driver in use: bcma-pci-bridge


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0a5]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 0a5c:219c Broadcom Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


brcmsmac              571212  0 
cordic                 12574  1 brcmsmac
brcmutil               15579  1 brcmsmac
mac80211              660592  1 brcmsmac
cfg80211              510218  2 brcmsmac,mac80211
bcma                   52443  2 brcmsmac
mxm_wmi                13021  0 
wmi                    19193  1 mxm_wmi


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


usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.164  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3:b3ff:fef4:494f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1165441 (1.1 MB)  TX bytes:365793 (365.7 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::92a4:deff:fe20:82e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3164 (3.1 KB)  TX bytes:4340 (4.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.164
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129


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


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Orange_FunSpot:  Infra, <MAC 'Orange_FunSpot' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    Babcia:          Infra, <MAC 'Babcia' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    Devil:           Infra, <MAC 'Devil' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2


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


[[/etc/NetworkManager/system-connections/Toffiland]] (600 root)
[connection] id=Toffiland | type=802-11-wireless
[802-11-wireless] ssid=Toffiland | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Babcia]] (600 root)
[connection] id=Babcia | type=802-11-wireless
[802-11-wireless] ssid=Babcia | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


##### iwlist channels ###################


eth0      no frequency information.


usb0      no frequency information.


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


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Orange_FunSpot' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"Orange_FunSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008228f9e5f
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: <MAC 'Babcia' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"Babcia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008228e7b28
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     21EC7461BC4D6521DBDCA51
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A0783053E3D218C552A3D06
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[bcma]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512


##### module parameters #################


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
blacklist b43
blacklist ssb


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   75.829699] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   75.829709] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   75.829860] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.292127] wlan0: authenticate with <MAC 'Babcia' [AC2]>
[   77.292234] wlan0: send auth to <MAC 'Babcia' [AC2]> (try 1/3)
[   77.296236] wlan0: authenticated
[   77.299258] wlan0: associate with <MAC 'Babcia' [AC2]> (try 1/3)
[   77.299436] wlan0: associate with <MAC 'Babcia' [AC2]> (try 2/3)
[   77.299634] wlan0: associate with <MAC 'Babcia' [AC2]> (try 3/3)
[   77.299834] wlan0: association with <MAC 'Babcia' [AC2]> timed out
[   78.031978] wlan0: authenticate with <MAC 'Babcia' [AC2]>
[   78.032076] wlan0: send auth to <MAC 'Babcia' [AC2]> (try 1/3)
[   78.035416] wlan0: authenticated
[   78.039480] wlan0: associate with <MAC 'Babcia' [AC2]> (try 1/3)
[   78.040088] wlan0: associate with <MAC 'Babcia' [AC2]> (try 2/3)
[   78.040851] wlan0: associate with <MAC 'Babcia' [AC2]> (try 3/3)
[   78.041158] wlan0: association with <MAC 'Babcia' [AC2]> timed out
[   79.176075] wlan0: authenticate with <MAC 'Babcia' [AC2]>
[   79.176144] wlan0: send auth to <MAC 'Babcia' [AC2]> (try 1/3)
[   79.177720] wlan0: send auth to <MAC 'Babcia' [AC2]> (try 2/3)
[   79.177987] wlan0: send auth to <MAC 'Babcia' [AC2]> (try 3/3)
[   79.180780] wlan0: authenticated
[   79.183799] wlan0: associate with <MAC 'Babcia' [AC2]> (try 1/3)
[   79.190086] wlan0: RX AssocResp from <MAC 'Babcia' [AC2]> (capab=0x431 status=0 aid=2)
[   79.190545] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   79.190548] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   79.190558] wlan0: associated
[   79.190566] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.276742] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   82.219020] wlan0: deauthenticated from <MAC 'Babcia' [AC2]> (Reason: 2=PREV_AUTH_NOT_VALID)
[   82.224403] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   82.224408] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement) (repeated 2 times)
[   86.117103] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   86.117246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   87.581031] wlan0: authenticate with <MAC 'Babcia' [AC2]>
[   87.581171] wlan0: send auth to <MAC 'Babcia' [AC2]> (try 1/3)
[   87.584987] wlan0: authenticated
[   87.589141] wlan0: associate with <MAC 'Babcia' [AC2]> (try 1/3)
[   87.589329] wlan0: associate with <MAC 'Babcia' [AC2]> (try 2/3)
[   87.593744] wlan0: RX AssocResp from <MAC 'Babcia' [AC2]> (capab=0x431 status=0 aid=2)
[   87.594314] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   87.594318] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   87.594325] wlan0: associated
[   87.594349] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.671126] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   90.638379] wlan0: deauthenticated from <MAC 'Babcia' [AC2]> (Reason: 2=PREV_AUTH_NOT_VALID)
[   90.653942] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   90.653959] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)


########## wireless info END ############

```

I have uninstalled all bcm-related packages (filtered by 'bcm' keyword in Synaptic and got rid of anything that passed as a Broadcom network driver), so I'm running native driver only, with ssb and b43 blacklisted (as you can see in the output).
I'm out of options and I have really no idea what else to try/do. I would greatly appreciate any help!

Cheers,
Mike

---

### Post by jeremy31 on 2014-12-20
Try changing the router encryption to WPA2-AES with no WPA-TKIP and see if your results change
This is from your wireless-info
```
[COLOR=#000000][FONT=Ubuntu Mono]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by mike273 on 2014-12-20
1. Unfortunately it didn't change a thing, still not connecting
2. It used to work earlier, with the same router settings. So, after all, it CAN connect to router with WPA2 MIXED encryption
3. Changing router settings is no solution. What if I had no access to the router?

---

### Post by jeremy31 on 2014-12-20
> **mike273 said:**
> 1. Unfortunately it didn't change a thing, still not connecting
2. It used to work earlier, with the same router settings. So, after all, it CAN connect to router with WPA2 MIXED encryption
3. Changing router settings is no solution. What if I had no access to the router?

Is the router set to a certain channel/frequency or set to auto?  I would set the secured network to channel 1 or 6

---

### Post by mike273 on 2014-12-20
It was set to auto (chn 11 was in use). I switched it to 6, with the same result.
Again - why are we looking at the router? I'd rather search for the solution within the driver. Even if we somehow manage to connect to the network by changing it's settings, I will later connect to some other network with different settings and then I'll have the same problem again.

---

### Post by jeremy31 on 2014-12-20
> **mike273 said:**
> It was set to auto (chn 11 was in use). I switched it to 6, with the same result.
Again - why are we looking at the router? I'd rather search for the solution within the driver. Even if we somehow manage to connect to the network by changing it's settings, I will later connect to some other network with different settings and then I'll have the same problem again.

I wonder if there was a kernel update that caused an issue, reboot and press shift to get the grub menu to show up and select advanced options for Ubuntu and choose an older kernel if available.  If you are sure it is a driver issue, a kernel update is the only way for that to happen since the drivers you are using are part of the kernel

---

### Post by mike273 on 2014-12-20
I was able to boot with 3.16.0-23-generic kernel but this didn't change a thing - still the same behaviour - it detects all wifi networks, but when it comes to connecting, it just repeatedly asks for password, tries to connect, asks again etc.
The very same thing used to happen when I used 'wl' driver instead of 'brcmsmac'. In other threads/posts/guides this usually happened when there were conflicting drivers, but I don't think if that's the case:

```
lsmod | egrep 'b43|brcm|wl|ssb|bcma
```
prints:
```

brcmsmac              571212  0 
cordic                 12574  1 brcmsmac
brcmutil               15579  1 brcmsmac
mac80211              660592  1 brcmsmac
cfg80211              510218  2 brcmsmac,mac80211
bcma                   52443  2 brcmsmac

```

---

### Post by jeremy31 on 2014-12-20
Does Ubuntu 14.04 work?  Ubuntu 14.10 will only be supported for about 4 more months and 14.04 will get support until 2019

---

### Post by mike273 on 2014-12-21
No, I haven't tried 14.10. I have tried different drivers though and It seems to work now. I'm not completly sure whym but after several reboots it always connects to the network now.
So I was using 'brcmsmac' driver, but here's what I found on their page:
> Please note: at least BCM4313 is not fully supported. Some models appears to work (users reported success), but some don't, and there's no indication that this is going to change.
Seems that my card is one of those not working.
This leaves me 1 option then, proprietary driver.
I've installed 'bcmwl-kernel-source' package and blacklisted 'brcmsmac' in /etc/modprobe.d/blacklist.conf. I also noticed that the package has created blacklisting file with all other drivers itself. Once the package was installed, I was able to connect immediately. This has happened before, though, with other drivers as well, so I restarted the laptop. It connected. Restart again - connected again. I have ran the info script again and here's the output:

```



########## wireless info START ##########


Report from: 21 Dec 2014 09:52 CET +0100


Booted last: 21 Dec 2014 09:51 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Wistron NeWeb Corp. Device [185f:051a]
    Kernel driver in use: wl


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0a5]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 004: ID 0a5c:219c Broadcom Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wl                   6367694  0 
mxm_wmi                13021  0 
cfg80211              510218  1 wl
wmi                    19193  1 mxm_wmi


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
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92a4:deff:fe20:82e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:1366
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4409 (4.4 KB)  TX bytes:21849 (21.8 KB)
          Interrupt:16 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"Babcia"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Babcia' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


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


- Device: wlan0  [Babcia] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
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
    Orange_FunSpot:  Infra, <MAC 'Orange_FunSpot' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    *Babcia:         Infra, <MAC 'Babcia' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2


  IPv4 Settings:
    Address:         192.168.1.101
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


[[/etc/NetworkManager/system-connections/Toffiland]] (600 root)
[connection] id=Toffiland | type=802-11-wireless
[802-11-wireless] ssid=Toffiland | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Babcia]] (600 root)
[connection] id=Babcia | type=802-11-wireless
[802-11-wireless] ssid=Babcia | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country PL: DFS-UNSET
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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


Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Babcia' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Babcia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Orange_FunSpot' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"Orange_FunSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 8ms ago


##### module infos ######################


[wl]
filename:       /lib/modules/3.16.0-28-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     DF2576C38AD45205B3556DD
depends:        cfg80211
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
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
blacklist b43
blacklist ssb
blacklist brcmsmac


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   97.400015] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############

```

I have also noticed something. After running 'sudo lshw -C network' now, the output is:

```

*-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:a4:de:20:82:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:f6c00000-f6c03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:44:65:fe
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:b000(size=256) memory:e2c04000-e2c04fff memory:e2c00000-e2c03fff

```

Earlier it listed 3 interfaces: those 2 above and one more wireless (unnamed). Curiously, the 'nameless' wireless interface was runing brcmsmac driver, while the BCM4313 - 'bcm-<something>' (I don't remember the name, sorry).
As you can see - the second wireless interface is now gone.

Another difference I noticed: running "lsmod | egrep 'b43|brcm|wl|ssb|bcma'" generated this output:
```

wl                   6367694  0 
cfg80211              510218  1 wl

```

When I was running brcmsmac driver the output list contained more elements. Now I'm not sure how to interpret it, but was it posiible that those elements (you can see them in my earlier post) cause this new interface to show up and 'hijack' the driver, causing network connection problem?

---


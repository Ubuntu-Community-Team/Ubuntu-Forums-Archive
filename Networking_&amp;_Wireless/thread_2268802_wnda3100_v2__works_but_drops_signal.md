---
title: "wnda3100_v2  works but drops signal"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by ChopMaster on 2015-03-11
Hello.  First time posting here but have learned a lot form other posts.   Thanks for any help you can provide.
I have gone as far to get my wnda3100_v2 installed and connect to the router but it is not stable.

I also have already ran these updates prior to this post:  
sudo apt-get update
sudo apt-get dist-upgrade

Hope that helps.

---

### Post by ChopMaster on 2015-03-11
```

########## wireless info START ##########

Report from: 11 Mar 2015 13:15 EDT -0400

Booted last: 11 Mar 2015 01:48 EDT -0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82c6]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:0095 Microsoft Corp. IntelliMouse Explorer 4.0 (IntelliPoint)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
ndiswrapper           283985  0 
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.127  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fed2:dd0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40564647 (40.5 MB)  TX bytes:2135752 (2.1 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e246:9aff:feb7:841a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930828 (930.8 KB)  TX bytes:117457 (117.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR-Guest"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'NETGEAR-Guest' [AC1]>   
          Bit Rate=130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:34  Invalid misc:10688   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [NETGEAR-Guest] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DDW36118D:       Infra, <MAC 'DDW36118D' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Chranian:        Infra, <MAC 'Chranian' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 64 WEP
    NETGEAR73:       Infra, <MAC 'NETGEAR73' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 94 WPA2
    *NETGEAR-Guest:  Infra, <MAC 'NETGEAR-Guest' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 85
    belkin54g:       Infra, <MAC 'belkin54g' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    WirelessHome3456:Infra, <MAC 'WirelessHome3456' [AC4]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA2
    DDW365CB:        Infra, <MAC 'DDW365CB' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2

  IPv4 Settings:
    Address:         192.168.1.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.127
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

[[/etc/NetworkManager/system-connections/NETGEAR73]] (600 root)
[connection] id=NETGEAR73 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR73 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR-Guest]] (600 root)
[connection] id=NETGEAR-Guest | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR-Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT752]] (600 root)
[connection] id=ATT752 | type=802-11-wireless
[802-11-wireless] ssid=ATT752 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR-Guest' [AC1]>
                    ESSID:"NETGEAR-Guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 02 - Address: <MAC 'NETGEAR73' [AC2]>
                    ESSID:"NETGEAR73"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'R<MAC address>Rext' [AC3]>
                    ESSID:"R&Rext"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: <MAC 'WirelessHome3456' [AC4]>
                    ESSID:"WirelessHome3456"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Chranian' [AC5]>
                    ESSID:"Chranian"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: <MAC 'DDW365CB' [AC6]>
                    ESSID:"DDW365CB"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  111.782326] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  111.789182] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  112.130569] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  112.692597] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  112.695626] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  112.729000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  133.493075] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[39127.877763] ndiswrapper: device wlan0 removed
[39130.709073] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[39131.278680] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[39131.281528] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[39131.297582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[39141.904407] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############ 
```

---

### Post by chili555 on 2015-03-11
I see that you have both an ethernet connection and wireless. Please detach the ethernet for all further tests.

Second, I see that you are connected to an unencrypted network. That's very dangerous. Let's concentrate on connecting to NETGEAR73.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Then, with the ethernet still detached, try to connect. If you can't, please run and post:```
dmesg | grep -e wlan -e ndis | tail -n20
```Thanks.

---

### Post by ChopMaster on 2015-03-11
```
chopmaster@ChopMaster:~$ sudo iw reg get
[sudo] password for chopmaster: 
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
chopmaster@ChopMaster:~$ 
 
```

---

### Post by chili555 on 2015-03-11
> country [COLOR="#FF0000"]00[/COLOR]:I recommend you set it explicitly as above.

---

### Post by ChopMaster on 2015-03-11
I got this ....```
  chopmaster@ChopMaster:~$ sudo iw reg get
[sudo] password for chopmaster: 
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
chopmaster@ChopMaster:~$ 
```

---

### Post by ChopMaster on 2015-03-11
I am not sure how to get to Network Manager to ignore pv6

---

### Post by ChopMaster on 2015-03-11
Found the Manager in the drop down window for wify......so it is ignored now

---

### Post by ChopMaster on 2015-03-11
```
  
########## wireless info START ##########

Report from: 11 Mar 2015 17:41 EDT -0400

Booted last: 11 Mar 2015 01:48 EDT -0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82c6]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:0095 Microsoft Corp. IntelliMouse Explorer 4.0 (IntelliPoint)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
ndiswrapper           283985  0 
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:50914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48763715 (48.7 MB)  TX bytes:5174065 (5.1 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e246:9aff:feb7:841a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7839516 (7.8 MB)  TX bytes:2209307 (2.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR73"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'NETGEAR73' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:319  Invalid misc:104774   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [NETGEAR73] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           144 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    R&Rext:          Infra, <MAC 'R<MAC 'R<MAC address>Rext' [AN1]>Rext' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 55 WEP
    NETGEAR-Guest:   Infra, <MAC 'NETGEAR-Guest' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 100
    WirelessHome3456:Infra, <MAC 'WirelessHome3456' [AC3]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 39 WPA2
    *NETGEAR73:      Infra, <MAC 'NETGEAR73' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 87 WPA2
    ECOT:            Infra, <MAC 'ECOT' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

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
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NETGEAR73]] (600 root)
[connection] id=NETGEAR73 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR73 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/NETGEAR-Guest]] (600 root)
[connection] id=NETGEAR-Guest | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR-Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/belkin54g]] (600 root)
[connection] id=belkin54g | type=802-11-wireless
[802-11-wireless] ssid=belkin54g | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT752]] (600 root)
[connection] id=ATT752 | type=802-11-wireless
[802-11-wireless] ssid=ATT752 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR73' [AC1]>
                    ESSID:"NETGEAR73"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR-Guest' [AC2]>
                    ESSID:"NETGEAR-Guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 03 - Address: <MAC 'WirelessHome3456' [AC3]>
                    ESSID:"WirelessHome3456"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Chranian' [AC4]>
                    ESSID:"Chranian"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: <MAC 'R<MAC 'R<MAC address>Rext' [AN1]>Rext' [AC5]>
                    ESSID:"R&Rext"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: <MAC 'DDW365CB' [AC6]>
                    ESSID:"DDW365CB"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  111.782326] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  111.789182] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  112.130569] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  112.692597] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  112.695626] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  112.729000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  133.493075] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[39127.877763] ndiswrapper: device wlan0 removed
[39130.709073] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[39131.278680] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[39131.281528] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[39131.297582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[39141.904407] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[49937.036833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[49947.804712] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[50175.523927] ndiswrapper: device wlan0 removed
[50179.560953] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[50180.122577] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[50180.125389] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[50180.145703] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[50200.771279] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############
   
```

---

### Post by chili555 on 2015-03-11
Looks very good! Is it stable?

---

### Post by ChopMaster on 2015-03-11
No it is not.  After some time sitting it seems to go back to dropping the connection

---

### Post by ChopMaster on 2015-03-11
It says I am connected to the router although I have no access to the internet.

---

### Post by ChopMaster on 2015-03-11
no it is not for some reason

---

### Post by ChopMaster on 2015-03-12
```
chopmaster@ChopMaster:~$ dmesg | grep -e wlan -e ndis | tail -n20
[  147.430452] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  147.437343] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  147.778228] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  148.335391] wlan0: ethernet device e0:46:9a:b7:84:1a using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[  148.338095] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  148.338792] usbcore: registered new interface driver ndiswrapper
[  148.379125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  148.379582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  492.648342] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
chopmaster@ChopMaster:~$ 
   
```

---

### Post by chili555 on 2015-03-12
I'm sorry. I have no other suggestions. Perhaps another one of our gurus has one. Your *dmesg* looks entirely in order.

---

### Post by ChopMaster on 2015-03-12
Thank you just the same for getting me this far.  I could not of even got it to work without your posts.

---


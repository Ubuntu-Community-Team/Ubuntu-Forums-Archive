---
title: "Ubuntu 16.04 LTS Server Wireless not working"
date: 2017-09-13
forum: Networking &amp; Wireless
---

### Post by laser1 on 2017-09-13
Hello,

I have a mini PC that has Ubuntu 16.04 LTS Server installed and I cannot get the wireless working it is a Broadcom chip and I have tried the Broadcom solutions , but nothing has worked as of yet.

Any help would be greatly appreciated.

Here is the output of the wireless-info.txt


```
########## wireless info START ##########

Report from: 13 Sep 2017 12:10 PDT -0700

Booted last: 13 Sep 2017 00:00 PDT -0700

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/budderfly/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
    Subsystem: Dell Wireless 1520 Half-size Mini PCIe Card [1028:000e]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   417792  0
mac80211              737280  2 b43,brcmsmac
cfg80211              565248  3 b43,brcmsmac,mac80211
ssb                    65536  1 b43
bcma                   53248  3 b43,brcmsmac

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp1s0
iface enp1s0 inet dhcp
iface enp1s0 inet6 auto

auto wlp2s0
iface wlp2s0 inet dhcp

wpa-ssid Testing
wpa-psk <WPA key removed>

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:391557 (391.5 KB)  TX bytes:208706 (208.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:13475 (13.4 KB)  TX bytes:13475 (13.4 KB)

wlp2s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp2s0b1' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0b1  IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 enp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp1s0

##### resolv.conf #######################

nameserver 209.18.47.62
nameserver 209.18.47.61
search socal.rr.com

##### network managers ##################

Installed:

    None found.

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

enp1s0    no frequency information.

wlp2s0b1  32 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)

wlp2s0b1  Scan completed :
          Cell 01 - Address: <MAC 'laser1' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"laser1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000041edd65
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Testing2' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Testing2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000853065e82
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Testing' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Testing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083ece5c46
                    Extra: Last beacon: 3156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000853063180
                    Extra: Last beacon: 3164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     CFC0DD2DF097296B2191A58
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[brcmutil]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[b43]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

[bcma]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     B8F81D53A09CD1D43DDE810
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[   10.724349] bcma-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
[   10.724519] bcma: bus0: Found chip with id 43224, rev 0x01 and package 0x0A
[   10.724555] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   10.724585] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   10.724639] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   10.762759] bcma: bus0: Bus registered
[   12.531505] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   12.531606] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   12.550061] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   12.553746] b43: probe of bcma0:1 failed with error -524
[   12.607369] brcmsmac bcma0:1: mfg 4bf core 812 rev 23 class 0 irq 17
[   12.635084] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 497
[   12.660925] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[   15.491391] r8169 0000:01:00.0 enp1s0: link up
[   15.491414] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[  195.728858] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  195.728990] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[  195.731011] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready

########## wireless info END ############



```

Thank you

---

### Post by praseodym on 2017-09-13
Blacklist the wrong driver:
```

echo "blacklist b43" | sudo tee /etc/modprobe.d/blacklist-b43.conf
```
Reboot

---

### Post by laser1 on 2017-09-13
I have disabled the driver and rebooted. 

However on reboot the network is showing as disabled.

Running lshw -C network gives me this

 ```

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 07
       serial: 70:e0:5d:68:1d:ea
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10b                            t 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI dup                            lex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.24 latency=0 link=yes multicast=yes por                            t=MII speed=1Gbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0704000-d0704fff memory:d0700000-d0703fff
  *-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d0600000-d0603fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlp2s0b1
       serial: 88:9f:fa:56:85:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.4.0-62-generic firmware=N/A                             link=no multicast=yes wireless=IEEE 802.11abgn

```

After running ifconfig wlp2s0b1 up

I can see wireless enabled

I still do not have an IP address



```
enp1s0    Link encap:Ethernet  HWaddr 70:e0:5d:68:1d:ea
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:112992 (112.9 KB)  TX bytes:59988 (59.9 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:12268 (12.2 KB)  TX bytes:12268 (12.2 KB)

wlp2s0b1  Link encap:Ethernet  HWaddr 88:9f:fa:56:85:3d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

If I reboot Wireless network/card is disabled again.

---

### Post by chili555 on 2017-09-13
> ##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp1s0
iface enp1s0 inet dhcp
iface enp1s0 inet6 auto

auto [COLOR="#FF0000"]wlp2s0[/COLOR]
iface wlp2s0 inet dhcp

wpa-ssid Testing
wpa-psk <WPA key removed>However, ifconfig reports:> [COLOR="#FF0000"]wlp2s0b1[/COLOR]  Link encap:Ethernet  HWaddr 88:9f:fa:56:85:3d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
<snip>Please change the /etc/network/interfaces file to read:```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp1s0
iface enp1s0 inet dhcp
iface enp1s0 inet6 auto

auto wlp2s0b1
iface wlp2s0b1 inet dhcp
wpa-ssid Testing
wpa-psk <WPA key removed>
```Reboot.

---

### Post by laser1 on 2017-09-13
I am now getting an IP address and I can SSH into server for awhile.

But I am still having an issue.

If I only connect via wireless (no ethernet cable plugged in for a wired connection), I SSH to it using the wireless IP.
After about 10 minutes my SSH session becomes unresponsive and times out. I can no longer access via the Wireless IP.

I start to get these messages in syslog:


```
Sep 13 14:36:51 budderfly-fc kernel: [  337.720892] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
Sep 13 14:36:51 budderfly-fc kernel: [  337.725539] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
Sep 13 14:36:51 budderfly-fc kernel: [  337.725569] brcmsmac bcma0:1: brcms_ops_bss_info_changed: cqm change: threshold 0, hys 0  (implement)
Sep 13 14:36:51 budderfly-fc kernel: [  337.725574] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
Sep 13 14:36:51 budderfly-fc kernel: [  337.725579] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
Sep 13 14:36:52 budderfly-fc kernel: [  338.591162] brcmsmac bcma0:1: wl0: fifo 0: descriptor error
Sep 13 14:36:52 budderfly-fc kernel: [  338.591171] brcmsmac bcma0:1: wl0: fatal error, reinitializing
Sep 13 14:36:52 budderfly-fc kernel: [  338.593132] ieee80211 phy0: Hardware restart was requested
Sep 13 14:36:52 budderfly-fc kernel: [  338.607453] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
Sep 13 14:36:52 budderfly-fc kernel: [  338.610079] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
Sep 13 14:36:52 budderfly-fc kernel: [  338.610113] brcmsmac bcma0:1: brcms_ops_bss_info_changed: cqm change: threshold 0, hys 0  (implement)
Sep 13 14:36:52 budderfly-fc kernel: [  338.610118] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
Sep 13 14:36:52 budderfly-fc kernel: [  338.610123] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
```



Any ideas on how to fix this issue? As this is a server, devices need to be able to connect to it at all times. At some locations I do not have the luxury of obtaining a wired connection.

Thanks again for all your help it is appreciated

---

### Post by chili555 on 2017-09-13
Let's see:```
lsmod | grep -e wl -e b43 -e brcm
```

---

### Post by laser1 on 2017-09-13
Here are results:

```
root@budderfly-fc:/var/log# lsmod | grep -e wl -e b43 -e brcm
brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              737280  1 brcmsmac
cfg80211              565248  2 brcmsmac,mac80211
bcma                   53248  2 brcmsmac
```

---

### Post by laser1 on 2017-09-14
Do those results show anything as to why i am getting disconnected from Wireless?

---

### Post by chili555 on 2017-09-15
> **laser1 said:**
> Do those results show anything as to why i am getting disconnected from Wireless?Yes, indeed. It shows this:> Sep 13 14:36:52 budderfly-fc kernel: [  338.591162] brcmsmac bcma0:1: wl0: fifo 0: descriptor error
Sep 13 14:36:52 budderfly-fc kernel: [  338.591171] brcmsmac bcma0:1: wl0: fatal error, reinitializing
Sep 13 14:36:52 budderfly-fc kernel: [  338.593132] ieee80211 phy0: Hardware restart was requestedI've Googled myself silly and don't know what else to try.

You might try blacklisting ALL the drivers that are listed in *lsmod* above and then load the proprietary driver:```
sudo modprobe wl
```Does the wireless work at all? Does it work well?

---

### Post by laser1 on 2017-09-19
Wireless works fine, then after about 20 minutes just drops. I can no longer access via wireless.

I then see these messages in syslog

```
Sep 19 07:13:19 budderfly-fc kernel: [  498.363621] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
Sep 19 07:13:20 budderfly-fc kernel: [  499.311097] brcmsmac bcma0:1: wl0: fifo 0: descriptor error
Sep 19 07:13:20 budderfly-fc kernel: [  499.315043] brcmsmac bcma0:1: wl0: fatal error, reinitializing
Sep 19 07:13:20 budderfly-fc kernel: [  499.320927] ieee80211 phy0: Hardware restart was requested
Sep 19 07:13:20 budderfly-fc kernel: [  499.338865] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
Sep 19 07:13:20 budderfly-fc kernel: [  499.345046] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
Sep 19 07:13:20 budderfly-fc kernel: [  499.349092] brcmsmac bcma0:1: brcms_ops_bss_info_changed: cqm change: threshold 0, hys 0  (implement)
Sep 19 07:13:20 budderfly-fc kernel: [  499.353097] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
Sep 19 07:13:20 budderfly-fc kernel: [  499.357063] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
Sep 19 07:13:21 budderfly-fc kernel: [  500.312190] brcmsmac bcma0:1: wl0: fifo 0: descriptor error
Sep 19 07:13:21 budderfly-fc kernel: [  500.316130] brcmsmac bcma0:1: wl0: fatal error, reinitializing
Sep 19 07:13:21 budderfly-fc kernel: [  500.321998] ieee80211 phy0: Hardware restart was requested
Sep 19 07:13:21 budderfly-fc kernel: [  500.336315] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
Sep 19 07:13:21 budderfly-fc kernel: [  500.343258] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
Sep 19 07:13:21 budderfly-fc kernel: [  500.347340] brcmsmac bcma0:1: brcms_ops_bss_info_changed: cqm change: threshold 0, hys 0  (implement)
Sep 19 07:13:21 budderfly-fc kernel: [  500.351336] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
Sep 19 07:13:21 budderfly-fc kernel: [  500.355295] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
```

Right after that see this:

```
Sep 19 07:18:44 budderfly-fc kernel: [  822.641309] WARNING: CPU: 0 PID: 1947 at /build/linux-W6HB68/linux-4.4.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:2672 brcms_c_suspend_mac_and_wait+0x24b/0x2c0 [brcmsmac]()
Sep 19 07:18:44 budderfly-fc kernel: [  822.641312] Modules linked in: drbg ansi_cprng ctr ccm nls_iso8859_1 arc4 brcmsmac cordic brcmutil mac80211 cfg80211 intel_rapl intel_soc_dts_iosf intel_powerclamp coretemp kvm_intel snd_hda_codec_hdmi snd_intel_sst_acpi snd_intel_sst_core snd_hda_codec_realtek snd_hda_codec_generic kvm snd_soc_sst_mfld_platform snd_hda_intel snd_hda_codec snd_soc_core irqbypass snd_compress punit_atom_debug snd_hda_core ac97_bus snd_pcm_dmaengine input_leds snd_hwdep snd_pcm joydev lpc_ich snd_timer bcma shpchp mei_txe snd mei soundcore snd_soc_sst_acpi mac_hid ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear hid_generic usbhid hid crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd i915 i2c_algo_bit drm_kms_helper r8169 syscopyarea sysfillrect sysimgblt ahci fb_sys_fops mii drm libahci fjes video
Sep 19 07:18:44 budderfly-fc kernel: [  822.641433] CPU: 0 PID: 1947 Comm: kworker/u4:1 Tainted: G        W       4.4.0-62-generic #83-Ubuntu
Sep 19 07:18:44 budderfly-fc kernel: [  822.641437] Hardware name: To be filled by O.E.M. To be filled by O.E.M./Aptio CRB, BIOS 5.6.5 01/19/2015
Sep 19 07:18:44 budderfly-fc kernel: [  822.641454] Workqueue: phy0 _brcms_timer [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641459]  0000000000000286 000000004d0b8c9f ffff8800349cfcd0 ffffffff813f7c63
Sep 19 07:18:44 budderfly-fc kernel: [  822.641465]  0000000000000000 ffffffffc093ff78 ffff8800349cfd08 ffffffff810812d2
Sep 19 07:18:44 budderfly-fc kernel: [  822.641471]  ffff880035359000 ffff8800349a2000 ffff880034a2b000 ffff880035359010
Sep 19 07:18:44 budderfly-fc kernel: [  822.641477] Call Trace:
Sep 19 07:18:44 budderfly-fc kernel: [  822.641488]  [<ffffffff813f7c63>] dump_stack+0x63/0x90
Sep 19 07:18:44 budderfly-fc kernel: [  822.641496]  [<ffffffff810812d2>] warn_slowpath_common+0x82/0xc0
Sep 19 07:18:44 budderfly-fc kernel: [  822.641501]  [<ffffffff8108141a>] warn_slowpath_null+0x1a/0x20
Sep 19 07:18:44 budderfly-fc kernel: [  822.641520]  [<ffffffffc08e053b>] brcms_c_suspend_mac_and_wait+0x24b/0x2c0 [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641539]  [<ffffffffc08e8b22>] wlapi_suspend_mac_and_wait+0x12/0x20 [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641560]  [<ffffffffc08ee4c8>] wlc_phy_stf_chain_active_get+0x48/0xb0 [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641580]  [<ffffffffc08e991a>] brcms_c_tempsense_upd+0x1a/0x60 [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641598]  [<ffffffffc08de5a0>] brcms_c_watchdog_by_timer+0xf0/0x2e0 [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641615]  [<ffffffffc08d8f43>] _brcms_timer+0x43/0xa0 [brcmsmac]
Sep 19 07:18:44 budderfly-fc kernel: [  822.641622]  [<ffffffff8109a515>] process_one_work+0x165/0x480
Sep 19 07:18:44 budderfly-fc kernel: [  822.641627]  [<ffffffff8109a87b>] worker_thread+0x4b/0x4c0
Sep 19 07:18:44 budderfly-fc kernel: [  822.641633]  [<ffffffff8109a830>] ? process_one_work+0x480/0x480
Sep 19 07:18:44 budderfly-fc kernel: [  822.641638]  [<ffffffff8109a830>] ? process_one_work+0x480/0x480
Sep 19 07:18:44 budderfly-fc kernel: [  822.641643]  [<ffffffff810a0ba8>] kthread+0xd8/0xf0
Sep 19 07:18:44 budderfly-fc kernel: [  822.641649]  [<ffffffff810a0ad0>] ? kthread_create_on_node+0x1e0/0x1e0
Sep 19 07:18:44 budderfly-fc kernel: [  822.641656]  [<ffffffff8183898f>] ret_from_fork+0x3f/0x70
Sep 19 07:18:44 budderfly-fc kernel: [  822.641661]  [<ffffffff810a0ad0>] ? kthread_create_on_node+0x1e0/0x1e0
Sep 19 07:18:44 budderfly-fc kernel: [  822.641665] ---[ end trace 354ff454f40f828e ]---
Sep 19 07:18:44 budderfly-fc kernel: [  822.641668] ------------[ cut here ]------------
```



Any ideas on what else to check? or configure?

---


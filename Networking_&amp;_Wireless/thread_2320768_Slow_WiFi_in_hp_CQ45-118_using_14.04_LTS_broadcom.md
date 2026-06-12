---
title: "Slow WiFi in hp CQ45-118 using 14.04 LTS broadcom"
date: 2016-04-17
forum: Networking &amp; Wireless
---

### Post by student-n on 2016-04-17
Hello Ubuntu comunity

I've been trying different possible solutions to repair the wifi in my laptop, in fact using the same machine loading windows arrives
at having the max of the internet connection at my home which is 20MB but with Ubuntu is around 4 to 7 Mb, any suggestion would be 
fully appreciated, thank you very much in advance for your time :)

```
lspci -nn
sudo lshw -C network

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Hewlett-Packard Company Device [103c:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 11h Processor HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 11h Processor DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS780M [Mobility Radeon HD 3200] [1002:9612]
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon (HD) 3000 Series] [1002:960f]
08:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
08:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
08:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
08:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
```

```
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d1100000-d1103fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth1
       version: 02
       serial: 00:1e:ec:aa:0c:fe
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan3
       serial: 00:21:00:68:66:c7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-85-generic firmware=666.2 ip=192.168.2.12 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by Hadaka on 2016-04-17
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is ***wireless-info.txt***
Next.
From your directory please copy,paste and post the ***wireless-info.txt***
thanks.

---

### Post by student-n on 2016-04-17
Hi Hadaka, here it is. Thanks for the fast reply



```
########## wireless info START ##########


Report from: 17 Apr 2016 13:43 EDT -0400


Booted last: 17 Apr 2016 13:25 EDT -0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
    Kernel driver in use: wl


0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30fb]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:c371 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wl                   6367819  0 
cfg80211              496328  1 wl
wmi                    19177  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan3     Link encap:Ethernet  HWaddr <MAC 'wlan3' [IF]>  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21944 errors:0 dropped:0 overruns:0 frame:76459
          TX packets:19480 errors:361 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21406783 (21.4 MB)  TX bytes:9157870 (9.1 MB)
          Interrupt:18 


##### iwconfig ##########################


eth1      no wireless extensions.


lo        no wireless extensions.


wlan3     IEEE 802.11abg  ESSID:"Leonardo Dr.PC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Leonardo Dr.PC' [AC1]>   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan3
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan3


##### resolv.conf #######################


nameserver 127.0.1.1
search Belkin


##### network managers ##################


Installed:


    NetworkManager


Running:


root       758     1  0 13:25 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan3  [Wi-Fi connection 1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan3' [IF]>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    VIDEOTRON4879:   Infra, <MAC 'VIDEOTRON4879' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    *Leonardo Dr.PC: Infra, <MAC 'Leonardo Dr.PC' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    BELL113:         Infra, <MAC 'BELL113' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    TP-LINK_2.4GHz_E5FB8B: Infra, <MAC 'TP-LINK_2.4GHz_E5FB8B' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BELL177:         Infra, <MAC 'BELL177' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Bell2545:        Infra, <MAC 'Bell2545' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BELL878:         Infra, <MAC 'BELL878' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2


  IPv4 Settings:
    Address:         192.168.2.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


[[/etc/NetworkManager/system-connections/leoRedmiNote]] (600 root)
[connection] id=leoRedmiNote | type=802-11-wireless
[802-11-wireless] ssid=leoRedmiNote | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Leonardo Dr.PC
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AF_MTL WiFi 1]] (600 root)
[connection] id=AF_MTL WiFi 1 | type=802-11-wireless
[802-11-wireless] ssid=AF_MTL WiFi | mac-address=<MAC 'wlan3' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AF_MTL WiFi]] (600 root)
[connection] id=AF_MTL WiFi | type=802-11-wireless
[802-11-wireless] ssid=AF_MTL WiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Montreal (based on set time zone)


country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


eth1      no frequency information.


lo        no frequency information.


wlan3     32 channels in total; available frequencies :
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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan3     Scan completed :
          Cell 01 - Address: <MAC 'Leonardo Dr.PC' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key: on
                    ESSID:"Leonardo Dr.PC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BELL113' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key: on
                    ESSID:"BELL113"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
          Cell 03 - Address: <MAC 'BELL878' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: o n
                    ESSID:"BELL878"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 17136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Bell2545' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key: on
                    ESSID:"Bell2545"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'VIDEOTRON4879' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key: on
                    ESSID:"VIDEOTRON4879"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'BELL938' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key: on
                    ESSID:"BELL938"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/3.13.0-85-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


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
options iwlwifi 11n_disable=12


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1503 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# PCI device 0x14e4:0x4315 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan3' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"
# PCI device 0x1106:0x3065 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


##### dmesg #############################


[    5.144069] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.258639] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    5.602612] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    6.130079] systemd-udevd[357]: renamed network interface wlan0 to wlan3
[    7.161348] r8169 0000:0a:00.0 eth1: link down
[    7.161422] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1055.439650] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############
```

---

### Post by Hadaka on 2016-04-17
Hi
From a working wired connection,Please open a terminal ctrl/alt/t
Copy and paste the following commands one at a time.

*Ignore any errors or file not found for commands 2 or 3

```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
then do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
and..your ssid..has a space and a "." in it..this can and does cause errors and drops
please modify,
```
Leonardo Dr.PC
```
lastly are you in the US or Canada?
when all this is completed, boot and test wireless
if you are still having difficulties..please post a new wireless diagnostic.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
and please use code tags.
How to -> [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
thanks.

---

### Post by student-n on 2016-04-17
Hi I already made the procedure you refer me, still is a mid speed, I mean for a connection of 20Mb is getting up to 8 with this new setup (5 more woohoo) But still is not it full capacity. I am connecting from Canada. Thank you very much

```



########## wireless info START ##########


Report from: 17 Apr 2016 15:46 EDT -0400


Booted last: 17 Apr 2016 15:40 EDT -0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
	Kernel driver in use: b43-pci-bridge


0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30fb]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:c371 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
b43                   387371  0 
bcma                   52096  1 b43
mac80211              638915  1 b43
cfg80211              496328  2 b43,mac80211
wmi                    19177  1 hp_wmi
ssb                    62379  1 b43


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44963253 (44.9 MB)  TX bytes:24971384 (24.9 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17467330 (17.4 MB)  TX bytes:13204543 (13.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"LeonardoDrPC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'LeonardoDrPC' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:774  Invalid misc:1001   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Belkin


##### network managers ##################


Installed:


	NetworkManager


Running:


root       793     1  0 15:40 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


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
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off


- Device: wlan0  [LeonardoDrPC] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TP-LINK_2.4GHz_E5FB8B: Infra, <MAC 'TP-LINK_2.4GHz_E5FB8B' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    VIDEOTRON4879:   Infra, <MAC 'VIDEOTRON4879' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    password is 123456: Infra, <MAC 'password is 123456' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    bimmer:          Infra, <MAC 'bimmer' [AC17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    VIDEOTRON4941:   Infra, <MAC 'VIDEOTRON4941' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    FAFAFA:          Infra, <MAC 'FAFAFA' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Bell2545:        Infra, <MAC 'Bell2545' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    VIDEOTRON4247:   Infra, <MAC 'VIDEOTRON4247' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Jammin Wireless: Infra, <MAC 'Jammin Wireless' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BELL113:         Infra, <MAC 'BELL113' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    BELL878:         Infra, <MAC 'BELL878' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    BELL694:         Infra, <MAC 'BELL694' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    BELL905:         Infra, <MAC 'BELL905' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BELL035:         Infra, <MAC 'BELL035' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    488stopbeingadick: Infra, <MAC '488stopbeingadick' [AN15]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    VIDEOTRON0243:   Infra, <MAC 'VIDEOTRON0243' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BELL177:         Infra, <MAC 'BELL177' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    DIAMOND-NETWORK: Infra, <MAC 'DIAMOND-NETWORK' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    BELL651:         Infra, <MAC 'BELL651' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    *LeonardoDrPC:   Infra, <MAC 'LeonardoDrPC' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    VIDEOTRON5601:   Infra, <MAC 'VIDEOTRON5601' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BELL195:         Infra, <MAC 'BELL195' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Mac's Wi-Fi Network: Infra, <MAC 'Mac's Wi-Fi Network' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BELL938:         Infra, <MAC 'BELL938' [AN24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    VIDEOTRON4575:   Infra, <MAC 'VIDEOTRON4575' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Nick Thamer:     Infra, <MAC 'Nick Thamer' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BELL293:         Infra, <MAC 'BELL293' [AN27]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2


  IPv4 Settings:
    Address:         192.168.2.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


[[/etc/NetworkManager/system-connections/leoRedmiNote]] (600 root)
[connection] id=leoRedmiNote | type=802-11-wireless
[802-11-wireless] ssid=leoRedmiNote | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Leonardo Dr.PC
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/LeonardoDrPC]] (600 root)
[connection] id=LeonardoDrPC | type=802-11-wireless
[802-11-wireless] ssid=LeonardoDrPC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AF_MTL WiFi 1]] (600 root)
[connection] id=AF_MTL WiFi 1 | type=802-11-wireless
[802-11-wireless] ssid=AF_MTL WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AF_MTL WiFi]] (600 root)
[connection] id=AF_MTL WiFi | type=802-11-wireless
[802-11-wireless] ssid=AF_MTL WiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Montreal (based on set time zone)


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      12   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'LeonardoDrPC' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=5 dBm  
                    Encryption key:on
                    ESSID:"LeonardoDrPC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000018c68446
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_2.4GHz_E5FB8B' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_2.4GHz_E5FB8B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003639acfdb5f
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BELL113' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BELL113"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c33a464d7b
                    Extra: Last beacon: 88ms ago
          Cell 04 - Address: <MAC 'FAFAFA' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"FAFAFA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009cfbc108b
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BELL177' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BELL177"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000014612ef
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Mac's Wi-Fi Network' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Mac's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025cd867c198
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'BELL195' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BELL195"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002ac6726
                    Extra: Last beacon: 336ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VIDEOTRON4941' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON4941"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003a133180
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'VIDEOTRON5601' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON5601"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002331f6181
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c6522c3e1d
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'VIDEOTRON0243' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON0243"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000011be3180
                    Extra: Last beacon: 280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'BELL905' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BELL905"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002292921
                    Extra: Last beacon: 420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Nick Thamer' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Nick Thamer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000042377def309
                    Extra: Last beacon: 368ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'VIDEOTRON4879' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON4879"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000051b68eb4
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'BELL694' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BELL694"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027f902180
                    Extra: Last beacon: 2400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'DIAMOND-NETWORK' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"DIAMOND-NETWORK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000421e4ca380a
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'bimmer' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"bimmer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf05986180
                    Extra: Last beacon: 2380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'password is 123456' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"password is 123456"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002bc7acc9a
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Bell2545' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Bell2545"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000506879a5d3
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'BELL936' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"BELL936"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002e375ef5180
                    Extra: Last beacon: 2556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'VIDEOTRON5079' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON5079"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001218a12180
                    Extra: Last beacon: 2052ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[b43]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
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


[bcma]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0EE2BE801594EE59EA3A85C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512


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
options iwlwifi 11n_disable=12


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    5.592100] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[    7.480108] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   13.136789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.165294] r8169 0000:0a:00.0 eth0: link down
[   13.165353] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.165955] r8169 0000:0a:00.0 eth0: link down
[   14.829688] r8169 0000:0a:00.0 eth0: link up
[   14.829706] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  227.182476] r8169 0000:0a:00.0 eth0: link down
[  248.249358] wlan0: authenticate with <MAC 'LeonardoDrPC' [AC1]>
[  248.272393] wlan0: send auth to <MAC 'LeonardoDrPC' [AC1]> (try 1/3)
[  248.291667] wlan0: authenticated
[  248.292626] wlan0: associate with <MAC 'LeonardoDrPC' [AC1]> (try 1/3)
[  248.295463] wlan0: RX AssocResp from <MAC 'LeonardoDrPC' [AC1]> (capab=0x411 status=0 aid=1)
[  248.295977] wlan0: associated
[  248.296074] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by Hadaka on 2016-04-17
Hi please open a terminal and do..
```
*echo "options* b43 *nohwcrypt*=*1*" | sudo tee -a /etc/modprobe.d/b43.conf
```
boot and test wireless
thanks.

---

### Post by student-n on 2016-04-17
Hi Hadaka

Tried but without results, pages load a bit slower but speed avg is the same :/

---

### Post by Hadaka on 2016-04-17
Your wireless report shows your country as US, this may
also be some of the reasons you are getting speeds you
you are not satisfied with. Please open a terminal then copy and paste..
```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
boot and post back a fresh wireless diagnostic report please.
thanks.

---

### Post by student-n on 2016-04-17
Hi Hadaka

Unfortunately didn't solve it, attaching also speedtest report, ndiswrapper could be an alternative or is not so healthly at all?

```
./speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from EBOX (96.127.195.106)...
Selecting best server based on latency...
Hosted by Fibrenoire Internet (Montreal, QC) [33.27 km]: 157.012 ms
Testing download speed........................................
Download: 1.93 Mbit/s
Testing upload speed..................................................
Upload: 1.11 Mbit/s


```

Fresh diagnostic from Wireless

```

########## wireless info START ##########

Report from: 17 Apr 2016 15:46 EDT -0400

Booted last: 17 Apr 2016 15:40 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
    Kernel driver in use: b43-pci-bridge

0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30fb]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:c371 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
b43                   387371  0 
bcma                   52096  1 b43
mac80211              638915  1 b43
cfg80211              496328  2 b43,mac80211
wmi                    19177  1 hp_wmi
ssb                    62379  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44963253 (44.9 MB)  TX bytes:24971384 (24.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17467330 (17.4 MB)  TX bytes:13204543 (13.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LeonardoDrPC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'LeonardoDrPC' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:774  Invalid misc:1001   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### network managers ##################

Installed:

    NetworkManager

Running:

root       793     1  0 15:40 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

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
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [LeonardoDrPC] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TP-LINK_2.4GHz_E5FB8B: Infra, <MAC 'TP-LINK_2.4GHz_E5FB8B' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    VIDEOTRON4879:   Infra, <MAC 'VIDEOTRON4879' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    password is 123456: Infra, <MAC 'password is 123456' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    bimmer:          Infra, <MAC 'bimmer' [AC17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    VIDEOTRON4941:   Infra, <MAC 'VIDEOTRON4941' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    FAFAFA:          Infra, <MAC 'FAFAFA' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Bell2545:        Infra, <MAC 'Bell2545' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    VIDEOTRON4247:   Infra, <MAC 'VIDEOTRON4247' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Jammin Wireless: Infra, <MAC 'Jammin Wireless' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BELL113:         Infra, <MAC 'BELL113' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    BELL878:         Infra, <MAC 'BELL878' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    BELL694:         Infra, <MAC 'BELL694' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    BELL905:         Infra, <MAC 'BELL905' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BELL035:         Infra, <MAC 'BELL035' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    488stopbeingadick: Infra, <MAC '488stopbeingadick' [AN15]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    VIDEOTRON0243:   Infra, <MAC 'VIDEOTRON0243' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BELL177:         Infra, <MAC 'BELL177' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    DIAMOND-NETWORK: Infra, <MAC 'DIAMOND-NETWORK' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    BELL651:         Infra, <MAC 'BELL651' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    *LeonardoDrPC:   Infra, <MAC 'LeonardoDrPC' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    VIDEOTRON5601:   Infra, <MAC 'VIDEOTRON5601' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BELL195:         Infra, <MAC 'BELL195' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Mac's Wi-Fi Network: Infra, <MAC 'Mac's Wi-Fi Network' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BELL938:         Infra, <MAC 'BELL938' [AN24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    VIDEOTRON4575:   Infra, <MAC 'VIDEOTRON4575' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Nick Thamer:     Infra, <MAC 'Nick Thamer' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BELL293:         Infra, <MAC 'BELL293' [AN27]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2

  IPv4 Settings:
    Address:         192.168.2.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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

[[/etc/NetworkManager/system-connections/leoRedmiNote]] (600 root)
[connection] id=leoRedmiNote | type=802-11-wireless
[802-11-wireless] ssid=leoRedmiNote | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Leonardo Dr.PC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LeonardoDrPC]] (600 root)
[connection] id=LeonardoDrPC | type=802-11-wireless
[802-11-wireless] ssid=LeonardoDrPC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AF_MTL WiFi 1]] (600 root)
[connection] id=AF_MTL WiFi 1 | type=802-11-wireless
[802-11-wireless] ssid=AF_MTL WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AF_MTL WiFi]] (600 root)
[connection] id=AF_MTL WiFi | type=802-11-wireless
[802-11-wireless] ssid=AF_MTL WiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Montreal (based on set time zone)

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      12   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'LeonardoDrPC' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=5 dBm  
                    Encryption key:on
                    ESSID:"LeonardoDrPC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000018c68446
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_2.4GHz_E5FB8B' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_2.4GHz_E5FB8B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003639acfdb5f
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BELL113' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BELL113"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c33a464d7b
                    Extra: Last beacon: 88ms ago
          Cell 04 - Address: <MAC 'FAFAFA' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"FAFAFA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009cfbc108b
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BELL177' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BELL177"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000014612ef
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Mac's Wi-Fi Network' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Mac's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025cd867c198
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'BELL195' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BELL195"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002ac6726
                    Extra: Last beacon: 336ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VIDEOTRON4941' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON4941"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003a133180
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'VIDEOTRON5601' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON5601"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002331f6181
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c6522c3e1d
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'VIDEOTRON0243' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON0243"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000011be3180
                    Extra: Last beacon: 280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'BELL905' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BELL905"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002292921
                    Extra: Last beacon: 420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Nick Thamer' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Nick Thamer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000042377def309
                    Extra: Last beacon: 368ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'VIDEOTRON4879' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON4879"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000051b68eb4
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'BELL694' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BELL694"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000027f902180
                    Extra: Last beacon: 2400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'DIAMOND-NETWORK' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"DIAMOND-NETWORK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000421e4ca380a
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'bimmer' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"bimmer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf05986180
                    Extra: Last beacon: 2380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'password is 123456' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"password is 123456"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002bc7acc9a
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Bell2545' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Bell2545"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000506879a5d3
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'BELL936' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"BELL936"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002e375ef5180
                    Extra: Last beacon: 2556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'VIDEOTRON5079' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON5079"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001218a12180
                    Extra: Last beacon: 2052ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
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

[bcma]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0EE2BE801594EE59EA3A85C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512

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
options iwlwifi 11n_disable=12

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    5.592100] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[    7.480108] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   13.136789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.165294] r8169 0000:0a:00.0 eth0: link down
[   13.165353] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.165955] r8169 0000:0a:00.0 eth0: link down
[   14.829688] r8169 0000:0a:00.0 eth0: link up
[   14.829706] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  227.182476] r8169 0000:0a:00.0 eth0: link down
[  248.249358] wlan0: authenticate with <MAC 'LeonardoDrPC' [AC1]>
[  248.272393] wlan0: send auth to <MAC 'LeonardoDrPC' [AC1]> (try 1/3)
[  248.291667] wlan0: authenticated
[  248.292626] wlan0: associate with <MAC 'LeonardoDrPC' [AC1]> (try 1/3)
[  248.295463] wlan0: RX AssocResp from <MAC 'LeonardoDrPC' [AC1]> (capab=0x411 status=0 aid=1)
[  248.295977] wlan0: associated
[  248.296074] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

Once again thanks and sorry for the inconvenient.

---

### Post by Hadaka on 2016-04-17
Hi the only thing i am seeing is a crowded wifi usage on channel 11
```
Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      12   APs on   Frequency:2.462 GHz (Channel ***11***)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'LeonardoDrPC' [AC1]>
                    Channel:***11***
```
Changing your router channel to 1 may help some, the b43
driver doesnt have alot of tweaks to make it faster, and your
wireless report shows good signal,no loss,no errors, connects on first try.
I am out of ideas, I did note the country code did not change.You can edit
the file...
```
sudo gedit /etc/default/crda
```
and change..REGDOMAIN=US to REGDOMAIN=CA
be sure to use uppercase CA
save and close gedit...boot
then you can ...
```
cat /etc/default/crda
```
to verify your change..
good luck, I have no further suggestions.

---

### Post by student-n on 2016-04-17
Thanks a lot for your time today, even if the problem persist is appreciated all your help and suggestions, somewhere machines are limited sometimes, but not human willingness. Have a great night, I will continue checking to see.

;)

---

### Post by student-n on 2016-04-17
Thanks a lot for your time today, even if the problem persist is appreciated all your help and suggestions, somewhere machines are limited sometimes, but not human willingness. Have a great night, I will continue checking to see.

;)

---


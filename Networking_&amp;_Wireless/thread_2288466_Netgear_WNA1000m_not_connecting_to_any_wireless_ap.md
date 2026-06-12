---
title: "Netgear WNA1000m not connecting to any wireless ap"
date: 2015-07-27
forum: Networking &amp; Wireless
---

### Post by Anirudh_Agarkhed on 2015-07-27
Hello,
        I'm running Ubuntu 15.04, on a desktop with linux kernel 4.1.2 from the Vivid repositories. The netgear wireless adapter detects access points, but fails to connect to any of it. Earlier, on 3.19 generic linux kernel, the same issue existed, and i tried many things suggested but no results. I appreciate any advices given, thank you in advance!

---

### Post by Anirudh_Agarkhed on 2015-07-27
output for some commands suggested before to others to make some analysis of the problem

$lsusbBus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 05c6:6001 Qualcomm, Inc. 
Bus 004 Device 002: ID 05ac:12aa Apple, Inc. iPod Touch 5.Gen [A1421]
Bus 004 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 1bcf:0002 Sunplus Innovation Technology Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bc2:ab21 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lsmod | grep rtl
rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                73728  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              745472  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              552960  2 mac80211,rtlwifi

$ modinfo rtl8192cu | grep filename
filename:       /lib/modules/4.1.2-040102-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko

$ dmesg | grep -i rtl
[    2.086685] r8169 0000:03:00.0 eth0: RTL8168f/8111f at 0xffffc90000c84000, e0:3f:49:ad:24:07, XID 08000800 IRQ 33
[11236.239053] rtl8192cu: Chip version 0x10
[11236.320961] rtl8192cu: MAC address: 4c:60:de:5e:d9:a4
[11236.320966] rtl8192cu: Board Type 0
[11236.321201] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[11236.321263] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[11236.353347] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[11236.354043] usbcore: registered new interface driver rtl8192cu
[11236.379517] rtl8192cu: MAC auto ON okay!
[11236.413609] rtl8192cu: Tx queue select: 0x05
root@a-ajax:/home/temp# modinfo rtl8192cu | grep -e version -e 9041
srcversion:     EEFC5EA65F8D59F1253072F
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
vermagic:       4.1.2-040102-generic SMP mod_unload modversions 

$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth1      no wireless extensions.


eth2      no wireless extensions.


ham0      no wireless extensions.


lo        no wireless extensions.

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: FC:DD:55:09:B0:82
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-6 dBm  
                    Encryption key:on
                    ESSID:"a_ajax"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001971f176
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0006615F616A6178
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A001119FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD09001018020400040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by praseodym on 2015-07-27
Does LAN work to change the driver according to this

[https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-5-und-14-04-fuer-Kernel-3-11-3-13-und-3-16](https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-5-und-14-04-fuer-Kernel-3-11-3-13-und-3-16)

---

### Post by Anirudh_Agarkhed on 2015-07-28
> **praseodym said:**
> Does LAN work to change the driver according to this

[https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-5-und-14-04-fuer-Kernel-3-11-3-13-und-3-16](https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-5-und-14-04-fuer-Kernel-3-11-3-13-und-3-16)

I had tried this before on Linux kernel 3.19, but it hadn't worked. It seems to be working fine with kernel 4.1.2. Thanks for suggesting this, it's working fine for now!

---


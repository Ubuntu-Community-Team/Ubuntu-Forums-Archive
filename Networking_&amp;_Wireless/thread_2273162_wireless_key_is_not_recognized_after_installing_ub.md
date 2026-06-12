---
title: "wireless key is not recognized after installing ubuntu 14.04"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by emilio8 on 2015-04-11
Hello,

I installed ubuntu 14.04 on my Toshiba satellite (I had windows before) but now I can't connect to Wi-Fi network (only through ethernet cable). It keeps asking me for the password even though I write it correctly. The Wi-Fi security settings says: WPA & WPA2 Personal.
Any clue how can I solve this? Do you need any further info?
Thanks a lot!

---

### Post by praseodym on 2015-04-11
Hi,

please run the wireless-script from the sticky thread and show the outputs here.

Thx

---

### Post by emilio8 on 2015-04-11
Hello, this is what you meant? 
I didn't copied it all, but hope this is ok. It says the driver is disconnected... sorry I'm quite new on this.
Thanks!

##### kernel ############################

Linux 3.16.0-34-generic #45~14.04.1-Ubuntu SMP Tue Mar 24 11:14:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0724]
    Kernel driver in use: rtl8723ae

#### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b307 Chicony Electronics Co., Ltd 
Bus 001 Device 007: ID 24db:3261  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0930:021d Toshiba Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723ae              81799  0 
rtl8723_common         23361  1 rtl8723ae
rtl_pci                26690  1 rtl8723ae
rtlwifi                64255  2 rtl_pci,rtl8723ae
mac80211              652718  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              494362  2 mac80211,rtlwifi
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################
wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2260 (2.2 KB)  TX bytes:3100 (3.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ARRIS-2212:      Infra, <MAC 'ARRIS-2212' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

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

##### module infos ######################

[rtl8723ae]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     5FDB4D618B8E6F42C4EA3C8
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:55:71:9E:5C:6C:61:54:BE:06:25:D0:48:83:AE:41:1B:76:41:AD
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

##### module parameters #################

[rtl8723ae]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

##### dmesg #############################

[15196.124838] rtlwifi: wireless switch is on
[15198.765598] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---


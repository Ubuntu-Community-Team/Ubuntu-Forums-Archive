---
title: "Wifi works but Internet keeps dropping after about 10 minutes"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by dustin18 on 2015-01-22
My internet keeps dropping about every 10 minutes. I disconnect and reconnect and it works again. However, it's a big pain and it's one of the only reasons I keeping going back to the legacy OS. 

I'm brand new to Linux and Ubuntu. I've fixed some small things by myself so far but I can't seem to fix my internet connection. I've already read some of the other similar threads but I'm very much a noob. 

Please let me know what you want to me to type into the terminal. I'll paste the output. 

Many thanks in advance.

Edit: Also, it appears I might have two wireless adapters. One internal, and one USB adapter. I think i'm using the USB one now. Not sure if any of this matters.

---

### Post by dustin18 on 2015-01-23
Forgot to mention that I'm on Ubuntu 14.04 LTS. I'll post some info that might allow people to help me better. 

Here's the output after i enter "iwconfig" 

wlan1     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Home Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 2C:B0:5D:96:28:3B   
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: 0ff
          Power Management: off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

---

### Post by dustin18 on 2015-01-23
I've tried looking on the Additional Drivers tab to see if there were alternatives for my wireless card but it didn't list anything for it. 


Here's the output from ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:24:8c:06:b2:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:70111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6716180 (6.7 MB)  TX bytes:6716180 (6.7 MB)

wlan0     Link encap:Ethernet  HWaddr 4c:60:de:5d:80:f5  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4e60:deff:fe5d:80f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1843761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1593247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2421809053 (2.4 GB)  TX bytes:181040097 (181.0 MB)

wlan1     Link encap:Ethernet  HWaddr 00:22:5f:5b:51:a3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:27115 (27.1 KB)

---

### Post by wildmanne39 on 2015-01-23
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by dustin18 on 2015-01-23
[HR][/HR]Thanks for the reply! Pleae find the attached wireless info as you requested. (I hope I attached it correctly)

---

### Post by wildmanne39 on 2015-01-24
I am sorry but for some reason I can not open that file, which is very strange, could you please run the script again and post the new file.
Thanks

---

### Post by dustin18 on 2015-01-24
> **Wild Man said:**
> I am sorry but for some reason I can not open that file, which is very strange, could you please run the script again and post the new file.
Thanks

Sure thing. Ran the script again. Attached the wireless info.tar.gz. 

I'll also try pasting the wireless-info.txt below in code tags. 

```

########## wireless info START ##########

Report from: 24 Jan 2015 13:48 EST -0500

Booted last: 21 Jan 2015 03:28 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Asus IPIBL-LB Motherboard [103c:2a6f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 006: ID 0480:0202 Toshiba America Info. Systems, Inc. 
Bus 002 Device 005: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 003: ID 15a9:0004 Gemtek WUBR-177G [Ralink RT2571W]
Bus 002 Device 002: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              67723  0 
rt73usb                31580  0 
rtl_usb                18448  1 rtl8192cu
rt2x00usb              20742  1 rt73usb
rtlwifi                63475  2 rtl_usb,rtl8192cu
rt2x00lib              55307  2 rt73usb,rt2x00usb
rtl8192c_common        53172  1 rtl8192cu
mac80211              630669  5 rtl_usb,rtlwifi,rt2x00lib,rt2x00usb,rtl8192cu
cfg80211              484040  3 mac80211,rtlwifi,rt2x00lib
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
crc_itu_t              12707  2 rt73usb,firewire_core

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
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4e60:deff:fe5d:80f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2647876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2272483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3481416094 (3.4 GB)  TX bytes:252726447 (252.7 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:27115 (27.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan0     IEEE 802.11bgn  ESSID:"Home Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Home Network' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

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

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

- Device: wlan0  [Home Network] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Home Network:   Infra, <MAC 'Home Network' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2

  IPv4 Settings:
    Address:         192.168.1.4
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

[[/etc/NetworkManager/system-connections/NETGEAR88_EXT]] (600 root)
[connection] id=NETGEAR88_EXT | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR88_EXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Home Network]] (600 root)
[connection] id=Home Network | type=802-11-wireless
[802-11-wireless] ssid=Home Network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR88_EXT 1]] (600 root)
[connection] id=NETGEAR88_EXT 1 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR88_EXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Home Network 1]] (600 root)
[connection] id=Home Network 1 | type=802-11-wireless
[802-11-wireless] ssid=Home Network | mac-address=<MAC 'wlan1' [IF]>
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

wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     No scan results

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Home Network' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Home Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000141a2151204
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2E676CE01D91070679A9EF3
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rt73usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     66CCBB24DCA72AAD23E9588
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rtl_usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

[rt73usb]
nohwcrypt: N

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[253937.532040] wlan0: authentication with <MAC 'Home Network' [AC1]> timed out
[253938.372429] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[253938.396109] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[253938.500027] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 2/3)
[253938.604028] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 3/3)
[253938.708033] wlan0: authentication with <MAC 'Home Network' [AC1]> timed out
[253939.940523] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[253939.964449] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[253939.964490] wlan0: authenticated
[253939.968034] wlan0: associate with <MAC 'Home Network' [AC1]> (try 1/3)
[253940.072021] wlan0: associate with <MAC 'Home Network' [AC1]> (try 2/3)
[253940.176033] wlan0: associate with <MAC 'Home Network' [AC1]> (try 3/3)
[253940.280037] wlan0: association with <MAC 'Home Network' [AC1]> timed out
[253942.013003] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[253942.032458] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[253942.136063] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 2/3)
[253942.240478] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 3/3)
[253942.344037] wlan0: authentication with <MAC 'Home Network' [AC1]> timed out
[253953.800607] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[253953.824466] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[253953.928027] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 2/3)
[253954.032022] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 3/3)
[253954.136025] wlan0: authentication with <MAC 'Home Network' [AC1]> timed out
[253962.748480] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[253962.772475] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[253962.876036] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 2/3)
[253962.980035] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 3/3)
[253963.052166] wlan0: authenticated
[253963.056034] wlan0: associate with <MAC 'Home Network' [AC1]> (try 1/3)
[253963.160032] wlan0: associate with <MAC 'Home Network' [AC1]> (try 2/3)
[253963.264046] wlan0: associate with <MAC 'Home Network' [AC1]> (try 3/3)
[253963.293918] wlan0: RX AssocResp from <MAC 'Home Network' [AC1]> (capab=0x431 status=0 aid=5)
[253963.293980] wlan0: associated
[254518.272363] wlan0: deauthenticating from <MAC 'Home Network' [AC1]> by local choice (reason=3)
[254522.765968] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[254522.784067] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[254522.848720] wlan0: authenticated
[254522.852152] wlan0: associate with <MAC 'Home Network' [AC1]> (try 1/3)
[254522.954261] wlan0: RX AssocResp from <MAC 'Home Network' [AC1]> (capab=0x431 status=0 aid=5)
[254522.954308] wlan0: associated
[256437.454592] wlan0: Connection to AP <MAC 'Home Network' [AC1]> lost
[256438.284518] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[256438.308542] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[256438.323103] wlan0: authenticated
[256438.324033] wlan0: associate with <MAC 'Home Network' [AC1]> (try 1/3)
[256438.330979] wlan0: RX AssocResp from <MAC 'Home Network' [AC1]> (capab=0x431 status=0 aid=5)
[256438.331034] wlan0: associated
[256465.509599] wlan0: Connection to AP <MAC 'Home Network' [AC1]> lost
[256466.364534] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[256466.388561] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[256466.409866] wlan0: authenticated
[256466.412051] wlan0: associate with <MAC 'Home Network' [AC1]> (try 1/3)
[256466.419372] wlan0: RX AssocResp from <MAC 'Home Network' [AC1]> (capab=0x431 status=0 aid=5)
[256466.419428] wlan0: associated
[277658.468731] wlan0: deauthenticating from <MAC 'Home Network' [AC1]> by local choice (reason=3)
[277667.651290] wlan0: authenticate with <MAC 'Home Network' [AC1]>
[277667.670871] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 1/3)
[277667.772019] wlan0: send auth to <MAC 'Home Network' [AC1]> (try 2/3)
[277667.805051] wlan0: authenticated
[277667.808026] wlan0: associate with <MAC 'Home Network' [AC1]> (try 1/3)
[277667.912046] wlan0: associate with <MAC 'Home Network' [AC1]> (try 2/3)
[277667.996557] wlan0: RX AssocResp from <MAC 'Home Network' [AC1]> (capab=0x431 status=0 aid=5)
[277667.996636] wlan0: associated

########## wireless info END ############

```

---

### Post by wildmanne39 on 2015-01-24
You have two usb devices plugged in at the same time, shut down your computer and please unplug the one that uses the ```
rtl8192cu
``` driver, then boot up and see if it connects if not do:
```
echo "options rt73usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt73usb.conf
sudo modprobe -rfv rt73usb
sudo modprobe -v rt73usb
```if it still does not connect then post a new file from the script so we can look at the configuration with this driver.
Thanks

---

### Post by dustin18 on 2015-01-25
I did both steps. After I ran the three lines of commands above it still didn't work so I turned off the power to the modem and plugged it back in. Now nobody has internet access in the house. The modem lights for wireless and the internet appear as if they are working but nobody can get online now. I'm typing this from my phone. Any chance I messed up the wireless network with these terminal commands? 

Also, now that we don't have internet, I couldn't run the wireless script again using your instructions. I still have the script but don't know the commands to run it. Any help is greatly appreciated.

---

### Post by wildmanne39 on 2015-01-25
No the commands did not change your router settings, turning the power off to your router/modem changed the settings.

To run the script again do:
```
cd ~
./wireless_script
```
Thanks

---

### Post by dustin18 on 2015-01-27
Thanks for having patience with me. 

Seems we had a problem with our ISP for a couple days. Internet is back up now but I'm having the same problem. Last night I could get a sporadic internet connection on Ubuntu but today it won't connect so I dual booted into Vista to post this. 

As you said, it appears i have two USB devices plugged in according to the Network Manager in the top right corner, however, when I unplug the little Netgear USB wireless thing, both disappear and I have zero wireless options or networks to connect to. I'm baffled as to why/how I have two USB wireless cards because I clearly only see one plugged into the computer. 

I ran the script without the USB plugged in after running the three lines of commands you told me to run. This time it only gave me the info as .txt. See results below. 

```

########## wireless info START ##########

Report from: 27 Jan 2015 13:59 EST -0500

Booted last: 27 Jan 2015 13:56 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Asus IPIBL-LB Motherboard [103c:2a6f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 0480:0202 Toshiba America Info. Systems, Inc. 
Bus 002 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 15a9:0004 Gemtek WUBR-177G [Ralink RT2571W]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt73usb                31580  0 
rt2x00usb              20742  1 rt73usb
rt2x00lib              55307  2 rt73usb,rt2x00usb
mac80211              630669  2 rt2x00lib,rt2x00usb
cfg80211              484040  2 mac80211,rt2x00lib
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
crc_itu_t              12707  2 rt73usb,firewire_core

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

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

[[/etc/NetworkManager/system-connections/NETGEAR88_EXT]] (600 root)
[connection] id=NETGEAR88_EXT | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR88_EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Home Network]] (600 root)
[connection] id=Home Network | type=802-11-wireless
[802-11-wireless] ssid=Home Network | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR88_EXT 1]] (600 root)
[connection] id=NETGEAR88_EXT 1 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR88_EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Living Room TV]] (600 root)
[connection] id=Living Room TV | type=802-11-wireless
[802-11-wireless] ssid=Living Room TV | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Home Network 1]] (600 root)
[connection] id=Home Network 1 | type=802-11-wireless
[802-11-wireless] ssid=Home Network | mac-address=<MAC 'wlan1' [IF]>
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

wlan1     14 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     No scan results

##### module infos ######################

[rt73usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     66CCBB24DCA72AAD23E9588
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt73usb]
nohwcrypt: Y

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rt73usb.conf]
options rt73usb nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   22.468661] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   22.488217] systemd-udevd[351]: renamed network interface wlan0 to wlan1
[   25.819358] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   25.903181] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   25.993227] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[  166.864475] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[  166.888326] systemd-udevd[2484]: renamed network interface wlan0 to wlan1
[  166.891937] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[  166.891969] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[  166.982698] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)

########## wireless info END ############

```

---

### Post by dustin18 on 2015-02-04
> **Wild Man said:**
> No the commands did not change your router settings, turning the power off to your router/modem changed the settings.

To run the script again do:
```
cd ~
./wireless_script
```
Thanks

```

########## wireless info START ##########

Report from: 27 Jan 2015 13:59 EST -0500

Booted last: 27 Jan 2015 13:56 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Asus IPIBL-LB Motherboard [103c:2a6f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 0480:0202 Toshiba America Info. Systems, Inc. 
Bus 002 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 15a9:0004 Gemtek WUBR-177G [Ralink RT2571W]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt73usb                31580  0 
rt2x00usb              20742  1 rt73usb
rt2x00lib              55307  2 rt73usb,rt2x00usb
mac80211              630669  2 rt2x00lib,rt2x00usb
cfg80211              484040  2 mac80211,rt2x00lib
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
crc_itu_t              12707  2 rt73usb,firewire_core

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

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

[[/etc/NetworkManager/system-connections/NETGEAR88_EXT]] (600 root)
[connection] id=NETGEAR88_EXT | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR88_EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Home Network]] (600 root)
[connection] id=Home Network | type=802-11-wireless
[802-11-wireless] ssid=Home Network | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR88_EXT 1]] (600 root)
[connection] id=NETGEAR88_EXT 1 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR88_EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Living Room TV]] (600 root)
[connection] id=Living Room TV | type=802-11-wireless
[802-11-wireless] ssid=Living Room TV | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Home Network 1]] (600 root)
[connection] id=Home Network 1 | type=802-11-wireless
[802-11-wireless] ssid=Home Network | mac-address=<MAC 'wlan1' [IF]>
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

wlan1     14 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     No scan results

##### module infos ######################

[rt73usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     66CCBB24DCA72AAD23E9588
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt73usb]
nohwcrypt: Y

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rt73usb.conf]
options rt73usb nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   22.468661] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   22.488217] systemd-udevd[351]: renamed network interface wlan0 to wlan1
[   25.819358] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   25.903181] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   25.993227] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[  166.864475] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[  166.888326] systemd-udevd[2484]: renamed network interface wlan0 to wlan1
[  166.891937] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[  166.891969] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[  166.982698] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)

########## wireless info END ############

```

---

### Post by dustin18 on 2015-02-10
Thanks to some anons over at 8chan, I seem to have resolved my wireless issue. I can't say I'm impressed with this forum though. But I am grateful to the one guy who tried helping me before he went missing. 

In case my experience can help others, I'll post the solution below. 
Disclaimer: Take the advice below at your own peril. I only have two weeks of Linux experience under my belt. 

Link to these full instructions: 
[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7) 

1. First you need to determine the exact chipset. Like this:

Launch a terminal window.

Use copy/paste to transfer the following line into the terminal:

lsusb

Press Enter.

Now you should see approximately the following output (example from my own computer):

Bus 002 Device 003: ID 0bda:8176 Realtek Semiconductor Corp.

or:

Bus 002 Device 004: ID 0bda:8178 Realtek Semiconductor Corp.

or:

Bus 002 Device 007: ID 0bda:818b Realtek Semiconductor Corp.

For these chipsets you'll find a solution below, which differs for every chipset.

Realtek RTL8188CUS en RTL8192CU chipsets (0bda:8176 en 0bda:8178)

2. Wireless Realtek chipsets that are running on the default rtl8192cu driver, often loses connection and run below their proper speed. That's because of a bug in the rtl8192cu driver.

For instance, this Realtek chipset is present in the Medion MD 86498 USB wireless dongle. The chipsets involved, are the RTL8192CU and the RTL8188CU.

Luckily there's a solution that'll make such a chipset run stable and fast, namely replacing the defective driver by a better one. This solution is necessary for the following operating systems:
- Ubuntu 14.04
- Linux Mint 17.1
- Ubuntu 12.04
- Linux Mint 13

This is how to do it:


1. First check whether the buggy driver rtl8192cu is active in your operating system:

Launch a terminal window.
(You can launch a terminal window like this: *Click*)

Use copy/paste to transfer the following line into the terminal:

lsmod | grep rtl

Press Enter.

When you see one or more times rtl8192cu in the terminal output, then it's active. In that case proceed with step 2.


2. Disconnect your wireless connection (unplug the USB adapter that contains the Realtek chipset), and temporarily connect to the internet by means of an ethernet cable (or by means of another wireless chipset that does function well).


Intermediary step, only necessary for Linux Mint 17 and 17.1: install the latest kernel within the 3.13 series, in the following way (item 1.2.3, left column)


3. Now install some applications for building the right driver:

Launch a terminal window.
(You can launch a terminal window like this: *Click*)

Type (use copy/paste):

sudo apt-get install linux-headers-generic build-essential dkms git

Press Enter and submit your password. Please note that the password will remain invisible, not even asterisks will show, which is normal.

Wait until the installation has completed.


4. Now download the source code of the right driver as follows. Copy and paste the following command line into the terminal:

git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)

Press Enter.

5. Set it up as a DKMS module:

Copy and paste into the terminal:

sudo dkms add ./rtl8192cu-fixes

Press Enter and if prompted, submit your password. Please note that the password will remain invisible, not even asterisks will show, which is normal.


6. Build and install the new driver:

Copy and paste into the terminal:

sudo dkms install 8192cu/1.9

Press Enter.


7. Refresh the module list:

Copy and paste into the terminal:

sudo depmod -a

Press Enter.


8. Blacklist the faulty driver:

Copy and paste into the terminal:

sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/

Press Enter.

9. Reboot your computer.


10. The problem should now be solved: disconnect the temporary ethernet cable and insert the Realtek device again.

With the following terminal command you can check whether the right driver is active now (copy and paste it into the terminal):

lsmod | grep 8192

Press Enter.

In the terminal output you should see that the new driver 8192cu is active. You should see no mention anymore of the old driver rtl8192cu.

Note: a possibly surprising side effect might be, that the light on your wireless card is blinking constantly now. That's normal: the light is blinking whenever data are being sent or received.

Troubleshooting

There is a known issue with power management on some hardware. If your WiFi connection drops after a few minutes, install the following module setting file to disable power management in your WiFi interface:

sudo cp ./rtl8192cu-fixes/8192cu-disable-power-management.conf /etc/modprobe.d/

And then reboot.

---

### Post by bret2 on 2015-04-15
@dustin18 -- Thanks huge for posting that github fix. Works like a charm for me with an Edimax EW-7811Un wireless USB adapter on Linux Mint 17.1.

---

### Post by mic4 on 2016-03-29
@dustin18 I created an account just to show my appreciation for your detailed guide here. I was having the exact same issue. Followed your guide on a fresh installation of Mint with an EW-7811Un.. restarted.. and am now zooming around with no connectivity issues whatsoever. You're the man!

---

### Post by wildmanne39 on 2016-03-30
Please do not post in old threads.
Thanks

---


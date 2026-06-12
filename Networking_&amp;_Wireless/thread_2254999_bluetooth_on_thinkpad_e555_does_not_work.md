---
title: "bluetooth on thinkpad e555 does not work"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by bejo3 on 2014-12-01
Hello Ubuntuforums-user. 

Recently I posted a thread concerning my wifi of a lenovo thinkpad e555 (realtek hardware: rtl8723be), which did not work when using elementary os.

[http://ubuntuforums.org/showthread.php?t=2254511](http://ubuntuforums.org/showthread.php?t=2254511)

 The thread could be solved successfully! My wifi is working perfectly. 

Now It seems as if my bluetooth, which comes with the same hardware, does not work. Neither can I see foreign devices, nor can my computer be seen on them. 

Just in case, somebody wants to know about the actual output of the wireless-script:
```


########## wireless info START ##########

Report from: 01 Dec 2014 19:20 CET +0100

Booted last: 01 Dec 2014 18:19 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Luna
Release:    0.2.1
Codename:    luna

##### kernel ############################

Linux 3.2.0-72-generic #107-Ubuntu SMP Thu Nov 6 14:24:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f2:b444 Chicony Electronics Co., Ltd 
Bus 004 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             120801  0 
rtl8723_common         23712  1 rtl8723be
rtl_pci                35613  1 rtl8723be
rtlwifi                91070  2 rtl8723be,rtl_pci
mac80211              614800  3 rtl8723be,rtl_pci,rtlwifi
cfg80211              599648  2 rtlwifi,mac80211
btcoexist              50313  1 rtl8723be
compat                 37460  6 rtl8723be,rtl_pci,rtlwifi,mac80211,cfg80211,btcoexist
wmi                    19256  0 

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
          Interrupt:86 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::ee0e:c4ff:fe54:9367/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35769963 (35.7 MB)  TX bytes:3994394 (3.9 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Heribert"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Heribert' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:389   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Heribert] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WLAN-79AC32:     Infra, <MAC 'WLAN-79AC32' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    WLAN-79AC329dad6e: Infra, <MAC 'WLAN-79AC329dad6e' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *Heribert:       Infra, <MAC 'Heribert' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    FRITZ!Box 7362 SL: Infra, <MAC 'FRITZ!Box 7362 SL' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2

  IPv4 Settings:
    Address:         192.168.2.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Heribert]] (600 root)
[connection] id=Heribert | type=802-11-wireless
[802-11-wireless] ssid=Heribert | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

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

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Heribert' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"Heribert"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000171870f90ee
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WLAN-79AC32' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WLAN-79AC32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d36eb0abc4
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FRITZ!Box 7362 SL' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000058506c67990
                    Extra: Last beacon: 12ms ago
                   eth0      Interface doesn't support scanning.

                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'WLAN-79AC329dad6e' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WLAN-79AC329dad6e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d36b3e04e1
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2A841709EF6A38E777CCD34
depends:        mac80211,rtlwifi,compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.2.0-72-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AEDBFD2C2F64D9D545BF951
depends:        mac80211,compat,cfg80211
vermagic:       3.2.0-72-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.2.0-72-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
srcversion:     15791DA6391E3692639BAB5
depends:        cfg80211,compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.2.0-72-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16-0-g19583ca) using backports v3.16-1-0-g87df966
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     67813FD63FE30A8DC22E6B7
depends:        compat
vermagic:       3.2.0-72-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
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

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist brcmfmac
blacklist ssb
blacklist bcma
blacklist bcm43xx

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:03.1/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:03.3/0000:03:00.0 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    5.512932] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    5.513582] rtlwifi: wireless switch is on
[    6.019134] ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    8.465565] wlan0: authenticate with <MAC 'Heribert' [AC1]>
[    8.480510] wlan0: send auth to <MAC 'Heribert' [AC1]> (try 1/3)
[    8.484096] wlan0: authenticated
[    8.488039] wlan0: associate with <MAC 'Heribert' [AC1]> (try 1/3)
[    8.506952] wlan0: RX AssocResp from <MAC 'Heribert' [AC1]> (capab=0x431 status=0 aid=1)
[    8.507155] wlan0: associated
[    8.507969] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.040492] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.936168] wlan0: no IPv6 routers present
[ 1094.191403] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1094.191552] wlan0: Connection to AP <MAC 'Heribert' [AC1]> lost
[ 1095.629838] wlan0: authenticate with <MAC 'Heribert' [AC1]>
[ 1095.649028] wlan0: send auth to <MAC 'Heribert' [AC1]> (try 1/3)
[ 1095.651238] wlan0: authenticated
[ 1095.652086] wlan0: associate with <MAC 'Heribert' [AC1]> (try 1/3)
[ 1095.671152] wlan0: RX AssocResp from <MAC 'Heribert' [AC1]> (capab=0x431 status=0 aid=1)
[ 1095.671317] wlan0: associated

########## wireless info END ############


```


If anybody can help me with this, i would be glad to read an answer. 

Thank you in advance. 
Best regards, Johannes.

---

### Post by bejo3 on 2014-12-04
Hello everybody. 

Unfortunately nobody could help me with my thread until this point - at least I did not get an answer. 
So I installed the newest plain ubuntu version 14.04 and removed eOS. Wifi worked right from scratch. I experienced a sudden loss of connection, but I hope that was do to my usage of the live cd before I fully installed it. I updated and upgraded the distribution. 
But still, my bluetooth is not working. What can it possibly be? Is my wifi and bluetooth hardware too new? 

Here is what the wireless script throws out: 

```

########## wireless info START ##########

Report from: 04 Dec 2014 20:33 CET +0100

Booted last: 04 Dec 2014 20:21 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b444 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11412 (11.4 KB)  TX bytes:10741 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::ee0e:c4ff:fe54:9367/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70943556 (70.9 MB)  TX bytes:2609511 (2.6 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Heribert"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Heribert' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1236   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Heribert] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WLAN-79AC329dad6e: Infra, <MAC 'WLAN-79AC329dad6e' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    WLAN-79AC32:     Infra, <MAC 'WLAN-79AC32' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    *Heribert:       Infra, <MAC 'Heribert' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Heribert]] (600 root)
[connection] id=Heribert | type=802-11-wireless
[802-11-wireless] ssid=Heribert | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

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

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Heribert' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Heribert"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001aee60e1b1f
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WLAN-79AC329dad6e' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WLAN-79AC329dad6e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000310ca2f89c7
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WLAN-79AC32' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WLAN-79AC32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000310cdefefae
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.750615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    5.635080] wlan0: authenticate with <MAC 'Heribert' [AC1]>
[    5.645246] wlan0: send auth to <MAC 'Heribert' [AC1]> (try 1/3)
[    5.646814] wlan0: authenticated
[    5.648164] wlan0: associate with <MAC 'Heribert' [AC1]> (try 1/3)
[    5.667183] wlan0: RX AssocResp from <MAC 'Heribert' [AC1]> (capab=0x431 status=0 aid=2)
[    5.667333] wlan0: associated
[    5.667351] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    7.483578] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############


```

Probably somebody can help me with this information now. I would be very glad to receive some advice. 

Thanks in advance. Best regards, Johannes. 

[code]

---

### Post by jeremy31 on 2014-12-04
[https://github.com/lwfinger/rtl8723au/issues/1](https://github.com/lwfinger/rtl8723au/issues/1)

Might be the only hope to get bluetooth going

---

### Post by bejo3 on 2014-12-09
Hi everybody. 

Nothing that I tryed worked out in here. I gave back the machine to the store, where I bought it. Apparently it is not that easy to get a Linux distribution running on notebooks. I'll have to check which machine suits my needs best and works with a nice linux distribution. 

This thread is not solved - but it can be ended. 

Many thanks to all who helped me here. Bye, Johannes.

---


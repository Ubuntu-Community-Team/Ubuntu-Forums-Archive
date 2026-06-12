---
title: "Ubuntu 12.04 LTS 3.11 unstable wifi"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by jimbo6 on 2014-03-19
Running Ubuntu 12.04 LTS kernel 3.11 and experiencing very unstable wifi. Disconnecting, weak signal, strong signal, mid strength and disconnecting within a minute. 

Hardware: Lenovo W530 using ThinkPad 1x1 b/g/n wifi card.

Recently updated to kernel 3.11 and reinstalled ndiswrapper.
 
Wifi was erratic before this, but not quite as erratic (ie some days will connect, some days not). 

Running Wicd.

I'm new to Linux, and require instructions on how to display more relevant diagnostic data.

ran lspci and got:

 ```
Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

(run via wifi)

Code:

```

########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux -ThinkPad-W530 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 


##### PCMCIA Card Info #####




##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback




##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BAZD_MEG_LOCAL_EXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 32:46:9A:FF:E2:ED   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:49   Missed beacon:0




##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #####


nameserver 192.168.1.1


##### nm-tool #####


##### NetworkManager.state #####




##### NetworkManager.conf #####




##### iwlist #####
```

code:

[COLOR=#333333][FONT=UbuntuRegular]iwconfig:[/FONT][/COLOR]

```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```

code:

[COLOR=#333333][FONT=UbuntuRegular]lshw:
[/FONT][/COLOR]

```
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:83:5a:fd
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f3a00000-f3a1ffff memory:f3a3b000-f3a3bfff ioport:7080(size=32)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: a4:17:31:f7:5d:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.11.0-18-generic firmware=N/A ip=192.168.1.129 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:4000(size=256) memory:f3000000-f3003fff
```

---

### Post by varunendra on 2014-03-19
Welcome to the forums jimbo6!

Please follow the instructions in this post to try a newer version of the driver : [http://ubuntuforums.org/showpost.php?p=12926946](http://ubuntuforums.org/showpost.php?p=12926946)

Let us know how it performs for you.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by jimbo6 on 2014-03-19
Thanks for the reply, Varun.

Tried the running [COLOR=#000000]3.12.8-1 and 3.13.2-1. Wifi signal still fluctuating and dropping as before.[/COLOR]

When I ran sudo make install I received "cant' read private key" logs.

I also don't understand how to do this:
[COLOR=#000000]*Oh, and please try the driver parameters with this driver as well. Some of them may be necessary sometimes.*[/COLOR]

---

### Post by jimbo6 on 2014-03-20
I ran:

```


sudo modprobe -rv rtl8192ce

sudo modprobe -v rtl8192ce swenc=Y


```

Signal strength still fluctuating and connection dropping out.

---

### Post by jimbo6 on 2014-03-20
Wireless script:

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux ThinkPad-W530 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 


##### PCMCIA Card Info #####


##### rfkill #####


1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BAZD_MEG_LOCAL_EXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #####


nameserver 192.168.1.1


##### nm-tool #####


##### NetworkManager.state #####


##### NetworkManager.conf #####


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"BAZD_MEG_LOCAL_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013be82f2f
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001242415A445F4D45475F4C4F43414C5F455854
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DDA50050F204104A0001101044000102103B000103104700100000000000001000000030469AFFE2ED102100044E54475210230009574E3230303052505410240001311042001253657269616C204E756D62657220486572651054000800060050F20400011011001B574E3230303052505428576972656C6573732041502D322E344729100800020086103C000103104900140024E26002000101600000020001600100020001


##### iwlist channel #####


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


##### lsmod #####


rtl8192ce              79730  0 
rtl8192c_common        70787  1 rtl8192ce
rtl_pci                35486  1 rtl8192ce
rtlwifi                90430  2 rtl8192ce,rtl_pci
mac80211              536549  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              496237  2 rtlwifi,mac80211
compat                 13893  4 rtl8192ce,rtlwifi,mac80211,cfg80211


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     07DEE99EA4ECF0763963EDC
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,compat,mac80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     968F4A50B796AC16999321D
depends:        mac80211,rtlwifi
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     470515CF947D1ACA5BD128D
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


##### modules #####


lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x05ac:0x1292 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    2.587218] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[    2.618443] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.642391] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.645339] rtlwifi: wireless switch is on
[    2.829416] Bluetooth: can't load firmware, may not work correctly
[    7.649821] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    7.881534] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.739347] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.860520] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.775703] wlan0: authenticate with <MAC address removed>
[   20.785854] wlan0: send auth to <MAC address removed> (try 1/3)
[   20.787386] wlan0: authenticated
[   20.791450] wlan0: associate with <MAC address removed> (try 1/3)
[   20.795447] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   20.795585] wlan0: associated
[   20.795595] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1554.336678] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1554.336728] wlan0: Connection to AP <MAC address removed> lost
[ 1555.658860] wlan0: authenticate with <MAC address removed>
[ 1555.678745] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1555.681954] wlan0: authenticated
[ 1555.682319] wlan0: associate with <MAC address removed> (try 1/3)
[ 1555.686397] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1555.686551] wlan0: associated
[ 1627.057866] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1627.057923] wlan0: Connection to AP <MAC address removed> lost
[ 1628.002805] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1629.018182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1630.494601] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1631.632121] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1633.763561] wlan0: authenticate with <MAC address removed>
[ 1633.773771] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1633.775924] wlan0: authenticated
[ 1633.779184] wlan0: associate with <MAC address removed> (try 1/3)
[ 1633.785493] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1633.785640] wlan0: associated
[ 1633.785680] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1748.044196] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1748.044228] wlan0: Connection to AP <MAC address removed> lost
[ 1749.379121] wlan0: authenticate with <MAC address removed>
[ 1749.398956] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1749.400458] wlan0: authenticated
[ 1749.402565] wlan0: associate with <MAC address removed> (try 1/3)
[ 1749.406642] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1749.406803] wlan0: associated
[ 1808.769814] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1808.769865] wlan0: Connection to AP <MAC address removed> lost
[ 1810.104468] wlan0: authenticate with <MAC address removed>
[ 1810.124460] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1810.125996] wlan0: authenticated
[ 1810.128150] wlan0: associate with <MAC address removed> (try 1/3)
[ 1810.136821] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1810.136961] wlan0: associated
[ 1875.495525] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1875.495559] wlan0: Connection to AP <MAC address removed> lost
[ 1876.587138] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1877.629149] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1879.135516] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1880.278221] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1882.412478] wlan0: authenticate with <MAC address removed>
[ 1882.422733] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1882.524161] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1882.526965] wlan0: authenticated
[ 1882.528238] wlan0: associate with <MAC address removed> (try 1/3)
[ 1882.532249] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1882.532426] wlan0: associated
[ 1882.532484] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1962.503812] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1962.503862] wlan0: Connection to AP <MAC address removed> lost
[ 1963.834184] wlan0: authenticate with <MAC address removed>
[ 1963.854131] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1963.857188] wlan0: authenticated
[ 1963.857724] wlan0: associate with <MAC address removed> (try 1/3)
[ 1963.861668] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1963.861810] wlan0: associated
[ 1963.909569] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1964.317407] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2791.608520] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2800.689365] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2801.835049] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2803.958655] wlan0: authenticate with <MAC address removed>
[ 2803.968858] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2803.970978] wlan0: authenticated
[ 2803.973975] wlan0: associate with <MAC address removed> (try 1/3)
[ 2803.980525] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2803.980674] wlan0: associated
[ 2803.980712] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2890.126124] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 2890.126159] wlan0: Connection to AP <MAC address removed> lost
[ 2891.272505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3348.644068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3350.175857] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3351.317332] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3353.444730] wlan0: authenticate with <MAC address removed>
[ 3353.454971] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3353.456716] wlan0: authenticated
[ 3353.460316] wlan0: associate with <MAC address removed> (try 1/3)
[ 3353.464328] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3353.464465] wlan0: associated
[ 3353.464497] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3365.648384] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3488.984413] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3499.449049] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3500.614493] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3502.745997] wlan0: authenticate with <MAC address removed>
[ 3502.756254] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3502.758705] wlan0: authenticated
[ 3502.761344] wlan0: associate with <MAC address removed> (try 1/3)
[ 3502.765553] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3502.765698] wlan0: associated
[ 3502.765737] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3592.891083] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 3592.891110] wlan0: Connection to AP <MAC address removed> lost
[ 3594.225342] wlan0: authenticate with <MAC address removed>
[ 3594.245158] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3594.250197] wlan0: authenticated
[ 3594.252737] wlan0: associate with <MAC address removed> (try 1/3)
[ 3594.260661] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3594.260873] wlan0: associated
[ 3689.706065] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 3689.706096] wlan0: Connection to AP <MAC address removed> lost
[ 3691.029206] wlan0: authenticate with <MAC address removed>
[ 3691.049082] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3691.055070] wlan0: authenticated
[ 3691.056782] wlan0: associate with <MAC address removed> (try 1/3)
[ 3691.060920] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 3691.061071] wlan0: associated
[ 3782.485112] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 3782.485167] wlan0: Connection to AP <MAC address removed> lost
[ 3783.432226] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4118.105092] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4122.494935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4123.629360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4125.772114] wlan0: authenticate with <MAC address removed>
[ 4125.782324] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4125.784790] wlan0: authenticated
[ 4125.787468] wlan0: associate with <MAC address removed> (try 1/3)
[ 4125.791434] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4125.791581] wlan0: associated
[ 4125.791616] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4235.985525] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 4235.985577] wlan0: Connection to AP <MAC address removed> lost
[ 4237.321520] wlan0: authenticate with <MAC address removed>
[ 4237.340520] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4237.342086] wlan0: authenticated
[ 4237.344175] wlan0: associate with <MAC address removed> (try 1/3)
[ 4237.348254] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4237.348402] wlan0: associated
[ 4382.956697] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 4382.956750] wlan0: Connection to AP <MAC address removed> lost
[ 4384.595711] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4527.151982] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4528.652846] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4529.810550] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4531.949995] wlan0: authenticate with <MAC address removed>
[ 4531.960248] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4531.962984] wlan0: authenticated
[ 4531.965351] wlan0: associate with <MAC address removed> (try 1/3)
[ 4531.969367] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4531.969528] wlan0: associated
[ 4531.969568] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4670.256942] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 4670.256951] wlan0: Connection to AP <MAC address removed> lost
[ 4671.600131] wlan0: authenticate with <MAC address removed>
[ 4671.620030] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4671.723792] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4671.731087] wlan0: authenticated
[ 4671.731725] wlan0: associate with <MAC address removed> (try 1/3)
[ 4671.735318] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4671.735474] wlan0: associated
[ 4805.197203] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 4805.197258] wlan0: Connection to AP <MAC address removed> lost
[ 4806.419217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5088.413092] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5089.873689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5090.991231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5093.134435] wlan0: authenticate with <MAC address removed>
[ 5093.144678] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5093.146407] wlan0: authenticated
[ 5093.150027] wlan0: associate with <MAC address removed> (try 1/3)
[ 5093.155058] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 5093.155204] wlan0: associated
[ 5093.155237] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6148.393970] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 6148.393995] wlan0: Connection to AP <MAC address removed> lost
[ 6149.740828] wlan0: authenticate with <MAC address removed>
[ 6149.760903] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6149.763431] wlan0: authenticated
[ 6149.764606] wlan0: associate with <MAC address removed> (try 1/3)
[ 6149.773874] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 6149.774018] wlan0: associated
[ 7138.100568] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 7138.100591] wlan0: Connection to AP <MAC address removed> lost
[ 7139.423670] wlan0: authenticate with <MAC address removed>
[ 7139.443678] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7139.445112] wlan0: authenticated
[ 7139.447174] wlan0: associate with <MAC address removed> (try 1/3)
[ 7139.450846] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 7139.450989] wlan0: associated
[ 7325.192411] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 7325.192435] wlan0: Connection to AP <MAC address removed> lost
[ 7326.868353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9154.674336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9156.170150] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9157.315613] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9159.455081] wlan0: authenticate with <MAC address removed>
[ 9159.465292] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9159.470370] wlan0: authenticated
[ 9159.470641] wlan0: associate with <MAC address removed> (try 1/3)
[ 9159.474642] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9159.474802] wlan0: associated
[ 9159.474847] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9303.786835] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 9303.786890] wlan0: Connection to AP <MAC address removed> lost
[ 9304.846512] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9370.092652] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9371.655605] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9372.773971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9374.908429] wlan0: authenticate with <MAC address removed>
[ 9374.918644] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9374.921960] wlan0: authenticated
[ 9374.923915] wlan0: associate with <MAC address removed> (try 1/3)
[ 9374.927916] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9374.928053] wlan0: associated
[ 9374.928083] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9376.446918] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9453.818870] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9456.865184] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9457.980694] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9460.102140] wlan0: authenticate with <MAC address removed>
[ 9460.112378] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9460.114219] wlan0: authenticated
[ 9460.117575] wlan0: associate with <MAC address removed> (try 1/3)
[ 9460.124110] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9460.124260] wlan0: associated
[ 9460.124299] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9758.935792] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 9758.935813] wlan0: Connection to AP <MAC address removed> lost
[ 9760.257745] wlan0: authenticate with <MAC address removed>
[ 9760.277759] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9760.279166] wlan0: authenticated
[ 9760.281395] wlan0: associate with <MAC address removed> (try 1/3)
[ 9760.285351] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9760.285508] wlan0: associated
[ 9777.831275] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9846.675616] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[ 9846.685481] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 9846.685644] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 9846.685849] rtlwifi: wireless switch is on
[ 9856.807234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9861.450713] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9862.534353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9865.480018] wlan0: authenticate with <MAC address removed>
[ 9865.490200] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9865.591922] wlan0: send auth to <MAC address removed> (try 2/3)
[ 9865.593452] wlan0: authenticated
[ 9865.595939] wlan0: associate with <MAC address removed> (try 1/3)
[ 9865.599917] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9865.600071] wlan0: associated
[ 9865.600110] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9986.926370] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 9986.926396] wlan0: Connection to AP <MAC address removed> lost
[ 9988.160948] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9989.193727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9990.751582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9991.885367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9994.024580] wlan0: authenticate with <MAC address removed>
[ 9994.034775] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9994.037778] wlan0: authenticated
[ 9994.040163] wlan0: associate with <MAC address removed> (try 1/3)
[ 9994.043769] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9994.043905] wlan0: associated
[ 9994.043933] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10198.541692] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[10198.541725] wlan0: Connection to AP <MAC address removed> lost
[10199.872750] wlan0: authenticate with <MAC address removed>
[10199.892735] wlan0: send auth to <MAC address removed> (try 1/3)
[10199.895600] wlan0: authenticated
[10199.896319] wlan0: associate with <MAC address removed> (try 1/3)
[10199.900432] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[10199.900583] wlan0: associated
[10572.241796] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[10572.241829] wlan0: Connection to AP <MAC address removed> lost
[10573.559988] wlan0: authenticate with <MAC address removed>
[10573.579862] wlan0: send auth to <MAC address removed> (try 1/3)
[10573.582081] wlan0: authenticated
[10573.583439] wlan0: associate with <MAC address removed> (try 1/3)
[10573.587514] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[10573.587666] wlan0: associated


########## wireless info END ############


```

and route -n:

```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
 
```
PING

```


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=254 time=5.56 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=254 time=6.11 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=254 time=10.8 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=254 time=7.23 ms


--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 5.563/7.442/10.857/2.063 ms


```

---

### Post by slooksterpsv on 2014-03-20
How far away is your computer from your wireless router? Are there any walls, microwaves, phones, etc. in the way? If you have an Android phone, download WiFi Analyzer from the Google Play Store and look for your Wifi network, the channel its on and what's around it that may be on the same channel. The app can also tell you a better channel for your wifi to be on.

---

### Post by jimbo6 on 2014-03-20
Hi slooksterpsv,

It's connected via a WN2000RPT extender. 

I encountered a booting error (scrolling text then lock up) and resolved it by upgrading to from 12.04 LTS 3.5 to 12.04 LTS 3.11 and updating the ndiswrapper. The booting error was encountered about two or three weeks ago after a system update on 12.04 LTS 3.5.

Prior to this, I hadn't encountered significant wifi issues (although it occasionally required disconnecting and reconnecting the router/extender). 

My Windows 7 partition encounters no problem with wifi (used in the same location) and has very smooth video calling with skype - which with my Ubuntu partition has always been erratic.

So I don't think it has much to do with the signal impediments, although the removal of a wall or two would certainly increase signal strength. Because I'm using an extender, the router dictates what channel I use.

EDIT: wifi is behaving more erratically than before. The connection is very sluggish and is disconnecting every few minutes.

---

### Post by jimbo6 on 2014-03-20
Is there any other information I can provide which might be useful? 

FYI wifi on windows 7 partition is working fine.

PS Does anyone know if 14.04 LTS will be compatible with this wifi card?

---

### Post by slooksterpsv on 2014-03-20
My Windows 8.1 Update 1 doesn't have issues with WiFi Signal Strength (connectivity issues yes) but there's a few reasons I do have certain issues:
1. Our WiFi router is going bad.
2. We have multiple Wireless devices and multiple wireless routers around us (apartment complexes suck).
3. The WiFi chip I have (RTL8188EE) I don't think works that well in this computer. I'm going to try and compile the driver directly from RTL website for my wireless.

---

### Post by jimbo6 on 2014-03-21
Thanks Slooksterpsv, 

[http://ubuntuforums.org/showthread.php?t=2196909&page=2](http://ubuntuforums.org/showthread.php?t=2196909&page=2)
Pretty much sums it up. There is little support for the Realtek wireless cards in Ubuntu 12.04 and although there may be some fixes in 14.04 it seems recommended that people just ditch the realtek cards and get something which has better support. 

I'm pretty gutted about this result.

---

### Post by varunendra on 2014-03-21
Could you please try installing the one from backports-3.12.8-1 again? That is the one I have had most successful cases so far (almost 100%, even if not with very awesome performance).

Along with that driver version, please try disabling "**N-channel**" in the router if it has the option (set it to b/g only mode), and try the parameters as suggested here : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

Even if you have tried that before, I'd like to see the following outputs with the parameters applied, temporarily or permanent..

With the above changes applied, if the problem still persists, please post a fresh report of "wireless_script", plus the output of -
```
grep [[:alnum:]] /sys/module/rtl*/parameters/*
```

---

### Post by jimbo6 on 2014-03-21
Hi Varun,

Unfortunately, my wifi is still as erratic and temperamental as before.

wireless script:

```

########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux ThinkPad-W530 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BAZD_MEG_LOCAL_EXT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=16/70  Signal level=-94 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #####


nameserver 192.168.1.1
nameserver 192.168.1.100


##### nm-tool #####


##### NetworkManager.state #####


##### NetworkManager.conf #####


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"VodafonePocketWiFi-F1F280"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000225f984559
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0019566F6461666F6E65506F636B6574576946692D463146323830
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A201118FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700102221020304050607080908636194F1F21021000842726F6164636F6D10230006536F66744150102400013010420001301054000800060050F20400011011000842726F6164636F6D100800020284103C0001011049000600372A000120
                    IE: Unknown: DD09001018020400040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Charlie's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004a34180aa
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0017436861726C696527732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 200100
                    IE: Unknown: 23021000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301770320
                    IE: Unknown: DD0E0017F20700010106881FA13A2459
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BAZD_MEG_LOCAL_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006265c26b
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001242415A445F4D45475F4C4F43414C5F455854
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DDA50050F204104A0001101044000102103B000103104700100000000000001000000030469AFFE2ED102100044E54475210230009574E3230303052505410240001311042001253657269616C204E756D62657220486572651054000800060050F20400011011001B574E3230303052505428576972656C6573732041502D322E344729100800020086103C000103104900140024E26002000101600000020001600100020001


##### iwlist channel #####


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


##### lsmod #####


rtl8192ce              79730  0 
rtl8192c_common        70705  1 rtl8192ce
rtl_pci                35486  1 rtl8192ce
rtlwifi                90145  2 rtl8192ce,rtl_pci
mac80211              526043  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              495836  2 rtlwifi,mac80211
compat                 13385  4 rtl8192ce,rtlwifi,mac80211,cfg80211


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     0AA476B9D524A7CBBB7360E
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,compat,mac80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8811228D1788BF0C4F4D7B6
depends:        mac80211,rtlwifi
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     710FFFC52D83E7E06A71F7E
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


##### modules #####


lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x05ac:0x1292 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    2.118938] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[    2.132058] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.138030] Bluetooth: can't load firmware, may not work correctly
[    2.153680] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.153911] rtlwifi: wireless switch is on
[    6.736094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.949958] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   16.026111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.955221] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.253350] wlan0: authenticate with <MAC address removed>
[   20.273290] wlan0: send auth to <MAC address removed> (try 1/3)
[   20.277386] wlan0: authenticated
[   20.281128] wlan0: associate with <MAC address removed> (try 1/3)
[   20.286077] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   20.286220] wlan0: associated
[   20.286244] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  271.504244] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  281.035989] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[  281.045822] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  281.046007] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  281.046212] rtlwifi: wireless switch is on
[  283.835304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  285.711056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  286.800302] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  289.779321] wlan0: authenticate with <MAC address removed>
[  289.799225] wlan0: send auth to <MAC address removed> (try 1/3)
[  289.902926] wlan0: send auth to <MAC address removed> (try 2/3)
[  289.909459] wlan0: authenticated
[  289.910917] wlan0: associate with <MAC address removed> (try 1/3)
[  289.914691] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  289.914841] wlan0: associated
[  289.914858] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  306.633167] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  317.852820] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[  317.862669] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  317.862685] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  317.862813] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  317.863030] rtlwifi: wireless switch is on
[  322.485748] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  331.508566] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.621493] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  335.943391] wlan0: authenticate with <MAC address removed>
[  335.963254] wlan0: send auth to <MAC address removed> (try 1/3)
[  336.066869] wlan0: send auth to <MAC address removed> (try 2/3)
[  336.070036] wlan0: authenticated
[  336.070889] wlan0: associate with <MAC address removed> (try 1/3)
[  336.078675] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  336.078760] wlan0: associated
[  336.078798] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  373.438618] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  383.058655] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[  383.068511] rtl8192ce: rtl8192ce: Power Save off (module option)
[  383.068524] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  383.068856] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  383.069146] rtlwifi: wireless switch is on
[  386.461102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  391.241079] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  392.369978] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  395.359285] wlan0: authenticate with <MAC address removed>
[  395.379189] wlan0: send auth to <MAC address removed> (try 1/3)
[  395.482853] wlan0: send auth to <MAC address removed> (try 2/3)
[  395.487011] wlan0: authenticated
[  395.490869] wlan0: associate with <MAC address removed> (try 1/3)
[  395.498383] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  395.498535] wlan0: associated
[  395.498575] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  414.400715] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  423.788343] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[  423.798198] rtl8192ce: rtl8192ce: Power Save off (module option)
[  423.798201] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  423.798213] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  423.798384] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  423.798593] rtlwifi: wireless switch is on
[  431.142113] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  435.426572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  436.548366] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  439.536902] wlan0: authenticate with <MAC address removed>
[  439.556770] wlan0: send auth to <MAC address removed> (try 1/3)
[  439.660545] wlan0: send auth to <MAC address removed> (try 2/3)
[  439.664899] wlan0: authenticated
[  439.668591] wlan0: associate with <MAC address removed> (try 1/3)
[  439.673570] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  439.673656] wlan0: associated
[  439.673694] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  446.572508] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  446.572555] wlan0: Connection to AP <MAC address removed> lost
[  447.550176] wlan0: authenticate with <MAC address removed>
[  447.570151] wlan0: send auth to <MAC address removed> (try 1/3)
[  447.673897] wlan0: send auth to <MAC address removed> (try 2/3)
[  447.778023] wlan0: send auth to <MAC address removed> (try 3/3)
[  447.882130] wlan0: authentication with <MAC address removed> timed out
[  458.423628] wlan0: authenticate with <MAC address removed>
[  458.443582] wlan0: send auth to <MAC address removed> (try 1/3)
[  458.445591] wlan0: authenticated
[  458.447224] wlan0: associate with <MAC address removed> (try 1/3)
[  458.451989] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  458.452074] wlan0: associated
[  464.633928] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  464.633958] wlan0: Connection to AP <MAC address removed> lost
[  465.616559] wlan0: authenticate with <MAC address removed>
[  465.636622] wlan0: send auth to <MAC address removed> (try 1/3)
[  465.740248] wlan0: send auth to <MAC address removed> (try 2/3)
[  465.844372] wlan0: send auth to <MAC address removed> (try 3/3)
[  465.948538] wlan0: authentication with <MAC address removed> timed out
[  476.490098] wlan0: authenticate with <MAC address removed>
[  476.510060] wlan0: send auth to <MAC address removed> (try 1/3)
[  476.512652] wlan0: authenticated
[  476.513603] wlan0: associate with <MAC address removed> (try 1/3)
[  476.518196] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  476.518282] wlan0: associated
[  482.689257] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  482.689293] wlan0: Connection to AP <MAC address removed> lost
[  483.674809] wlan0: authenticate with <MAC address removed>
[  483.694851] wlan0: send auth to <MAC address removed> (try 1/3)
[  483.798568] wlan0: send auth to <MAC address removed> (try 2/3)
[  483.902790] wlan0: send auth to <MAC address removed> (try 3/3)
[  484.006921] wlan0: authentication with <MAC address removed> timed out
[  494.544288] wlan0: authenticate with <MAC address removed>
[  494.564286] wlan0: send auth to <MAC address removed> (try 1/3)
[  494.566437] wlan0: authenticated
[  494.567994] wlan0: associate with <MAC address removed> (try 1/3)
[  494.575811] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  494.575895] wlan0: associated
[  500.324917] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  502.546694] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  502.951527] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  504.109473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  506.247070] wlan0: authenticate with <MAC address removed>
[  506.257288] wlan0: send auth to <MAC address removed> (try 1/3)
[  506.270071] wlan0: authenticated
[  506.270557] wlan0: associate with <MAC address removed> (try 1/3)
[  506.275162] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  506.275248] wlan0: associated
[  506.275286] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

~$ grep [[:alnum:]] /sys/module/rtl*/parameters/*

```

/sys/module/rtl8192ce/parameters/debug:0
/sys/module/rtl8192ce/parameters/fwlps:N
/sys/module/rtl8192ce/parameters/ips:N
/sys/module/rtl8192ce/parameters/swenc:Y
/sys/module/rtl8192ce/parameters/swlps:N

```

---

### Post by varunendra on 2014-03-21
You still seem to be using "N" channel in the router, please try disabling it. Refer to your router's user manual to see where the modes (b/g/n) can be selected/changed. Reboot the router after saving the change. If it doesn't help, can be easily reverted.

Also, if it supports 2.4/5 GHz dual-band mode, set it to 2.4 GHz only as 5 GHz doesn't seem to be well supported by many Linux drivers yet.

Please confirm which of these options are available in your router/access-point and if you tried changing them as suggested. Along with that, please post which country you are in. Is the router showing the same "Regulatory Domain" code or country name? (for example, US for USA, CA for Canada, etc..)

We may need to explicitly define the country code for regdomain settings. Currently it has been defaulted to "00" in your system.

---

### Post by jimbo6 on 2014-03-21
Hi Varun,

My router shows that it is set to 802.11 b+g with fragmentation threshold of 2346b.

I'm based in Australia and the setting was saved in the router previously.

---

### Post by varunendra on 2014-03-21
Does it offer the option to set it to "g-only" mode? Worth trying, assuming you don't have any ancient device that relies on "b" mode.

And please try this in Ubuntu -
```
sudo iw reg set AU
```
Disconnect --> Reconnect the wifi and see if it made any difference. All this with previous changes applied (the parameters).

This card has been reported to work nicely with the backported driver from kernel 3.12, so it seems to be something else than the driver to me.

Did Wicd solve the purpose you installed it for? If not, I'd recommend to reinstall NetworkManager -
```
sudo apt-get install network-manager network-manager-gnome
```
..and purge Wicd after that -
```
sudo apt-get purge wicd
```

---

### Post by jimbo6 on 2014-03-21
Hi Varun,

I've still got rapidly fluctuating signal strengths. Router set to 802.11g, tested with all the parameters etc. Still no change. 

Wicd was a bit strange. Even after purging wicd, it is still the only network manager available on the dash and it automatically loaded after rebooting the computer. I then removed it via the software centre. Rebooted and tried the original network manager again, and the original network manager is back.


Here's the updated wireless script:

```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


##### kernel #####


Linux ThinkPad-W530 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21f3]
	Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 


##### PCMCIA Card Info #####


##### rfkill #####


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BAZD_MEG_LOCAL_EXT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:86   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [BAZD_MEG_LOCAL_EXT] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Charlie's Wi-Fi Network: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA2
    7B4A08:          Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 26 WPA2
    VodafonePocketWiFi-F1F280: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA2
    Angel of death:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BigPond34ED:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA
    *BAZD_MEG_LOCAL_EXT: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BAZD_MEG_LOCAL:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2


  IPv4 Settings:
    Address:         192.168.1.180
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             192.168.1.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


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


##### lsmod #####


rtl8192ce              79730  0 
rtl8192c_common        70705  1 rtl8192ce
rtl_pci                35486  1 rtl8192ce
rtlwifi                90145  2 rtl8192ce,rtl_pci
mac80211              526043  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              495836  2 rtlwifi,mac80211
compat                 13385  4 rtl8192ce,rtlwifi,mac80211,cfg80211


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     0AA476B9D524A7CBBB7360E
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,compat,mac80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8811228D1788BF0C4F4D7B6
depends:        mac80211,rtlwifi
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     710FFFC52D83E7E06A71F7E
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


##### modules #####


lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x05ac:0x1292 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    2.783532] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[    2.809904] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.829809] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.830016] rtlwifi: wireless switch is on
[    2.924570] Bluetooth: can't load firmware, may not work correctly
[    3.571523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.571774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.776892] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   44.651916] wlan0: authenticate with <MAC address removed>
[   44.671749] wlan0: send auth to <MAC address removed> (try 1/3)
[   44.673222] wlan0: authenticated
[   44.675522] wlan0: associate with <MAC address removed> (try 1/3)
[   44.679851] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   44.679973] wlan0: associated
[   44.679981] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

---

### Post by varunendra on 2014-03-21
So the change we made to "RegDomain" country code was lost after reboot, which is normal I think -
> **jimbo6 said:**
> ```

##### iw reg get #####


**country [COLOR="#FF0000"]00[/COLOR]:**
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

```

However, it is the "iwconfig" output that is mysterious to me, because you say you have set the router to "g" mode, while "iwconfig" is still showing speed above 54 Mbps, which means it is communicating at (negotiated) "N" speeds -
```
wlan0     IEEE 802.11bgn  **ESSID:"BAZD_MEG_LOCAL_EXT"**  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          **Bit Rate=[COLOR="#FF0000"]72.2 Mb/s[/COLOR]**   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:86   Missed beacon:0
```
Are you sure it is only your router/access-point (the one you are making the changes in) to which it is connecting? Is it the one that has ESSID "BAZD_MEG_LOCAL_EXT"?

Please try forcing the correct regdomain code again, we'll make it permanent later if it helps -
```
sudo iw reg set AU
```

And IF you are sure the router settings are correct, and it is connecting to the one you want it to connect to (in which you are saving the changes), then try forcing a lower speed -
```
sudo iwconfig wlan0 rate 48M
```
You may also try even lower speeds like "24M" or "36M" with the above command and see if they make the connection any more stable.

---

### Post by jimbo6 on 2014-03-21
Hi Varun,

Thanks for this advice. 

It is puzzling as to why switching my b/g/n options to g on my router hasn't shown up on the results of my wireless script report. Could it be that I'm using both a router and a range extender? I changed the base router's settings to g but there is no such option for the extender. 

I followed these instructions to disable 11n: [http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable)

```

echo "options iwlwifi [COLOR=#417394]11n_disable[/COLOR]=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```

Here is my updated wireless script (I have also made the regdomain permanent as per your instructions):

```

########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux ThinkPad-W530 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"BAZD_MEG_LOCAL_EXT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [BAZD_MEG_LOCAL_EXT] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    VodafonePocketWiFi-F1F280: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA2
    Angel of death:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    *BAZD_MEG_LOCAL_EXT: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA2
    Charlie's Wi-Fi Network: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    BAZD_MEG_LOCAL:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    BigPond34ED:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA
    7B4A08:          Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 74 WPA2


  IPv4 Settings:
    Address:         192.168.1.181
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             192.168.1.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"BAZD_MEG_LOCAL_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004392fb1b
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001242415A445F4D45475F4C4F43414C5F455854
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DDA50050F204104A0001101044000102103B000103104700100000000000001000000030469AFFE2ED102100044E54475210230009574E3230303052505410240001311042001253657269616C204E756D62657220486572651054000800060050F20400011011001B574E3230303052505428576972656C6573732041502D322E344729100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"Angel of death"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e0440a2853
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000E416E67656C206F66206465617468
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606071700000000000000000000000000000000000000
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B000103104700102FBE24FD93B5D2907B06DA4C067AB5871021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F204000110110007426F424C697465100800020084103C000101
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"BAZD_MEG_LOCAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b37de7178
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 000E42415A445F4D45475F4C4F43414C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860164700260AC3E103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010013127A
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"VodafonePocketWiFi-F1F280"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fd42fc318
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0019566F6461666F6E65506F636B6574576946692D463146323830
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A201118FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700102221020304050607080908636194F1F21021000842726F6164636F6D10230006536F66744150102400013010420001301054000800060050F20400011011000842726F6164636F6D100800020284103C0001011049000600372A000120
                    IE: Unknown: DD09001018020400040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"BigPond34ED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000139836184
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 000B426967506F6E6433344544
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Charlie's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001217c37a83
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0017436861726C696527732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 200100
                    IE: Unknown: 23021000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301770320
                    IE: Unknown: DD0E0017F20700010106881FA13A2459
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Bellaaaaaaa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000094e33b0a
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000B42656C6C61616161616161
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0017F206010103010000
                    IE: Unknown: DD0D0017F206020106BC52B716A84B
                    IE: Unknown: DD09001018020100040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"7B4A08"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000121719ebd4
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0006374234413038
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160C000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000015127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706393520090510
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Byrnes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009a663d3183
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 00064279726E6573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: DD310050F204104A000110104400010210470010E0C4EE314F4C1092B30B3F01F5478E21103C0001031049000600372A000120
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


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


##### lsmod #####


rtl8192ce              79730  0 
rtl8192c_common        70705  1 rtl8192ce
rtl_pci                35486  1 rtl8192ce
rtlwifi                90145  2 rtl8192ce,rtl_pci
mac80211              526043  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              495836  2 rtlwifi,mac80211
compat                 13385  4 rtl8192ce,rtlwifi,mac80211,cfg80211


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     0AA476B9D524A7CBBB7360E
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,compat,mac80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8811228D1788BF0C4F4D7B6
depends:        mac80211,rtlwifi
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     710FFFC52D83E7E06A71F7E
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


##### modules #####


lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x05ac:0x1292 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    2.123905] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[    2.135366] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.156462] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.156664] rtlwifi: wireless switch is on
[    2.325773] Bluetooth: can't load firmware, may not work correctly
[    3.875619] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.875790] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.271914] wlan0: authenticate with <MAC address removed>
[    6.293005] wlan0: send auth to <MAC address removed> (try 1/3)
[    6.294435] wlan0: authenticated
[    6.295559] wlan0: associate with <MAC address removed> (try 1/3)
[    6.303497] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[    6.303695] wlan0: associated
[    6.303703] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    7.194090] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   98.131985] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[   98.132042] wlan0: Connection to AP <MAC address removed> lost
[   99.443199] wlan0: authenticate with <MAC address removed>
[   99.462322] wlan0: send auth to <MAC address removed> (try 1/3)
[   99.463752] wlan0: authenticated
[   99.465933] wlan0: associate with <MAC address removed> (try 1/3)
[   99.469750] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   99.469968] wlan0: associated


########## wireless info END ############

```



I am loathed to reduce the internet speed for the sake of stability. It is baffling how the same wifi card doesn't have to make such compromises on my windows partition. Further, (although the internet stability was never as consistent as on my windows partition) I didn't encounter this much instability before reinstalling ndiswrapper and upgrading to 3.11. 

Although my 12.04 Ubuntu wifi has always been more inconsistent than my windows partition, at least it has functional enough for me to use it as my primary OS. Should I just try to hold out by solely using my Windows partition for a couple of months to see if 14.04 will bring in marked improvements to the situation? What do you think? Will there be any improvements to Realtek wifi card support? I love using Ubuntu and significantly prefer it to Windows almost all respects, but reliable, stable and fast wifi is paramount for my needs. I'm very thankful for your attention to this matter and sorry you have had to share my frustration.

---

### Post by varunendra on 2014-03-22
> **jimbo6 said:**
> I followed these instructions to disable 11n....
Aha, gotcha! Firstly, those instructions disable the N-support on the driver, not the router, and Secondly, those instructions are for iwlwifi driver, not yours!

You have to disable the N on the router itself, by logging into its Admin control web interface. Refer to the router's manual to see how to do that.

> **jimbo6 said:**
> Here is my updated wireless script (I have also made the regdomain permanent as per your instructions):
```

**country [COLOR="#FF0000"]00[/COLOR]**:
    (2402 - 2472 @ 40), (3, 20)
    ....
```

As you can see above, the regdomain is still "00". I said we "will" make it permanent IF it helps, the command I suggested only applies the change Temporarily (until next boot). Usually not a big deal, but *sometimes* it does matter.

I haven't yet suggested to make it permanent because I'm not yet sure if it'll help. Sometimes, when the router was manufactured for another country than where it is being used (like imported one, or purchased from eBay etc.), forcing the local country code may even further worsen the stability. So we need to make sure it helps before making it permanent.

Once again, do remember to run this command on *each boot* (as long as we are in troubleshooting mode) to explicitly define the country code 'AU' (Australia) -
```
sudo iw reg set AU
```
To confirm whether it took effect -
```
iw reg get
```

> **jimbo6 said:**
> I am loathed to reduce the internet speed for the sake of stability.
I agree, that compromise is really not acceptable for modern networks, that's why I keep it as a last resort. But in our case here, we don't even know yet if it is going to help. Try it the correct way (by setting it in the router/AP, not in Ubuntu), and see if it helps. If it didn't, it is easy to revert so that at least other devices can take advantage of higher speeds (if they can).

However, keep in mind that the speed of the router drops to the lowest speed mode that any of the connected devices is using. So, for example, if you have a device on your network that connects to it in "g" mode, the router speed will drop to "g" mode anyway (while that device is connected), even if all the other connected devices do support "N" mode.

> **jimbo6 said:**
> Should I just try to hold out by solely using my Windows partition for a couple of months to see if 14.04 will bring in marked improvements to the situation? What do you think? Will there be any improvements to Realtek wifi card support? I love using Ubuntu and significantly prefer it to Windows almost all respects, but reliable, stable and fast wifi is paramount for my needs. I'm very thankful for your attention to this matter and sorry you have had to share my frustration.
First of all, most of us troubleshooters here are those bunch of guys who love to keep ourselves updated on "What works the best", and we don't mind any amount of tinkering to achieve that. It's a privilege to be able to help with something, and it's a pleasure to work with users who are cooperative and understand that we do it voluntarily. The intention is mostly to make the 'community' a better, helpful and enjoyable place, and partly to improve our own skills. :)

About waiting for 14.04 - there is, unfortunately, no guaranty or even a strong likelihood that things will improve dramatically. 14.04 will come out with kernel 3.13, and the driver in it would be more or less the same that you already tried from the backports (3.13...).

That being said, drivers keep improving, and given enough and proper **bug-reports + testing + feedbacks** from the users, nothing is impossible or unlikely.

What you are using as an OS is a result of collaborative and mostly selfless contributions from millions of developers/users across the globe, and you can join anytime you wish to help making it better. Imagine all those users who do the testing, file bug-reports, test patches, submit feedbacks, contribute in countless other ways sat back limiting themselves to Windows or even a "somehow working" version of Linux, and hoping some day some update will miraculously fix everything on a newer version.... then how much do you think the developers (most of whom are also volunteers) can do on their own, and how fast the development would be?

If you like the OS, consider contributing back as much as you can comfortably, in whatever way or form you like and can enjoy. For instance, register yourself on Launchpad if you don't already have an account there, and find an existing bug report about your problem (or submit a new one if there isn't an exact problem as yours is reported). Then submit your logs, details, whatever you are asked to help the developers determining the problem and suggest a patch/workaround. Keep using Windows for your regular work if you really need it, but keep track of your bug report as well, and do comment, testing, feedback when and as required.

You are not obliged to do anything like that and can keep using the OS as much and to whatever extent you like. But I bet you'll get addicted to the feeling of "Having contributed" back once you taste and realize it. If you can enjoy the OS, you'll certainly enjoy being part of its development as well, you just need to figure out the way that suits you best.

Sorry if I sounded emotional, I was not. I just don't know the Art of describing the Linux Philosophy and its way of working in a few words. :)

**Bottomline about your last quoted part above -** Use whatever fulfills you current needs, but consider submitting a bug report or adding yourself to an existing one. Hope for the best, but don't expect any miracles. :)

---

### Post by jimbo6 on 2014-03-22
Hi Varun,

Yes, it is a great mystery why the country code and g speed settings are just not reflected in the results! My previous post which explained the modification I had made to the 11n iwlwifi driver was done after having made the g speed change on my router a couple of posts before. It was just a shot in the dark to see if it would work!

From my reading on the topic - it appears, for the most part, that certain Realtek wireless chip sets are just incompatible with the OS. I can accept that the hardware is problematic with Linux. It's a disappointing result, but one that is understandable. Is it worth highlighting that for other, particularly new users? I'll probably hold out for the big 14.04 LTS release to test it with my system before making the decision to purchase and install another wifi card.

I completely agree with your sentiments. I am fully cognizant of the Linux philosophy you have outlined above. It is one of my primary reasons for switching to Ubuntu in the first place and why I prefer it to Windows. I wish to contribute my experience so that other users who may encounter similar issues as mine. Likewise, I am also cognizant of the selfless volunteer contributions you and others pour into the community and provide assistance to users like myself. I am extremely appreciative and grateful for it. I'll compose a bug report soon. In the meantime, if any other ideas/solutions come to mind please let me know!

---

### Post by varunendra on 2014-03-22
> **jimbo6 said:**
> Is it worth highlighting that for other, particularly new users? .....I'll compose a bug report soon. In the meantime, if any other ideas/solutions come to mind please let me know!
Sure you should share your experience for the benefit of all. For example, you may update this wiki page sharing your experience with the card - what you tried, what worked (to what extent), what failed etc : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

The base page for other such Supported device lists (in case you have some verified info to share about some other card also) : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I'm working on adding a few commands/codes in the wireless script to grab some more relevant info in problematic cases like this one. Hopefully it would be able to provide more insight into the setup more reliably, without requiring us to ask those extra outputs separately. But I don't know if I'll have enough time to dedicate to forums after this month (going to get involved in something, not sure for how long and how much time it'll spare me).

For now, I'll ask someone to look at this thread to see if I missed something obvious or if there is something else worth trying. You'll know if they posted. :)

---

### Post by praseodym on 2014-03-22
Try these module parameters:

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot. Have you tried the Beta of 14.04 LTS? IMHO the driver improved there...

---


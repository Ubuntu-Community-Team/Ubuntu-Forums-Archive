---
title: "Unstable wireless connection"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by eric5 on 2014-02-10
Hello, I have been fighting this problem for awhile now, ever since I got a new wireless router. I will connect and my internet speed is how it should be, then approx 5 min in it craps out EVERY time. Usually I have to reboot to get another 5 min before it craps out again. sigh

Looked in using the terminal to reset the network and that doesn't help much... end up rebooting after much frustration. Was ok with the previous hotspot I was using, but this new netgear router from verizon just sucks - for me at least. Stuck with it for 2 years, so if anyone can help me diagnosis the issue I would be appreciative! Note: every other computer/device works flawlessly with this router at same time my computer in question doesnt...

Sometimes I can whois somesitelikemine.com in terminal, and my connection will work again for a few minutes. Not everytime, but enough to pull my hair out more lol.

Using 802.11 WiFi Adapter... think gigabit with WPA2 & rtl8192ce driver. System is updated regularly. Ubuntu 12.04 lts 64bit.

Thanks for any help.

Eric

---

### Post by Iowan on 2014-02-11
Verify that your IP address is remaining consistent - almost sounds like the lease is timing out...
You could also try releasing or renewing the lease.  The router might provide hints about lease time.

---

### Post by eric5 on 2014-02-11
How would I verify that? I have had problems registering on some forums, forum mods have said my ip shows up as restricted etc. Verizon working for me lol!
Thanks for repling lowan.

---

### Post by Iowan on 2014-02-11
I'm more interested in the machine's IP address than the router's external address. You should be able to use **ifconfig ** from a terminal to show the IP address. You can also try to **ping** the router. Check the IP when the "net" is "working" and again when it isn't.  You may not see anything significant if the lease is expiring on the router.  That's where checking the router settings would be valuable.

---

### Post by eric5 on 2014-02-11
wlan0     Link encap:Ethernet  HWaddr 08:10:76:26:31:bc  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a10:76ff:fe26:31bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:156869852 (156.8 MB)  TX bytes:36569464 (36.5 MB)

---

### Post by varunendra on 2014-02-12
Hi Eric!

Command outputs should be always posted within 'Code' tags. Please follow the "Using Code Tags" link in my signature below to see a quick HowTo with screenshots.

As for your network problem, let's take a look at your system-wide overall setup. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by eric5 on 2014-02-27
Hello, thankyou for responding. Still having these issues, hard to use my linux box anymore... **hate** to go back to windows just to be able to use it again. :( I just downloaded your script and gave it a go. Hopefully you can see something wrong and get me steered in the correct direction. ~Eric

```

*************** info trace ***************

***** uname -a *****

Linux Orion 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 005: ID 1c4f:0016 SiGma Micro 
Bus 005 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 011 Device 002: ID 0bda:0301 Realtek Semiconductor Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"The_Smiths"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=300 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13276   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

***** lsmod *****

rtl8192ce              84872  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111269  1 rtl8192ce
mac80211              506862  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              205774  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [The_Smiths] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           300 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *The_Smiths:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 68 WPA2

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"The_Smiths"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000231d09005
                    Extra: Last beacon: 424ms ago
                    IE: Unknown: 000A5468655F536D69746873
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001004A83E2CC6BA2E45103BB68C57F6C72E1021000D4E4554474541522C20496E632E102300074D425231353135102400074D4252313531351042000230311054000800060050F2040001101100074D425231353135100800020084103C000101
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A400004243BC0062326600
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060D0400000000000000000000000000000000000000


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     DA52BF758B7683607AFCB85
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     6B1F1667933740748AE6E8D
depends:        mac80211
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     47B0B8A4B26657F075ABAED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:09.0/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:05.0/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.695701] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.695708] rtl8192ce 0000:03:00.0: setting latency timer to 64
[    3.005766] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    3.006584] rtlwifi: wireless switch is on
[    3.013184] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[    3.351430] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.352845] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.506259] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   24.004554] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   54.005130] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   94.009336] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  144.003067] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  204.004919] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  264.005833] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  324.005157] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  384.005740] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  444.003249] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  504.005665] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  564.005222] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  601.006920] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  602.312371] wlan0: authenticate with <MAC address removed> (try 1)
[  602.314249] wlan0: authenticated
[  602.334332] wlan0: associate with <MAC address removed> (try 1)
[  602.338387] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  602.338391] wlan0: associated
[  602.349744] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  612.416017] wlan0: no IPv6 routers present
[  627.866334] wlan0: authenticate with <MAC address removed> (try 1)
[  627.868727] wlan0: authenticated
[  627.868941] wlan0: associate with <MAC address removed> (try 1)
[  627.872744] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  627.872753] wlan0: associated
[ 5706.862785] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5708.058195] wlan0: authenticate with <MAC address removed> (try 1)
[ 5708.059742] wlan0: authenticated
[ 5708.059929] wlan0: associate with <MAC address removed> (try 1)
[ 5708.067334] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 5708.067338] wlan0: associated
[ 8467.682633] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8468.874656] wlan0: authenticate with <MAC address removed> (try 1)
[ 8468.877248] wlan0: authenticated
[ 8468.877380] wlan0: associate with <MAC address removed> (try 1)
[ 8468.885955] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 8468.885958] wlan0: associated
[10274.430419] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[10384.004830] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10504.003935] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10624.004341] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10744.004073] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10864.004782] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10984.004128] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11104.003079] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11224.004779] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11344.005196] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11464.005085] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11584.004673] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11704.003079] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11824.005310] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11944.005139] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12064.003058] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12184.004889] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12304.004110] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12424.003046] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12544.003744] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12664.005267] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12784.003588] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[12904.003728] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13024.007677] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13144.004455] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13264.005193] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13384.004729] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13504.004243] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13624.004853] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13744.003690] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13864.005077] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[13984.004438] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14104.003027] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14224.005097] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14237.144475] rtl8192ce 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[14237.144489] rtl8192ce 0000:03:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfddfc004)
[14237.144494] rtl8192ce 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xde01)
[14237.144499] rtl8192ce 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[14237.144504] rtl8192ce 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[14237.145387] rtlwifi: wireless switch is on
[14238.820373] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14239.157575] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14239.339635] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14260.005721] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14290.006537] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14330.002926] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14380.002916] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14440.004257] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14472.852081] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[14474.043693] wlan0: authenticate with <MAC address removed> (try 1)
[14474.046101] wlan0: authenticated
[14474.046449] wlan0: associate with <MAC address removed> (try 1)
[14474.051718] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[14474.051723] wlan0: associated
[14474.064875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14484.248008] wlan0: no IPv6 routers present
[17546.257733] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[17660.003786] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[17780.004112] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[17900.003832] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18020.003799] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18140.004212] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18260.003915] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18380.004382] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18500.003398] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18620.003826] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18740.004413] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18860.004183] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[18980.003754] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19100.003719] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19220.004629] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19340.004547] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19460.004098] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19580.003648] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19700.004454] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19820.004184] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[19940.004337] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20060.003720] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20180.004232] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20300.004611] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20420.003882] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20540.004051] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20660.004463] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20780.003905] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20835.904472] rtl8192ce 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[20835.904486] rtl8192ce 0000:03:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfddfc004)
[20835.904491] rtl8192ce 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xde01)
[20835.904496] rtl8192ce 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[20835.904501] rtl8192ce 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[20835.905078] rtlwifi: wireless switch is on
[20837.746497] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20838.192330] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20838.371207] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20859.003656] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20889.002664] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20929.002826] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20943.449424] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20944.640141] wlan0: authenticate with <MAC address removed> (try 1)
[20944.641683] wlan0: authenticated
[20944.641899] wlan0: associate with <MAC address removed> (try 1)
[20944.645514] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[20944.645519] wlan0: associated
[20944.657710] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20955.000015] wlan0: no IPv6 routers present
[27022.666737] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[27023.858386] wlan0: authenticate with <MAC address removed> (try 1)
[27023.859865] wlan0: authenticated
[27023.860113] wlan0: associate with <MAC address removed> (try 1)
[27023.866082] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[27023.866087] wlan0: associated

****************** done ******************

```

---

### Post by varunendra on 2014-02-28
Hmm.. your dmesg is full of these -
> **eric5 said:**
> ```

[20838.371207] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20859.003656] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20889.002664] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[20929.002826] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
.... (and on and on..)

```

..which is definitely a problem, but not sure about the cause. I have a guess though - probably either the firmware is suspending frequently, or more likely, is crashing frequently due to not being able to handle the high speed traffic it is getting, thus reloaded frequently.

Accordingly, please try some tweaks -

Try changing the channel in the router to 1 or 11.
Also try disabling the N-channel in the router (setting it to b/g only mode). If you do get N-speeds and need it, still do it just for experiment. You may revert it after the testing if you need the N-channel.

After saving any changes in the router, reboot it to let the changes properly take effect.

If these don't help, please try the suggestions in this post : [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912) and report back how it goes.

**PS:**
Is a fresh installation an easy choice for you? Just in case we needed to compile newer driver, a newer kernel may be required. Although shouldn't be necessary.

---

### Post by eric5 on 2014-03-01
Thanks for the help **varunendra**, I changed the router's channel from auto to 01. So far all *seems* fine loading pages with no crapping out. I will keep testing and see how it goes and will report back as needed.

~ I am still having issues with connecting to the dang router. Sometimes takes multiple attempts, reboots, etc to get it to connect. But that is another issue!

---

### Post by varunendra on 2014-03-01
Please do let us know. It is the feedback by users like you that keeps us up-to-date with most relevant and working solutions.

and..
> **eric5 said:**
> ~ I am still having issues with connecting to the dang router....But that is another issue!
..or maybe not. If it is the same interface, that is a related problem and should get resolved, in addition to being stable.

---


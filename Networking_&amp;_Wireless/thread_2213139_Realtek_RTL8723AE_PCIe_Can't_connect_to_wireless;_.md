---
title: "Realtek RTL8723AE PCIe: Can't connect to wireless; Ubuntu 13.04"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by Grey_Dawn_Breaking on 2014-03-25
I've just bought a new computer which came loaded with Ubuntu 13.04, and it won't connect to the internet. I used to consider myself pretty good with computers, but it turns out that my skill was entirely Windows-dependent. I am hopelessly and embarrassingly out of my depth with Ubuntu. 

The manufacturer sent me what I'm told is a driver, but didn't say how to install it. It's a zip file containing one tar.gz and one rar file. There was no install or readme file. 

I've tried double-clicking on each individual file contained within the zipped folders; they mostly opened in a text editor. I've tried restarting the computer with the zipped and unzipped tar.gz file dropped into various folders where it seemed like it should work (config, etc), but there was no change. I tried running a command text line I found through here: [http://www.control-escape.com/linux/lx-swinstall.html](http://www.control-escape.com/linux/lx-swinstall.html) (the tar ball instructions) with the tar.gz file dropped into various locations around the computer; it kept returning a "file not found"-type error. I have no idea what else to try.

I'm happy to provide more information as needed. Can anyone help? :)

---

### Post by Grey_Dawn_Breaking on 2014-03-25
I saw someone else ask for this, so I figured I'd put it out there. This is from the wireless script recommended by varunendra.

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

##### kernel #####

Linux horize-W650SR 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae

04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0650]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 005: ID 1058:1023 Western Digital Technologies, Inc. Elements SE
Bus 003 Device 004: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

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

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR35:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA2
    RUBYG:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Bostocks:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA2

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
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR35"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000027b4587f79d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00094E4554474541523335
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001088F5A131D9EE691FABFAC53B5DCB27D0102100074E6574676561721023000A44474E443337303076321024000A44474E4433373030763210420004313233341054000800060050F20400011011000A44474E4433373030763210080002200C103C0001031049000600372A000120
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"RUBYG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a40d6e73d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00055255425947
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606071600000000000000000000000000000000000000
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B0001031047001068219D365FD93DA0B38BA3AD8689198F1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F204000110110007426F424C697465100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
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

##### lsmod #####

rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723aefw_B.bin
firmware:       rtlwifi/rtl8723aefw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     03790CA78F2ECC964C06F5E
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 

##### modules #####

loop
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

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    2.480219] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[    2.492617] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.492778] rtlwifi: wireless switch is on
[    3.002392] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.002562] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.267687] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   17.124055] rtlwifi: wireless switch is on
[   24.514461] rtlwifi: wireless switch is on
[   52.459644] wlan0: authenticate with <MAC address removed>
[   52.491474] wlan0: send auth to <MAC address removed> (try 1/3)
[   52.493026] wlan0: authenticated
[   52.495265] wlan0: associate with <MAC address removed> (try 1/3)
[   52.498143] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   52.498254] wlan0: associated
[   52.498260] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.475843] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   65.263965] wlan0: authenticate with <MAC address removed>
[   65.292808] wlan0: send auth to <MAC address removed> (try 1/3)
[   65.294303] wlan0: authenticated
[   65.295609] wlan0: associate with <MAC address removed> (try 1/3)
[   65.298518] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   65.298616] wlan0: associated
[   73.277211] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  345.374387] wlan0: authenticate with <MAC address removed>
[  345.403364] wlan0: send auth to <MAC address removed> (try 1/3)
[  345.404887] wlan0: authenticated
[  345.406127] wlan0: associate with <MAC address removed> (try 1/3)
[  345.409062] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  345.409166] wlan0: associated
[  353.386958] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  357.292148] wlan0: authenticate with <MAC address removed>
[  357.321052] wlan0: send auth to <MAC address removed> (try 1/3)
[  357.322543] wlan0: authenticated
[  357.323849] wlan0: associate with <MAC address removed> (try 1/3)
[  357.326761] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  357.326851] wlan0: associated
[  365.306162] wlan0: deauthenticated from <MAC address removed> (Reason: 15)

########## wireless info END ############


```

---

### Post by bshatt1987 on 2014-03-25
What are the files called in the package that you were sent?

---

### Post by Grey_Dawn_Breaking on 2014-03-25
Main zip: RTL8723AS-VAU linux driver

two internal folders:
8723AE_8723AU_Linux_BT_20121109_v35.rar
rtl8723A_WiFi_linux_v4.1.3_6044.20121224.tar.gz

Contents of rtl8723A_WiFi_linux_v4.1.3_6044.20121224.tar.gz:

Folders core, hal, include, and os_dep
files: make_drv, Makefile, runwpa, Kconfig, clean, ifcfg-wlan0, wlan0dhcp, autoconf_rtl8723a_sdio_linux.h, autoconf_rtl8723a_usb_linux.h, Kconfig_rtl8723a_sdio_linux, Kconfig_rtl8723a_usb_linux

There are a ton of files in each folder, let me know if you need them all?

---

### Post by bshatt1987 on 2014-03-25
Alright, I'm pretty much a beginner myself, but I have been learning a little bit so I'll try to help.  
If you've got wired internet access on the machine, you might try this (each command individually):
```
sudo apt-get install --reinstall build-essential linux-headers-$(uname -r)
wget  http://media.cdn.ubuntu-de.org/forum/attachments/38/34/5443987-rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patc.gz
tar xzvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013_patc.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware
```

Reboot the computer and see if it worked.

If you don't have wired access, try this - 

To extract the files I rarely use the terminal and just right click on the package and click "Open with Archive Manager".  Then I extract it that way, into my home folder.  
The way I'm seeing it, there are archives within the archive, so you'll want to extract those as well.  Then use the terminal to navigate into the rtl8723A_WiFi_linux_v4.1.3_6044.20121224 folder. 
So if you extract rtl8723A_WiFi_linux_v4.1.3_6044.20121224.tar.gz to it's own folder in your home folder, in the terminal you'd type:
```
cd ./rtl8723A_WiFi_linux_v4.1.3_6044.20121224
```

Once you're inside that folder in the terminal, do (again, each command individually):
```
make
sudo make install
sudo depmod -a
sudo update-initramfs -u 
sudo cp -r firmware/* /lib/firmware
```
Reboot the computer.

---

### Post by mörgæs on 2014-03-25
13.04 is out of support.
Your best option is to begin with a fresh install of 13.10 using wired internet access, forgetting wifi to begin with. Please post back when that works.

---


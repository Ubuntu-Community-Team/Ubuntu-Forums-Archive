---
title: "BCM4331 Erratic Connection"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by shadesofoctober on 2014-07-24
Alright guys, so I hate to contribute yet another wireless issue post, but I honestly cannot find a single similar solved topic.

Basically, I've been running 14.04 on my Macbook 8,1 (I know this is an Apple device, but I feel this is more a networking section issue). It uses a Broadcom 4331.

Rather recently, last 2-3 days, I've been getting a very unreliable connection.
Sort of 30-seconds on, 2-minutes off kinda deal. Network manager shows the connection as still being held, but I can't even ping my gateway, let alone Google.

I have tried BOTH b43 and wl drivers (firmware-b43-installer, linux-firmware-nonfree, and bcmwl-kernel-source packages). All same results, surprisingly.

I was running Ubuntu Gnome when it first started, but wiped and installed vanilla Ubuntu last night.. still getting same results. I'm at a loss. At this point, I'm worried the hardware's gone under.
I may try Fedora and see if I get same results, but when using it I have to compile the module from scratch with every new kernel (Very annoying).

Anyhow, here are the wireless-info script results. I'll post the ones from wl and b43.

```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux mbp81-linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)


03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00d6]
    Kernel driver in use: wl


##### lsusb #####


Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 009: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan1     IEEE 802.11abg  ESSID:"drupper"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.100 0.0.0.0         UG    0      0        0 wlan1
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #####


nameserver 127.0.1.1
search hsd1.wa.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan1  [drupper 1] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           195 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *drupper:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2


  IPv4 Settings:
    Address:         192.168.100.156
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.100


    DNS:             75.75.75.75
    DNS:             75.75.76.76
    DNS:             192.168.100.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-5 dBm  
                    Encryption key:on
                    ESSID:"drupper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000764727570706572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C33FE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          
##### iwlist channel #####


wlan1     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #####


[   10.528022] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.529311] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   10.664089] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   10.708191] wlan0: Broadcom BCM4331 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   10.747533] systemd-udevd[354]: renamed network interface wlan0 to wlan1
[   44.618371] ERROR @wl_notify_scan_status : wlan1 Scan_results error (-22)
[   89.045342] ERROR @wl_notify_scan_status : wlan1 Scan_results error (-22)
[  236.398509] ERROR @wl_notify_scan_status : wlan1 Scan_results error (-22)
[  261.520572] ERROR @wl_dev_intvar_get : error (-1)
[  261.520583] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  579.532903] ERROR @wl_notify_scan_status : wlan1 Scan_results error (-22)
[  633.485565] ERROR @wl_dev_intvar_get : error (-1)
[  633.485576] ERROR @wl_cfg80211_get_tx_power : error (-1)


########## wireless info END ############

```

And from using b43:

```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux mbp81-linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)


03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]
    Kernel driver in use: bcma-pci-bridge


##### lsusb #####


Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 009: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


b43                   387371  0 
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
bcma                   52096  1 b43


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan1     IEEE 802.11bg  ESSID:"drupper"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=0 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:192  Invalid misc:154   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.100 0.0.0.0         UG    0      0        0 wlan1
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #####


nameserver 127.0.1.1
search hsd1.wa.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan1  [drupper 1] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *drupper:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2


  IPv4 Settings:
    Address:         192.168.100.156
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.100


    DNS:             75.75.75.75
    DNS:             75.75.76.76
    DNS:             192.168.100.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"drupper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000064cb029034
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000764727570706572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C33FE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
         
##### iwlist channel #####


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
          Current Frequency:2.462 GHz (Channel 11)


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     42BAE2DB9BADE3E7ECA2CC0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #####


[    9.119007] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
[    9.119043] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[    9.119070] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[    9.119125] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[    9.170235] bcma: bus0: Bus registered
[   10.670948] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   10.671339] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   10.956405] systemd-udevd[350]: renamed network interface wlan0 to wlan1
[   20.452416] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   20.544999] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.545278] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.036504] wlan1: authenticate with <MAC address removed>
[   22.066035] wlan1: send auth to <MAC address removed> (try 1/3)
[   22.070149] wlan1: authenticated
[   22.073822] wlan1: associate with <MAC address removed> (try 1/3)
[   22.096828] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=15)
[   22.097281] wlan1: associated
[   22.097311] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


########## wireless info END ############

```

Edit: Running ping for 5 minutes under Ubuntu to Google gets me about 73% packet loss with a ~50ms trip. The same under OS X is 0% packet loss with ~20ms trips. So much for the hardware.
Edit2: Using an earlier kernel made no difference either. Totally confused.. is there a recent update out that kills bcm device connectivity?

---

### Post by Hadaka on 2014-07-24
Hi, open a terminal and please do..

you may get *not found or some error on these, but do
both anyway.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do.
```
sudo apt-get update
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe b43
```
Then run the wireless script again if this doesnt help
thanks

---

### Post by mode7 on 2014-07-24
Hi Hadaka, I followed the steps for reinstalling b43 but had the same issue. wl was already purged.
(This is shadesofoctober, btw, just got back into my old account)

Ping for about 15 min, 46% packet loss :/ (Is there another way to check connectivity status over a period of time?)

```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux mbp81-linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)


03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]
    Kernel driver in use: bcma-pci-bridge


##### lsusb #####


Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


b43                   387371  0 
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
bcma                   52096  1 b43


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan1     IEEE 802.11bg  ESSID:"drupper"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=0 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:146  Invalid misc:117   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.100 0.0.0.0         UG    0      0        0 wlan1
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #####


nameserver 127.0.1.1
search hsd1.wa.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan1  [drupper 1] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           24 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *drupper:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2


  IPv4 Settings:
    Address:         192.168.100.156
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.100


    DNS:             75.75.75.75
    DNS:             75.75.76.76
    DNS:             192.168.100.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"drupper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000069d504615b
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000764727570706572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C33FE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
         
##### iwlist channel #####


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
          Current Frequency:2.462 GHz (Channel 11)


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     42BAE2DB9BADE3E7ECA2CC0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #####


[   14.960456] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
[   14.960487] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   14.960512] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   14.960558] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   14.971705] bcma: bus0: Bus registered
[   15.174084] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   15.174492] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   15.475885] systemd-udevd[347]: renamed network interface wlan0 to wlan1
[   20.904471] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   20.997012] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.997293] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.303767] wlan1: authenticate with <MAC address removed>
[   22.333881] wlan1: send auth to <MAC address removed> (try 1/3)
[   22.355397] wlan1: authenticated
[   22.357642] wlan1: associate with <MAC address removed> (try 1/3)
[   22.380800] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=21)
[   22.381205] wlan1: associated
[   22.381227] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


########## wireless info END ############
```

---

### Post by Hadaka on 2014-07-24
ok, let's give this a try..
```
sudo modprobe -rf b43
echo options b43 nohwcrypt=1 | sudo tee -a /etc/modprobe.d/b43.conf
sudo modprobe b43
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo iw reg set US
```
and repost the wireless script if this doesnt help
thanks

---

### Post by mode7 on 2014-07-24
No-Go.. tried multiple reboots. Talk about frustrating.. I've been using this computer for a web development class :(

```

########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux mbp81-linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)


03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]
    Kernel driver in use: bcma-pci-bridge


##### lsusb #####


Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


b43                   387371  0 
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
bcma                   52096  1 b43


##### iw reg get #####


country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan1     IEEE 802.11bg  ESSID:"drupper"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=0 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:25  Invalid misc:70   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.100 0.0.0.0         UG    0      0        0 wlan1
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #####


nameserver 127.0.1.1
search hsd1.wa.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan1  [drupper] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           24 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *drupper:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2


  IPv4 Settings:
    Address:         192.168.100.156
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.100


    DNS:             75.75.75.75
    DNS:             75.75.76.76
    DNS:             192.168.100.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"drupper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006ac200f5b6
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000764727570706572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C33FE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


wlan1     11 channels in total; available frequencies :
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


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     42BAE2DB9BADE3E7ECA2CC0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
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


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x14e4:0x16b4 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #####


[   14.551173] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
[   14.551206] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   14.551234] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   14.551628] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   14.602327] bcma: bus0: Bus registered
[   14.755920] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   14.756325] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   14.969487] systemd-udevd[354]: renamed network interface wlan0 to wlan1
[   20.077763] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   20.170386] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.170737] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   21.076642] wlan1: authenticate with <MAC address removed>
[   21.106810] wlan1: send auth to <MAC address removed> (try 1/3)
[   21.131769] wlan1: authenticated
[   21.134714] wlan1: associate with <MAC address removed> (try 1/3)
[   21.158397] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=24)
[   21.158821] wlan1: associated
[   21.158847] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   75.666453] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[   84.629635] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   84.703467] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  103.081048] wlan1: authenticate with <MAC address removed>
[  103.088380] wlan1: send auth to <MAC address removed> (try 1/3)
[  103.111020] wlan1: authenticated
[  103.112102] wlan1: associate with <MAC address removed> (try 1/3)
[  103.134902] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=22)
[  103.135728] wlan1: associated
[  103.135801] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


########## wireless info END ############

```

---

### Post by Hadaka on 2014-07-24
try setting you rnetwork piv4 like this
[ATTACH=CONFIG]254995[/ATTACH]

and set ipv6 to ignore

---

### Post by mode7 on 2014-07-24
Nope :( I switched to Google's nameservers, and ignored ipv6 (Which I tried before I wiped the computer)

This computer has been out for 3 years, and I've always had issues with it's wireless!!

I may try Fedora or OpenSUSE just to see if the problem is still there. I'd really like to stick with Ubuntu on this machine for the long-term, though.

---

### Post by Hadaka on 2014-07-24
Yeah, im running out of ideas here, and ive always had
good luck with appl boxes, you might try ubuntu12.04
its supported untill 2017 and is a proven os,
sorry i wasnt able to get your problem solved, perhaps
someone else has some ideas.

one last possible is to turn off the N function in the router if possible.

---

### Post by mode7 on 2014-07-25
Fedora 20, wl driver.. same issue. Took hours to update and get it set up, too.

Thought for sure another distro would work, but this leads me back to thinking my wifi transponder is damaged or failing.

Please tell me someone else has had this issue or something. Lack of (reliable) wireless renders this computer useless.
I could use a dongle, but it kills the laptop's form factor, and more often that not cuts off the only other USB port because the idiotic hardware designers put them so close together.
Not that it's not a choice, but just a very annoying one.

What really frustrates me is I don't see ANY indication anywhere. No dmesg errors, nada. It just fails to connect (Yet still shows as connected). Is there another log somewhere??

---

### Post by mode7 on 2014-07-25
Update, I tried installing Elementary Luna since it is based on 12.04 (IIRC) and I had it laying around.
The install itself failed, something about Grub-EFI package not finding target. I had this problem before, but haven't had to deal with it in a couple years, so I've forgotten the solution.
However, at some point during the install, it managed to install the wl drivers, so I decided to just give them a try... and no issue. 0% packet loss, decent round-trip-time.

I really would prefer to not focus resources on installing an older version, because the kernels prior to 3.3 do not support EFI stubs, which I use. And the development tools are older, I want a more modern g++ with c++11 support, QT creator, GIT, etc..

So basically..
Older distros (at least 12.04), wireless connection works fine.
OSX 10.9, works fine.
Modern distros up to about 3-4 days ago, works fine. After that, wifi connection is super sporadic.

What is causing this? Was some broken update pushed out? It would have to be at least on both Fedora and Ubuntu.
Now I haven't tried installing OpenSUSE yet, but since I wiped the machine so many times already, why not?

I appreciate any insight anyone might have, or if anyone has had similar issues!

Edit: OpenSUSE failed to even boot after install. Could not mount root filesystem.

---

### Post by Hadaka on 2014-07-25
Hi, 

brcm4331 seems to only be found in aapl boxes and just doesnt want
to run on the 14.04 os/current kernel, but will run on 12.04
the linux-firmware-nonfree is the correct driver for this card. I would
suggest using a usb wifi,changeing out the 4331 card for a 4311 or 4318
card or running os 12.04lts .those are pretty much your options. changeing
the card should allow you to use 14.04.
good luck

---

### Post by mode7 on 2014-07-25
Well, 12.04 brings way more issues in exchange for fixing wireless.
And unfortunately I cannot take it apart and exchange the PCI wifi (As much as I'd like to remove it and grind it into dust)
But, I think I will reinstall 14.04 and go find a nice smaller usb wifi adapter.
Maybe the issue will fix itself with some update, I just wish I knew why it worked just fine until this week.
Thanks for the help, anyhow.

---

### Post by varunendra on 2014-07-26
Please check syslog and see if there are some hints there. If not sure, please upload the output of -
```
egrep -i 'wpa|network|b43|ssb|dhclient|wlan' /var/log/syslog
```
..to pastebin.ubuntu.com, and post the pastebin link here.

If the output is so long that it goes beyond the terminal, you may redirect it to a file by appending " > filename" after the above command, or, by installing "pastebinit" and using it to upload the output directly from terminal -
```
sudo apt-get install pastebinit
egrep -i 'wpa|network|b43|ssb|dhclient|wlan' /var/log/syslog **| pastebinit**
```

We may be seeing a possible bug in Network Manager or wpa_supplicant, the one I have in mind causes the freeze exactly every two minutes.

---

### Post by mode7 on 2014-07-26
I have looked through the output of syslog, but really do not know what specifically to look for.
The output is pretty much entirely from boot. There is nothing that comes up after (During actual usage and connection downtime)
Anyhow, here is the output from today: [http://pastebin.ubuntu.com/7871006/](http://pastebin.ubuntu.com/7871006/)

---

### Post by Hadaka on 2014-07-27
Hi, you still have wl being used as the driver with is not correct,,
```
Jul 26 19:33:01 mbp81-linux NetworkManager[1053]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan1/rfkill1) (driver [COLOR=#ff0000]**wl**[/COLOR][COLOR=#ff0000][/COLOR])

```
please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do while connected to the internet with cable
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
Then please repeat Varunendras request
thanks.[COLOR=#ff0000][/COLOR]

---

### Post by mode7 on 2014-07-27
I just stuck with wl since it is what Ubuntu actually uses by default (Appears in the proprietary driver list) and it always seemed a little more stable (Back before this issue). 
But I've switched to b43 and rebooted. It's behaving a little better, but after about 10 min it got very bad again.
Here is the syslog output starting from about the reboot.
[http://paste.ubuntu.com/7872196/](http://paste.ubuntu.com/7872196/)
The wpa_supplicant messages are new from last time. Nothing really sticking out to my untrained eyes, though.

---

### Post by varunendra on 2014-07-27
Yup, the ones I was suspecting to see are here too -
```
Jul 26 22:45:53 mbp81-linux wpa_supplicant[1124]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jul 26 22:45:58 mbp81-linux wpa_supplicant[1124]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 26 22:46:36 mbp81-linux wpa_supplicant[1124]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jul 26 22:46:41 mbp81-linux wpa_supplicant[1124]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 26 22:47:39 mbp81-linux wpa_supplicant[1124]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jul 26 22:50:45 mbp81-linux wpa_supplicant[1124]: message repeated 2 times: [ wlan1: CTRL-EVENT-SCAN-STARTED ]
Jul 26 22:50:50 mbp81-linux wpa_supplicant[1124]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 26 22:52:45 mbp81-linux wpa_supplicant[1124]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jul 26 22:56:45 mbp81-linux wpa_supplicant[1124]: message repeated 2 times: [ wlan1: CTRL-EVENT-SCAN-STARTED ]
Jul 26 22:56:50 mbp81-linux wpa_supplicant[1124]: nl80211: send_and_recv->nl_recvmsgs failed: -33
```
..however, I am not yet sure if these messages are the problem themselves or the result of the problem, or just a red herring. Nonetheless, since everything abnormal seems to be associated with "NetworkManager" in the syslog, can you please try WICD instead of Network Manager for a test?

Please follow these exact instructions to download the Network Manager packages first, then install WICD and purge NM : [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

Then reboot and let us know if it could improve things.

Oh, and keep the b43 driver on now, don't revert to "wl" unless all our attempts with b43 have failed.

---

### Post by mode7 on 2014-07-27
The WICD install went great. Besides the absence of a tray icon, it detected all the nearby networks and connected just fine.

Unfortunately, the problem is still there, and if anything, quite a bit worse.
I have 2 routers in my house (Upstairs/downstairs), they both run on different channels, are both made by Linksys (But different models), and I've had the same bad luck with both.
I usually will get internet for just a tiny bit by switching to the other router, but it inevitably comes back to not working.

I will re-post the syslog and wireless-script since I haven't used WICD until now..
Syslog dump: [http://paste.ubuntu.com/7872662/](http://paste.ubuntu.com/7872662/)
Wireless script: [http://paste.ubuntu.com/7872701/](http://paste.ubuntu.com/7872701/)

Note: The rtl driver is for the little Edimax USB adapter I've been using (Stole it from my Raspberry Pi). I don't have it plugged in at all while testing any of this stuff out.

I really appreciate your guys' help, so far. It's a shame this wireless is being so insanely stubborn.

---

### Post by varunendra on 2014-07-27
Please unplug your USB adapter, then remove your current udev rules file -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Reboot and run a new, experimental script mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) (download it beforehand so you don't have to connect the usb adapter to download and run it). This one covers some extra info that may be helpful sometimes.

We want a clean report, so don't plug in the usb adapter after the reboot, until the report is generated.

---

### Post by mode7 on 2014-07-27
Bad news. After removing the udev rules and rebooting, no networks could be detected at all using the built-in wireless.
The b43 mod is still loaded, and the bcm4331 device is recognized, so not sure what happened there.
I grabbed the script output before plugging in the usb adapter, though.
[http://paste.ubuntu.com/7872972/](http://paste.ubuntu.com/7872972/)

Edit: Had to reboot into OSX just to make sure the device was still working.. go figure, still working absolutely fine under OSX.
Maybe I have to purge and reload the b43 modules to get it back.
I've installed 4 distros on this in the past 2 days, so I am fine with trying whatever at this point. Nothing to lose.

---

### Post by varunendra on 2014-07-27
> **mode7 said:**
> Bad news.
I'd say 'different news', maybe not bad at all.

A new udev file has been generated as expected. I am not very familiar with WICD myself, so it is possible that it has remembered the old logical name "wlan1" in the profile it saved. Besides, there is another thing I don't like to see - the "Power Management" on the wireless is "on".

Please try the following -

**1)** Delete any saved profiles in WICD, then try to scan for available networks again. Reboot if required.

**2)** Before rebooting, try turning the power management off on the wifi interface -
```
sudo iwconfig wlan0 power off
```
And after reboot, check -
```
iwconfig
```
Has "Power Management" turned back on? Is the "Tx Power" still '0' ?

If the Tx Power is still 0, try this -
```
sudo iwconfig wlan0 txpower 20
```
If that returns any errors, try value '15' instead of 20. Does it stick (check with "iwconfig" again). If yes, try to scan manually -
```
sudo iwlist scan
```
Can you see available networks in the output?

If anything has to be reverted, I would start with WICD - purging it with "sudo apt-get purge wicd", then installing Network Manager again with "sudo apt-get install network-manager-gnome" .... followed by a reboot to let it load automatically.

I won't suggest to revert to the wl driver yet, since b43 has been a trusted driver, and we can't try as many things with "wl" as with "b43".

---

### Post by Hadaka on 2014-07-27
hi have you been doing the.,,
```
sudo apt-get update
```
when you have been distro hoppin?
if not...please do.
I also noticed,,,your card,,
```
Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [**[COLOR=#ff0000]14e4:4331[/COLOR]**] (rev 02)
```
gets its alias from the bcma module,
```
~$ modinfo bcma
filename:       /lib/modules/3.2.0-67-generic-pae/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v0000**[COLOR=#ff0000]14e4[/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]**d0000**[COLOR=#ff0000]4331[/COLOR]**[COLOR=#ff0000][/COLOR]**[COLOR=#ff0000][/COLOR]**sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*

```
*so you might also want to try the special case #1 as found in the sticky.

---

### Post by mode7 on 2014-07-27
Good catch on the power management. Didn't notice that turned back on.

Alright, so from using iwconfig, I was unable to make any progress. The interface is refusing to accept any input.
Attempting** sudo iwconfig wlan0 power off**
```

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```
Now setting the txpower property doesn't return any errors, but if I run iwconfig again, it is still 0. This is before and after reboot, too.
Doing any scanning reports that for wlan0: Interface doesn't support scanning : Network is down.

I think at this point, I will do the revert and see if it can interact with the interface again.

Edit: @Hadaka, I could not fully get elementary Luna fully installed (Although I was able to install wl in the live session, which worked great), and a full yum upgrade for Fedora (Same wifi problem). I tried OpenSUSE last, but it couldn't boot, so I wiped and went back to Ubuntu 14.04.
I did try blacklisting b43 and ssb, but it didn't detect any interface at all upon reboot :(

I purged wicd and went back to network manager, and it detects networks again.
After using for a bit, it is still very spotty. It took forever to get the script results into pastebin.
Here is the latest wireless info script (Only thing I removed were neighbor's APs): [http://paste.ubuntu.com/7877753/]("https://paste.ubuntu.com/7877753/")

---

### Post by Gary_Shelton on 2014-10-04
It's not your hardware, or at least not your hardware failing. I have an early-2011 15" MBP with the same BCM4331 that's running Linux (only way I could continue to use it after the discrete GPU stopped functioning), and I have exactly the same problem. While using WiFi, my connection drops packets, stops resolving, etc. Linux has been terrific on this machine otherwise, but for me the erratic WiFi severely limits my machine's usefulness as a portable :/

---

### Post by Rod_Guareschi on 2014-10-15
mode7, you are not the only one with this issue. I have the exact same issue with the same hardware. So far, I believe I've tried ~20 proposed solutions with no luck.

I tried on Mint, Fedora and now back to Ubuntu 14.04

I wanted to help you guys with more information however I'm not a Linux expert.

---

### Post by cch-harris on 2014-12-07
I as well have a MBP with BCM4331.  I have tried both Ubuntu and Fedora, and have also failed to get a steady wireless connection, and have also attempted many different fixes, with no luck.

---

### Post by abuelodelanada on 2015-02-24
> **mode7 said:**
> Fedora 20, wl driver.. same issue. Took hours to update and get it set up, too.

Thought for sure another distro would work, but this leads me back to thinking my wifi transponder is damaged or failing.

Please tell me someone else has had this issue or something. Lack of (reliable) wireless renders this computer useless.
I could use a dongle, but it kills the laptop's form factor, and more often that not cuts off the only other USB port because the idiotic hardware designers put them so close together.
Not that it's not a choice, but just a very annoying one.

What really frustrates me is I don't see ANY indication anywhere. No dmesg errors, nada. It just fails to connect (Yet still shows as connected). Is there another log somewhere??

I have the same problem!! I'm running Ubuntu 14.04

```

~ &#10095;&#10095;&#10095; lspci -nn -d 14e4:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
~ &#10095;&#10095;&#10095; sudo dmidecode -s system-product-name
MacBookPro8,1
~ &#10095;&#10095;&#10095; uname -a
Linux manolito 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
~ &#10095;&#10095;&#10095; 

```

Tesgin with 

```

$ mtr google.com

```

I see that suddenly I start loosing packets...

The same thing happends to me with OSX :(

---

### Post by abuelodelanada on 2015-03-10
> **abuelodelanada said:**
> I have the same problem!! I'm running Ubuntu 14.04

```

~ &#10095;&#10095;&#10095; lspci -nn -d 14e4:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
~ &#10095;&#10095;&#10095; sudo dmidecode -s system-product-name
MacBookPro8,1
~ &#10095;&#10095;&#10095; uname -a
Linux manolito 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
~ &#10095;&#10095;&#10095; 

```

Tesgin with 

```

$ mtr google.com

```

I see that suddenly I start loosing packets...

The same thing happends to me with OSX :(


I solve it!!!!

I run:
```

$ sudo apt-get update
$ sudo apt-get --reinstall install bcmwl-kernel-source
```

and now (crossing fingers) it's working good!!

Anyway I found 2 more options to solve it:

1.- Download Broadcom driver and compile it:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

README: [http://www.broadcom.com/docs/linux_sta/README_6.30.223.248.txt](http://www.broadcom.com/docs/linux_sta/README_6.30.223.248.txt)

2.- Download Windows driver and use ndiswrapper.

Anyway, I didn't need to use options 1 and 2

---


---
title: "Wireless Not Functioning on Macbook Pro 7.1 (Tested in 12.04 &amp; 13.04)"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by bennett2 on 2013-09-12
Hi all,

I am a new Ubuntu user, ventured into the OS to check things out and quickly after seeing the layout and smoothness of the OS I have been determined to get Ubuntu to function on this computer, it seems wonderful!

Since I first installed 12.04 on my MBP (triple boot it already has Windows XP and Mac OS X) the installation was very smooth, no hitches asides from wireless and graphics (will post that in the correct section :)).  The wireless did not work when I installed 12.04, and going through "Additional Drivers" would result in all sorts of "Sorry, something went wrong" errors and would not complete the update.  Finally one day later after a few restarts and entering all sorts of fun things into my terminal based on web found fixes it installed, and then the entire computer froze when I selected my router from the list!  After a reboot it worked, and as I have been seeing major graphical distortion upon bootup (until actually in the desktop screen) I decided to install the Nvidia drivers for my 320m graphics.  Unfortunately after this happened, the computer would boot to the ubuntu loading screen with the 5 dots (this was my first time not seeing the graphical distortion) then the screen would blink bright white and shut off, computer still on.  Thus my fixed wireless was no longer relevant, and I reinstalled 12.04.

Upon reinstall of 12.04 I followed many online suggestions, to no avail.  Finally I read that one fellow had his macbook pro 7.1 work flawlessly on 13.04, so I went straight to the ubuntu site, mounted 13.04 to a USB and did a fresh install.  Naturally I was very cautious this time as I have now reinstalled ubuntu around 5 times in the past 2 days!  I havent entered any internet suggestions into my terminal window yet (asides from rfkill list, and rfkill unblock wifi). 

After fresh install of 13.04 I downloaded additional driver for Broadcom STA and it worked!  I rebooted my computer to "lock-in" the changes and once again "Wi-fi Networks" was greyed out and said "disconnected" below it, even though enable Wi-fi is checked.  I tried to move to no proprietary drivers then back to activating the Broadcom STA drivers, but this no longer fixes the problem.

Please help!  I will post the wireless log below.  If I need to clean anything up or provide any other information please let me know, I'm a total Ubuntu newbie :D.

After I typed the command to get the wireless-info txt my computer froze after pasting and returned me to a ubuntu login window I have never seen before....:confused:

Heres the txt

```

*************** info trace ***************

***** uname -a *****

Linux bennett-UbuntuMBP 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. Device [106b:008d]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:08a0] (rev a2)

***** lsusb *****

Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. 

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      No scan results


***** resolv.conf *****

nameserver 127.0.1.1
search sc.rr.com

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-30-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-30-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   13.171657] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.243543] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.294714] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   46.016067] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[   79.020056] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  122.026256] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  175.022213] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  238.020289] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  301.020401] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  364.022212] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  427.025902] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  490.018236] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  553.022125] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  616.026092] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  679.022302] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  742.026036] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  805.022267] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  868.025969] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  931.020744] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[  994.022027] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1057.021305] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1120.026095] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1183.022141] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1246.022160] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1309.022295] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1372.024202] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1435.020028] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1498.021279] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1561.016063] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1624.020143] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1687.021988] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1750.020084] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1813.020040] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1876.020091] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 1939.020114] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 2002.021940] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 2007.894284] ERROR @wl_dev_intvar_get : error (-1)
[ 2007.894289] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2016.610357] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)

****************** done ******************


```

Thanks for taking the time to read and help!

---

### Post by chili555 on 2013-09-12
Getting your device 14e4:432b going is tricky. A couple of reliable resources I've read suggest the Additional Drivers, which installs bcmwl-kernel-source, is not correct. I am not sure myself but I am happy to have a willing tester! 

First, this is one very unhappy driver!> [ 1939.020114] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 2002.021940] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 2007.894284] ERROR @wl_dev_intvar_get : error (-1)
[ 2007.894289] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2016.610357] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)Let's remove the driver and see if, by any chance, your freeze issues go away, too! Please open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot so we have a clean slate. Get a temporary wired ethernet connection and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
iwconfig
```Do you have a wireless interface, ideally wlan0? Does it scan and see networks?```
sudo iwlist wlan0 scan
```If not, let's look for troubleshooting clues here:```
dmesg | grep -e b43 -e wlan
```

---

### Post by bennett2 on 2013-09-12
Thank you so much for the reply!  I just got home and ran through the steps, first removed/purged bcmwl-kernel-source and rebooted, then followed the next 3 commands up to iwconfig.  The wireless was then re-enabled and I was able to use it...however I was wary as a reboot has removed the positive changes every time in the past.  I decided to reboot to test and indeed my wireless is gone again.  I am going to post my updated wireless-info.txt as well as the other commands:

Wireless Info

```

*************** info trace ***************

***** uname -a *****

Linux bennett-UbuntuMBP 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. Device [106b:008d]
    Kernel driver in use: b43-pci-bridge
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:08a0] (rev a2)

***** lsusb *****

Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   378693  0 
bcma                   41051  1 b43
mac80211              606457  1 b43
cfg80211              510937  2 b43,mac80211
ssb                    56986  1 b43

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     No scan results


***** resolv.conf *****

nameserver 127.0.1.1
search sc.rr.com

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

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     F6F97440A9DA6418F4C2856
alias:          bcma:m04BFid0812rev1Dcl*
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
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     14621F6EC014F731244437C
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
vermagic:       3.8.0-30-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    3.084084] ssb: Found chip with id 0x4322, rev 0x01 and package 0x0A
[    3.084094] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x17, vendor 0x4243)
[    3.084100] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x10, vendor 0x4243)
[    3.084105] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x0B, vendor 0x4243)
[    3.084111] ssb: Core 3 found: PCI (cc 0x804, rev 0x0E, vendor 0x4243)
[    3.084117] ssb: Core 4 found: USB 2.0 Device (cc 0x81A, rev 0x05, vendor 0x4243)
[    3.084122] ssb: Core 5 found: UNKNOWN (cc 0x8FF, rev 0x00, vendor 0x4243)
[    3.084128] ssb: Core 6 found: Internal Memory (cc 0x80E, rev 0x03, vendor 0x4243)
[    3.139814] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   15.062448] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   15.104130] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   19.504039] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   19.736952] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.737228] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

iwconfig:

```
bennett@bennett-UbuntuMBP:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

sudo iwlist wlan0 scan:

```
bennett@bennett-UbuntuMBP:~$ sudo iwlist wlan0 scan
wlan0     No scan results


```

dmesg | grep -e b43 -e wlan:

```
bennett@bennett-UbuntuMBP:~$ dmesg | grep -e b43 -e wlan
[   15.062448] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   15.104130] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   19.504039] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   19.736952] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.737228] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Again, thank you so much for the help and let me know if I can provide anything else to help!

-Bennett

EDIT: Now I'm back on my windows desktop, my Macbook Pro in question (running Ubuntu) is about to detonate based on the graphics going on here...attaching pics (in case they are relevant to this issue).

[ATTACH=CONFIG]246199[/ATTACH]


EDIT2: A few reboots have fixed the graphical madness going on in the above thumbnail, but the wireless issue lingers.

---

### Post by chili555 on 2013-09-13
> but the wireless issue lingers. With the ethernet detached, reboot so we have a clean slate and see if the driver loaded:```
lsmod | grep b43
```We hope we see b43, ssb, mac80211, bcma and cfg80211. If not, load it:```
sudo modprobe b43
```If that fixes it, let's load b43 automagically:```
sudo -i
echo b43 >> /etc/modules
exit
```If b43 was loaded, do you have a wireless interface, ideally wlan0?```
iwconfig
```Is the wireless switch or key combination on or off?```
rfkill list all
```Finally, are there any clues here?```
dmesg | grep -e b43 -e wlan -e 8021
```

---

### Post by bennett2 on 2013-09-13
lsmod | grep b43 returns the following result with Ethernet disconnected:

[ATTACH=CONFIG]246216[/ATTACH]

as it says b43 0, should I proceed to enter the other commands you listed?

Thank you again!

**Edit:** After my laptop was left alone for 5ish minutes the wireless is again detected and connected....now I am afraid to reboot for fear it will disable again :(

---

### Post by chili555 on 2013-09-13
> **bennett2 said:**
>  After my laptop was left alone for 5ish minutes the wireless is again detected and connected....now I am afraid to reboot for fear it will disable again :(However, that's the only way we'll know! Please proceed.

---

### Post by bennett2 on 2013-09-13
Rebooted and wireless was kicked out again, here's what I've got:

lsmod | grep b43

```
bennett@bennett-UbuntuMBP:~$ lsmod | grep b43
b43                   378693  0 
bcma                   41051  1 b43
mac80211              606457  1 b43
cfg80211              510937  2 b43,mac80211
ssb                    56986  1 b43


```

Edit: Some heavy graphical issues come and go with this rig, while typing these replies and sitting in terminal (nothing graphic's intensive).

Wireless did not automatically re-enable this time after typing that command.

Followed up with "sudo modprobe b43" which was completed after password entry, had no result to wireless.  Below is the current wireless-info.txt and iwconfig that shows, should I still proceed with the next step?

```

sudo -i 
echo b43 >> /etc/modules
exit

```

lastly here is the current result of iwconfig:

```
bennett@bennett-UbuntuMBP:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by chili555 on 2013-09-13
> should I still proceed with the next step?Yes, please:```
rfkill list all
dmesg | grep -e b43 -e wlan -e 8021
```And please post the outcome.

---

### Post by bennett2 on 2013-09-14
Ok here's what I've got:

rfkill list all:

```
bennett@bennett-UbuntuMBP:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


```

dmesg | grep -e b43 -e wlan -e 8021:

```
bennett@bennett-UbuntuMBP:~$ dmesg | grep -e b43 -e wlan -e 8021
[   14.167069] cfg80211: Calling CRDA to update world regulatory domain
[   14.254576] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   14.304063] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   14.760063] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.916641] cfg80211: World regulatory domain updated:
[   14.916644] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.916647] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.916649] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.916651] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.916652] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.916654] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.540066] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   23.773036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.773312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by varunendra on 2013-09-14
Hi !

While Dr. Chili is away, would you like to try an alternative solution?

So far, I have seen only one user reporting back that it 'worked' for him.

We can try it real quick and if it doesn't help, we can quickly clean up the mess and hide it before dr. chili can see. :P

So.. if you are willing to try a possibly newer version of the sta driver again, please post the output of -
```
apt-cache show bcmwl-kernel-source | grep Version
dpkg -s bcmwl-kernel-source
```
If everything is as expected, the second command should return a response like "bcmwl-kernel-source is not installed..."

---

### Post by bennett2 on 2013-09-16
I have been out of town and will be trying this tomorrow evening, thank you for the reply!

---


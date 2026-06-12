---
title: "Realtek RTL8723BE wifi card -no networks found!"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by lbbarber24 on 2015-05-30
Hello all, I'm Lee -'intermediate-Linux-user' with a problem.

Bought a new HP Probook 455 G2 with "OEM Ubuntu 14.04 LTS" -arrived with 12.04 LTS. Little embarrassing for eBuyer, but not a problem for me as I was going wipe and clean install -I like my partitions just so....

/Boot > 200MB > Ext2 > Primary
/       > 10GB   > Ext4 > Primary
/usr   > 40GB   > Ext4 > Primary
Swap > 2GB     > Linux-Swap > Logical
/home> to 1TB end > Ext 4 > Logical

On clean install of 14.04 LTS I had ethernet plugged in for updates etc during install which worked fine. On reboot I removed the ethernet and found that the wireless 'worked' (i.e. the card was detected fine), but no networks were found; my phone and desktop are fine with the wireless network so it's an idiosyncrasy of the laptop....

Some useful information, I've tried to be thorough as for as my knowledge goes:
```

lee@xxxxxxxx:~$ lspci | grep -i wireless
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

```
```

lee@xxxxxxx:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        C4:8E:8F:AE:A5:DB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        3C:A8:2A:DE:75:A0

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.132
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.253

    DNS:             192.168.1.253

```
```

lee@xxxxxxx:~$ nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  

```
```

lee@xxxxxxx:~$ sudo rfkill list
[sudo] password for lee: 
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```

lee@xxxxxxx:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```
```

lee@xxxxxxx:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Device or resource busy

```

Any ideas why I have a device that's correctly installed, but won't scan for or find networks?

Cheers!
 Lee
--Confused Chap From UK--

**UPDATE**
I've just found the Wireless Troubleshooting page with the diagnostic code, output follows:
```

lee@xxxxxxx:~$ sudo apt-get update; sudo apt-get install usbutils pciutils hwinfo grep rfkill; sudo lshw -C network; rfkill list; sudo iwlist scan | grep -Ei 'chan|ssid'; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nnk | grep -iA2 net; lsusb; nmcli nm status; sudo lshw -short; uname -a; sudo updatedb; dmesg | grep -E  '02:00|80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rror|rtl|RTL|rt2|RT2|rt3|RT3|rt5|RT5|rt6|RT6|rt7|RT7|usb|witch|wl';sudo dmidecode|grep -E 'anufact|roduct|erial|elease'; iwconfig; grep -E '80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl' /etc/modprobe.d/*; cat /var/lib/NetworkManager/NetworkManager.state; sudo hwinfo --netcard ; ps -aux|grep -E 'wpa|icd|etwork'; netstat -rn ; cat /etc/resolv.conf; ls -lia /boot; grep tmpfs /etc/fstab; ubuntu-support-status; sudo update-pciids; sudo update-usbids; sudo lsmod

[sudo] password for lee: 

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 3c:a8:2a:de:75:a0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.132 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:90 ioport:4000(size=256) memory:d5804000-d5804fff memory:d5800000-d5803fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: c4:8e:8f:ae:a5:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.16.0-38-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:36 ioport:3000(size=256) memory:d4800000-d4803fff
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2235]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04ca:704d Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  
H/W path        Device      Class       Description
===================================================
                            system      HP ProBook 455 G2 (L8B56ES#ABU)
/0                          bus         2235
/0/5                        memory      64KiB BIOS
/0/17                       processor   AMD A10-7300 Radeon R6, 10 Compu
/0/17/18                    memory      256KiB L1 cache
/0/17/19                    memory      4MiB L2 cache
/0/0                        memory      8GiB System Memory
/0/0/0                      memory      SODIMMProject-Id-Version: lshwRe
/0/0/1                      memory      8GiB SODIMM DDR3 Synchronous 160
/0/100                      bridge      Advanced Micro Devices, Inc. [AM
/0/100/0.2                  generic     Advanced Micro Devices, Inc. [AM
/0/100/1                    display     Kaveri
/0/100/1.1                  multimedia  Advanced Micro Devices, Inc. [AM
/0/100/3.1                  bridge      Advanced Micro Devices, Inc. [AM
/0/100/3.1/0    eth0        network     RTL8111/8168/8411 PCI Express Gi
/0/100/3.2                  bridge      Advanced Micro Devices, Inc. [AM
/0/100/3.2/0    wlan0       network     RTL8723BE PCIe Wireless Network 
/0/100/3.4                  bridge      Advanced Micro Devices, Inc. [AM
/0/100/3.4/0                generic     RTS5229 PCI Express Card Reader
/0/100/10                   bus         FCH USB XHCI Controller
/0/100/11                   storage     FCH SATA Controller [AHCI mode]
/0/100/12                   bus         FCH USB OHCI Controller
/0/100/12.2                 bus         FCH USB EHCI Controller
/0/100/13                   bus         FCH USB OHCI Controller
/0/100/13.2                 bus         FCH USB EHCI Controller
/0/100/14                   bus         FCH SMBus Controller
/0/100/14.2                 multimedia  FCH Azalia Controller
/0/100/14.3                 bridge      FCH LPC Bridge
/0/100/14.4                 bridge      FCH PCI Bridge
/0/100/14.5                 bus         FCH USB OHCI Controller
/0/101                      bridge      Advanced Micro Devices, Inc. [AM
/0/102                      bridge      Advanced Micro Devices, Inc. [AM
/0/103                      bridge      Advanced Micro Devices, Inc. [AM
/0/104                      bridge      Advanced Micro Devices, Inc. [AM
/0/105                      bridge      Advanced Micro Devices, Inc. [AM
/0/106                      bridge      Advanced Micro Devices, Inc. [AM
/0/107                      bridge      Advanced Micro Devices, Inc. [AM
/0/108                      bridge      Advanced Micro Devices, Inc. [AM
/0/109                      bridge      Advanced Micro Devices, Inc. [AM
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/sda    disk        1TB HGST HTS541010A9
/0/1/0.0.0/1    /dev/sda1   volume      200MiB Linux filesystem partitio
/0/1/0.0.0/2    /dev/sda2   volume      10000MiB EXT4 volume
/0/1/0.0.0/3    /dev/sda3   volume      48GiB EXT4 volume
/0/1/0.0.0/4    /dev/sda4   volume      872GiB Extended partition
/0/1/0.0.0/4/5  /dev/sda5   volume      2000MiB Linux swap / Solaris par
/0/1/0.0.0/4/6  /dev/sda6   volume      870GiB Linux filesystem partitio
/0/2            scsi1       storage     
/0/2/0.0.0      /dev/cdrom  disk        DVDRW  SU208GB
/1                          power       VI04040XL
Linux ubuntubox 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[    0.000000] DMI: Hewlett-Packard HP ProBook 455 G2/2235, BIOS M75 Ver. 01.09 12/04/2014
[    0.000000] AGP: No AGP bridge found
[    0.000000] No NUMA configuration found
[    0.000000] AGP: No AGP bridge found
[    3.166564] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    3.182185] pci 0000:02:00.0: [10ec:b723] type 00 class 0x028000
[    3.182210] pci 0000:02:00.0: reg 0x10: [io  0x3000-0x30ff]
[    3.182240] pci 0000:02:00.0: reg 0x18: [mem 0xd4800000-0xd4803fff 64bit]
[    3.182354] pci 0000:02:00.0: supports D1 D2
[    3.182355] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.201751] usbcore: registered new interface driver usbfs
[    3.201766] usbcore: registered new interface driver hub
[    3.201916] usbcore: registered new device driver usb
[    3.214232] Switched to clocksource hpet
[    3.225391] pnp: PnP ACPI: found 7 devices
[    3.712092] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    3.735661] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    3.736725] Console: switching to colour frame buffer device 170x48
[    3.737629] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    3.737657] ACPI: Lid Switch [LID]
[    4.167530] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    4.178643] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.178645] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.178648] usb usb1: Product: EHCI Host Controller
[    4.178649] usb usb1: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    4.178651] usb usb1: SerialNumber: 0000:00:12.2
[    4.179045] hub 1-0:1.0: USB hub found
[    4.179829] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    4.190635] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.190638] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.190640] usb usb2: Product: EHCI Host Controller
[    4.190641] usb usb2: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    4.190643] usb usb2: SerialNumber: 0000:00:13.2
[    4.191008] hub 2-0:1.0: USB hub found
[    4.250639] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    4.250644] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.250646] usb usb3: Product: OHCI PCI host controller
[    4.250648] usb usb3: Manufacturer: Linux 3.16.0-38-generic ohci_hcd
[    4.250650] usb usb3: SerialNumber: 0000:00:12.0
[    4.251063] hub 3-0:1.0: USB hub found
[    4.310620] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    4.310625] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.310627] usb usb4: Product: OHCI PCI host controller
[    4.310629] usb usb4: Manufacturer: Linux 3.16.0-38-generic ohci_hcd
[    4.310630] usb usb4: SerialNumber: 0000:00:13.0
[    4.311172] hub 4-0:1.0: USB hub found
[    4.370620] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    4.370625] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.370627] usb usb5: Product: OHCI PCI host controller
[    4.370629] usb usb5: Manufacturer: Linux 3.16.0-38-generic ohci_hcd
[    4.370631] usb usb5: SerialNumber: 0000:00:14.5
[    4.371042] hub 5-0:1.0: USB hub found
[    4.372184] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    4.372186] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.372188] usb usb6: Product: xHCI Host Controller
[    4.372190] usb usb6: Manufacturer: Linux 3.16.0-38-generic xhci_hcd
[    4.372191] usb usb6: SerialNumber: 0000:00:10.0
[    4.372576] hub 6-0:1.0: USB hub found
[    4.375410] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    4.375412] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.375414] usb usb7: Product: xHCI Host Controller
[    4.375415] usb usb7: Manufacturer: Linux 3.16.0-38-generic xhci_hcd
[    4.375417] usb usb7: SerialNumber: 0000:00:10.0
[    4.375750] hub 7-0:1.0: USB hub found
[    4.382446] Loaded X.509 cert 'Magrathea: Glacier signing key: c284edaccf0b473652c34d23bec356944236e63b'
[    4.434782] tpm_tis 00:06: A TPM error (7) occurred attempting to read a pcr value
[    4.434789] ima: No TPM chip found, activating TPM-bypass!
[    4.436371] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.499047] r8169 0000:01:00.0 eth0: RTL8168g/8111g at 0xffffc9000001e000, 3c:a8:2a:de:75:a0, XID 10900800 IRQ 90
[    4.499050] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    4.750633] usb 1-5: new high-speed USB device number 3 using ehci-pci
[    4.947346] usb 1-5: New USB device found, idVendor=04ca, idProduct=704d
[    4.947351] usb 1-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    4.947353] usb 1-5: Product: HP HD Webcam
[    4.947355] usb 1-5: Manufacturer: DEFSU019I7Z5PT
[    4.947357] usb 1-5: SerialNumber: 200901010001
[    5.218644] usb 3-3: new full-speed USB device number 2 using ohci-pci
[    5.380734] usb 3-3: No LPM exit latency info found, disabling LPM.
[    5.402736] usb 3-3: New USB device found, idVendor=0bda, idProduct=b001
[    5.402741] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.402744] usb 3-3: Product: Bluetooth Radio 
[    5.402746] usb 3-3: Manufacturer: Realtek 
[    5.402748] usb 3-3: SerialNumber: 00e04c000001
[    5.728145] Switched to clocksource tsc
[    8.402012] input: HP Wireless hotkeys as /devices/virtual/input/input12
[    8.416077] lp: driver loaded but no devices found
[    8.470138] cfg80211: Calling CRDA to update world regulatory domain
[    8.524564] fb: switching to radeondrmfb from VESA VGA
[    8.524600] Console: switching to colour dummy device 80x25
[    8.533316] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    8.554490] usbcore: registered new interface driver btusb
[    8.572440] uvcvideo: Found UVC 1.00 device HP HD Webcam (04ca:704d)
[    8.579099] input: HP HD Webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input14
[    8.579602] usbcore: registered new interface driver uvcvideo
[    8.622229] lis3lv02d: 8 bits 3DC sensor found
[    8.700849] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.701223] rtlwifi: wireless switch is on
[    8.797829] cfg80211: World regulatory domain updated:
[    8.797835] cfg80211:  DFS Master region: unset
[    8.797839] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    8.797844] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    8.797849] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    8.797853] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    8.797856] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    8.797859] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    8.854195] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[    9.204416] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   11.055647] Console: switching to colour frame buffer device 170x48
[   11.085757] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input17
[   11.106591] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   11.106600] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.106604] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   11.106608] sound hdaudioC1D0:    mono: mono_out=0x0
[   11.106611] sound hdaudioC1D0:    inputs:
[   11.106615] sound hdaudioC1D0:      Mic=0x19
[   11.106618] sound hdaudioC1D0:      Internal Mic=0x12
[   11.119821] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input18
[   11.120010] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input19
[   17.349902] r8169 0000:01:00.0 eth0: link down
[   17.349943] r8169 0000:01:00.0 eth0: link down
[   17.350020] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.828779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.724546] vboxdrv: Found 4 processor cores.
[   18.943962] vboxpci: IOMMU found
[   19.043485] r8169 0000:01:00.0 eth0: link up
[   19.043503] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.280655] audit: type=1400 audit(1433028271.335:68): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/etc/dconf/profile/gdm" pid=1609 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[36274.003084] r8169 0000:01:00.0 eth0: link down
[36298.359838] r8169 0000:01:00.0 eth0: link up
    Release Date: 12/04/2014
        Serial services are supported (int 14h)
    Manufacturer: Hewlett-Packard
    Product Name: HP ProBook 455 G2
    Serial Number: CND513922Z
    Manufacturer: Hewlett-Packard
    Product Name: 2235
    Serial Number: PELTDI51V8JXBG
    Manufacturer: Hewlett-Packard
    Serial Number: CND513922Z
    Manufacturer: AMD Corporation
    Serial Number: NotSupport
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Manufacturer: Micron
    Serial Number: 0EADA982
    Manufacturer: 33-22
    SBDS Serial Number: 78B7
    SBDS Manufacture Date: 2015-01-15
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

/etc/modprobe.d/alsa-base.conf:install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci
/etc/modprobe.d/blacklist.conf:blacklist eth1394
/etc/modprobe.d/blacklist.conf:# replaced by p54pci
/etc/modprobe.d/blacklist.conf:blacklist prism54
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist bcm43xx
/etc/modprobe.d/blacklist-oss.conf:blacklist uart6850
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
/etc/modprobe.d/iwlwifi.conf:&& /sbin/modprobe -r mac80211
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
sudo: hwinfo: command not found
root       885  0.0  0.1 345060 12376 ?        Ssl  00:24   0:03 NetworkManager
root      1038  0.0  0.0  30616  5072 ?        Ss   00:24   0:18 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
nobody    1134  0.0  0.0  35232  3328 ?        S    00:24   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root     19241  0.0  0.0  10236  5288 ?        S    10:28   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-952e8414-1b72-44f7-847f-a993a0d6d46a-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
lee      19785  0.0  0.0  15952  2196 pts/5    S+   12:01   0:00 grep --color=auto -E wpa|icd|etwork
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.253   0.0.0.0         UG        0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
total 60729
    2 drwxr-xr-x  4 root root     1024 May 30 16:25 .
    2 drwxr-xr-x 23 root root     4096 May 30 16:23 ..
   13 -rw-r--r--  1 root root  1207386 Jan 15 18:22 abi-3.16.0-30-generic
   23 -rw-r--r--  1 root root  1207096 May  8 11:44 abi-3.16.0-38-generic
   14 -rw-r--r--  1 root root   171768 Jan 15 18:22 config-3.16.0-30-generic
   22 -rw-r--r--  1 root root   171817 May  8 11:44 config-3.16.0-38-generic
32769 drwxr-xr-x  5 root root     1024 May 30 16:24 grub
   19 -rw-r--r--  1 root root 19444925 May 30 14:25 initrd.img-3.16.0-30-generic
   26 -rw-r--r--  1 root root 19446795 May 30 16:25 initrd.img-3.16.0-38-generic
   11 drwx------  2 root root    12288 May 30 14:17 lost+found
   15 -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
   16 -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
   17 -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
   12 -rw-------  1 root root  3511040 Jan 15 18:22 System.map-3.16.0-30-generic
   21 -rw-------  1 root root  3513313 May  8 11:44 System.map-3.16.0-38-generic
   18 -rw-r--r--  1 root root  6345120 May 30 14:18 vmlinuz-3.16.0-30-generic
   20 -rw-------  1 root root  6351952 May  8 11:44 vmlinuz-3.16.0-38-generic
Support status summary of 'ubuntubox':

You have 54 packages (2.3%) supported until February 2016 (9m)
You have 85 packages (3.6%) supported until May 2017 (3y)
You have 92 packages (3.9%) supported until February 2015 (9m)
You have 1911 packages (80.6%) supported until May 2019 (5y)

You have 3 packages (0.1%) that can not/no longer be downloaded
You have 227 packages (9.6%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
Downloaded daily snapshot dated 2015-05-31 03:15:01
--2015-05-31 12:01:48--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org (www.linux-usb.org)... 216.34.181.97
Connecting to www.linux-usb.org (www.linux-usb.org)|216.34.181.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 547006 (534K) [text/plain]
Saving to: &#8216;/var/lib/usbutils/usb.ids.new&#8217;

100%[==============================>] 547,006      440KB/s   in 1.2s   

2015-05-31 12:01:50 (440 KB/s) - &#8216;/var/lib/usbutils/usb.ids.new&#8217; saved [547006/547006]

Done.
Module                  Size  Used by
nls_iso8859_1          12713  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               405920  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69509  8 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     47548  1 
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
arc4                   12608  2 
kvm                   452088  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
joydev                 17393  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
serio_raw              13483  0 
snd_hwdep              17698  1 snd_hda_codec
snd_seq_midi           13564  0 
media                  21903  2 uvcvideo,videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_rawmidi            30876  1 snd_seq_midi
k10temp                13144  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
edac_core              56549  0 
edac_mce_amd           22578  0 
i2c_piix4              22166  0 
btusb                  32497  0 
bluetooth             446409  22 bnep,btusb,rfcomm
radeon               1412941  4 
rtl8723be              85054  0 
6lowpan_iphc           18702  1 bluetooth
btcoexist              50304  1 rtl8723be
rtsx_pci_ms            18168  0 
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                64255  2 rtl_pci,rtl8723be
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
memstick               16966  1 rtsx_pci_ms
snd_timer              29562  2 snd_pcm,snd_seq
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
ttm                    93588  1 radeon
cfg80211              494362  2 mac80211,rtlwifi
snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         61574  1 radeon
drm                   311018  7 ttm,drm_kms_helper,radeon
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
i2c_algo_bit           13413  1 radeon
wmi                    19193  1 hp_wmi
parport_pc             32741  0 
ppdev                  17671  0 
hp_accel               26034  0 
lis3lv02d              20156  1 hp_accel
lp                     17759  0 
input_polldev          14607  1 lis3lv02d
video                  20128  0 
parport                42348  3 lp,ppdev,parport_pc
tpm_infineon           17131  0 
mac_hid                13227  0 
hp_wireless            12637  0 
mmc_block              36056  2 
rtsx_pci_sdmmc         23043  0 
psmouse               106610  0 
rtsx_pci               46259  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   34062  5 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169

```

Hopefully this is better info!

**UPDATE #2**
Further news... I ran the following commands and I can now SEE the wireless networks available to me:
```

lee@xxxxxxx:~$ sudo modprobe  rtl8723be msi=0
[sudo] password for lee: 
lee@xxxxxxx:~$ more /sys/module/rtl8723be/parameters/msi 
N
lee@xxxxxxx:~$ sudo modprobe -r rtl8723be
lee@xxxxxxx:~$ sudo modprobe rtl8723be msi=1
lee@xxxxxxx:~$ more /sys/module/rtl8723be/parameters/msi
Y

```

However: still doesn't connect to the selected network. It makes out like it's trying to and then tells me it's disconnected from the network...
...and so it continues.

**UPDATE #3** 
Update #2 is persistent on log-out/log-in, but not on reboot. Oh well....next!

---

### Post by lp.descamps on 2015-06-12
hello. got exactly the same stuff (got that hp from ebuyer. thought it was ubuntu compatible. hw issue free) on mate 15.04. I used lubuntu 15.04 on dell 5yrs laptop.

i tried few things but nothing worked so gave up .. it s friday .. had enough ... so i took my wifi from hp 5yrs old and stick it in the dell so now i have a good wifi but how frustrating it is 

i read your brilliant investigation but dont see how you solved it??

also, why /usr on another partition?

cheers

---

### Post by chewycwook on 2015-06-12
You can try what I was told to do.  [http://ubuntuforums.org/showthread.php?t=2282079](http://ubuntuforums.org/showthread.php?t=2282079) I replaced the stock driver, it seemed to rectify my issues.

---

### Post by lp.descamps on 2015-06-15
Hi,

i tried 
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
but no luck

what i found weird is the rtlwifi is working ok with ubuntu 15.04 on my dell old laptop but not working with my new hp 455.
same built on both
thanks

---

### Post by Pilot6 on 2015-06-15
Post output of

lspci -knn | grep Net -A2
rfkill list

on your hp455

---

### Post by lp.descamps on 2015-06-16
> **Pilot6 said:**
> Post output of

lspci -knn | grep Net -A2
rfkill list

on your hp455

```

louis@HP455G2:~$ lspci -knn | grep Net -A2
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:2231]
	Kernel driver in use: rtl8723be
louis@HP455G2:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

many thanks

---

### Post by Pilot6 on 2015-06-16
It looks OK. What does

iwconfig 

show?

---

### Post by lp.descamps on 2015-06-17
hi i will give it a go tomorrow. anything else you want me to try?

every time i m trying something i need to swap the wifi card in the laptop. thanks

---

### Post by lp.descamps on 2015-09-30
> **Pilot6 said:**
> It looks OK. What does

iwconfig 

show?

hello, sorry for the late reply. i ve re built the laptop using ubuntu 14.04 LTS

did 
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware

still not working (working fine on windows 10)

and to answer the question above. thanks

HP-455-G2:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

---

### Post by rolomonio on 2015-12-11
i have the same card, and the problem is whith the power managment, so you need to turn off.
to shut down the power managment you just write this line in the console:

***sudo echo "options rtl8723be fwlps=0">/etc/modprobe.d/rtl8723be.conf***

restart and problem solved.
i have one week without the problem.
i found the solution in this page:
[https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset)

---

### Post by jeremy31 on 2015-12-11
> **rolomonio said:**
> i have the same card, and the problem is whith the power managment, so you need to turn off.
to shut down the power managment you just write this line in the console:

***sudo echo "options rtl8723be fwlps=0">/etc/modprobe.d/rtl8723be.conf***

restart and problem solved.
i have one week without the problem.
i found the solution in this page:
[https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset)

Pilot6 said his PPA had that option enabled in the source code so you wouldn't need that command

---

### Post by lp.descamps on 2015-12-30
i did a default install for 14.04.3
then
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
then reboot
sudo echo "options rtl8723be fwlps=0">/etc/modprobe.d/rtl8723be.conf
then reboot

still not working

---

### Post by janmes2 on 2016-02-23
I had WiFi installed OK but no networks found. Also had a funny cursor.

Simply added the command instructions "iommu=soft" to grub menu and all is good.

---

### Post by paul-grundy on 2016-03-21
> **rolomonio said:**
> i have the same card, and the problem is whith the power managment, so you need to turn off.
to shut down the power managment you just write this line in the console:

***sudo echo "options rtl8723be fwlps=0">/etc/modprobe.d/rtl8723be.conf***

restart and problem solved.
i have one week without the problem.
i found the solution in this page:
[https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset)

Thank you for this.  Worked a treat!!!   Joined the forum just to say this.   :D

---


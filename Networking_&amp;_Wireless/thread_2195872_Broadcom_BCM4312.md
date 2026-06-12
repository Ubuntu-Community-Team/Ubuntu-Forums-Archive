---
title: "Broadcom BCM4312"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by c3369091 on 2013-12-26
Hi, I've been trying for the past 3 or so hours to get wireless set up. Im running 12.04 on an old Dell inspiron 1720. It uses Broadcom STA drivers. Ethernet works fine.

If i try and install the driver using the user interface I get: Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

Ive also read about 10 or so threads and tried all the commands to get it working, such as: 

```
 sudo apt-get purge bcmwl-kernel-source
```

```
 sudo apt-get install firmware-b43-installer
```

```


sudo apt-get install firmware-b43-lpphy-installer


```

```
sudo apt-get install firmware-b43legacy-installer
```

and 

```
sudo apt-get install b43-fwcutter
```

among others.

After running these, wireless networks do not appear.

Thanks in advance, help will be much appreciated.

---

### Post by wildmanne39 on 2013-12-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by c3369091 on 2013-12-26
alright:
```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f2]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 003 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 008: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 009: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ssb                    57842  1 b44

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1



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


***** resolv.conf *****

nameserver 127.0.0.1
search no-domain-set.bellcanada

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

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.312294] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.312317] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.312335] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.312353] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.312371] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.379090] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    2.433826] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    2.433839] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.433850] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.433857] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.472168] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.493691] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   22.301877] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   22.344089] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   29.808120] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   35.360898] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.362731] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  144.804218] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  144.804224] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[  261.760337] b44 ssb1:0 eth0: powering down PHY
[  261.844131] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[  261.844152] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[  261.844170] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[  261.844188] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[  261.844206] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[  261.908211] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[  261.944122] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[  261.944138] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[  261.944149] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[  261.944160] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[  261.984185] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[  262.004626] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[  265.804202] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  265.804208] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 1275.060346] b44 ssb1:0 eth0: powering down PHY
[ 1275.228180] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[ 1275.228206] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[ 1275.228226] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[ 1275.228247] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[ 1275.228273] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[ 1275.292403] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[ 1275.504224] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[ 1275.504242] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[ 1275.504253] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[ 1275.504263] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[ 1275.545392] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 1275.564978] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[ 1279.816412] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 1279.816422] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 1912.816313] b44 ssb1:0 eth0: Link is down
[ 1978.816229] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 1978.816239] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 2813.816305] b44 ssb1:0 eth0: Link is down
[ 2870.816235] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 2870.816241] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 2999.181202] b44 ssb1:0 eth0: powering down PHY
[ 2999.264152] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[ 2999.264174] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[ 2999.264192] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[ 2999.264210] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[ 2999.264228] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[ 2999.328900] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[ 2999.368091] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[ 2999.368103] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[ 2999.368111] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[ 2999.368119] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[ 2999.408160] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 2999.428603] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[ 3003.816366] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 3003.816376] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 5623.816230] b44 ssb1:0 eth0: Link is down
[ 5861.745583] b44 ssb1:0 eth0: powering down PHY
[ 5868.561699] Modules linked in: b44(F) ssb(F) nls_utf8(F) udf(F) arc4(F) snd_hda_codec_idt(F) snd_hda_intel(F) snd_hda_codec(F) i915(F) snd_hwdep(F) snd_pcm(F) snd_seq_midi(F) r852(F) snd_rawmidi(F) sm_common(F) drm_kms_helper(F) joydev(F) snd_seq_midi_event(F) nand(F) uvcvideo(F) drm(F) snd_seq(F) mtd(F) parport_pc(F) snd_timer(F) nand_ids(F) coretemp(F) ppdev(F) snd_seq_device(F) nand_bch(F) bnep(F) bch(F) videobuf2_core(F) lp(F) gpio_ich(F) psmouse(F) i2c_algo_bit(F) rfcomm(F) r592(F) snd(F) videodev(F) btusb(F) nand_ecc(F) parport(F) soundcore(F) videobuf2_vmalloc(F) memstick(F) snd_page_alloc(F) videobuf2_memops(F) dell_wmi(F) lpc_ich(F) serio_raw(F) sparse_keymap(F) bluetooth(F) video(F) dell_laptop(F) wmi(F) dcdbas(F) microcode(F) mac_hid(F) hid_generic(F) usbhid(F) hid(F) firewire_ohci(F) firewire_core(F) crc_itu_t(F) sdhci_pci(F) sdhci(F) [last unloaded: ssb]
[ 5901.816334] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 5901.816343] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

****************** done ******************
```

---

### Post by wildmanne39 on 2013-12-26
Please do:
```
sudo apt-get purge --remove bcmwl-kernel-source b43-fwcutter firmware-b43-installer firmware-b43legacy-installer firmware-b43-lpphy-installer
```
Then do:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
``` disable wired connection then reboot, if it does not connect post a new wireless info file so we can make sure the changes took effect.
Thanks

---

### Post by c3369091 on 2013-12-27
No luck.
```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f2]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   392109  0 
mac80211              630977  1 b43
cfg80211              525244  2 b43,mac80211
bcma                   41244  1 b43
ssb                    57842  2 b43,b44

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


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

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     No scan results


***** resolv.conf *****

nameserver 127.0.0.1
search no-domain-set.bellcanada

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

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.304418] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.304440] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.304458] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.304476] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.304494] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.376563] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    2.452056] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    2.452066] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.452073] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.452081] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.492178] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.512624] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   22.866205] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   22.908085] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   30.120112] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   35.641072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.642986] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  144.804220] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  144.804230] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

****************** done ******************


```

---

### Post by wildmanne39 on 2013-12-27
Make sure you have your wired connection unplugged when you try to connect by wifi.

Please set your wireless settings in network manager in the top right corner to match the screenshots.

In network manager settings make sure wireless is enabled.

Do you have internet connection by another wireless device while trying to connect with your wifi for example usb adaptor or bluetooth?
Thanks

---

### Post by c3369091 on 2013-12-27
Ethernet cable is disconnected. Both networking and wireless are enabled. No wireless (SSID's) networks are showing up/being detected despite ~5 on being displayed on my other computers, including another laptop running 12.04 (Sony). Therefore I cannot match the screen shots. The wifi symbol is also light up on the physical laptop.

---

### Post by tgalati4 on 2013-12-27
Post the output of:

```
modinfo b43
```

I'm running a BCM4311 on 12.10 and mine looks like:

tgalati4@Mint14-Extensa ~ $ modinfo b43
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     5C5408969167493023BD033
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
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

It's possible that your wireless card needs reseating.  Turn the machine off, open the acess door and gently remove and reinstall the card.  Blow out any dust.

---

### Post by c3369091 on 2013-12-27
Card most likely does not need reseating as I had connected to wireless running Vista hours beforehand.

```
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

```

---

### Post by tgalati4 on 2013-12-27
Shutdown, pull the battery for a hour, then reboot and look through /var/log/syslog to see if there are any module hiccups.  You can increase the verbosity of the b43 module by setting verbose=3.  Make sure bluetooth is turned off.

---

### Post by wildmanne39 on 2013-12-27
Please copy and paste this command and see if that helps:
```
echo "options b43 pio=1 qos=0" | sudo tee /etc/modprobe.d/b43.conf
```
this driver is usually very dependable.

---

### Post by c3369091 on 2013-12-28
> **Wild Man said:**
> Please copy and paste this command and see if that helps:
```
echo "options b43 pio=1 qos=0" | sudo tee /etc/modprobe.d/b43.conf
```
this driver is usually very dependable.

Networks are still not showing up.

---

### Post by c3369091 on 2013-12-28
> **tgalati4 said:**
> Shutdown, pull the battery for a hour, then reboot and look through /var/log/syslog to see if there are any module hiccups.  You can increase the verbosity of the b43 module by setting verbose=3.  Make sure bluetooth is turned off.

Doing a Battery pull now.

---

### Post by tgalati4 on 2013-12-28
Don't forget to add *verbose=3* to Wild Man's echo command.  Set it back to *verbose=2* when (and if) we get this solved.  I agree the b43 driver is generally pretty good even though it is a binary blob and not open source.  Unfortunately, troubleshooting such black boxes is more difficult.  Pulling the battery should reset any digital antenna trim settings and anything left over from a Vista session that could be interfering.  Don't forget to reboot your wireless router as well.

---

### Post by c3369091 on 2013-12-28
Rebooted router, battery puled >5 hrs, entered into terminal:

```
echo "options b43 pio=1 qos=0 verbose=3" | sudo tee /etc/modprobe.d/b43.conf


```

Still not picking up the networks.



Not going be able to do anything with the laptop for a week, so leave thread open (not yet solved).

---

### Post by c3369091 on 2014-02-14
Bump. Stiill not solved.

---

### Post by chili555 on 2014-02-14
Let's see: ```
rfkill list all
dmesg | grep -e b43 -e ssb
```Thanks.

---

### Post by c3369091 on 2014-02-14
I just now managed to get it working by entering the ssid as a hidden network (which it is not).

Much thanks to all who helped me (weeks back).

---


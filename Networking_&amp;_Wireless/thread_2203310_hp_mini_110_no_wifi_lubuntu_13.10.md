---
title: "hp mini 110 no wifi lubuntu 13.10"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by nitkov on 2014-02-02
Hi everyone,
I have installed lubuntu 13.10 on my hp mini 110. The problem is that I don't have wifi. What I mean by that is that wifi light in from of laptop stays red all the time(it should turn blue when wifi is on). I have tried to manually push the button to the left but to no avail, light stays red and wireless icon in right lower corner is grayed out without any options for wireless. I can connect with wire but I want to enable wireless. I have checked out few threads here but to no avail. Any help would be appreciate it.

---

### Post by varunendra on 2014-02-02
Welcome to the forums nitkov !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by nitkov on 2014-02-02
Sorry, that don't look right, let me try it again
```

*************** info trace ***************

***** uname -a *****

Linux z-HP-Mini-110-1100 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: b43-pci-bridge
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 001 Device 004: ID cd12:ef18  
Bus 001 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. RTS5159 Card Reader Controller
Bus 001 Device 002: ID 10f1:1a13 Importek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   356285  0 
bcma                   40966  1 b43
mac80211              513247  1 b43
cfg80211              401436  2 b43,mac80211
ssb                    51596  1 b43

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.49
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****

nameserver 127.0.1.1
search Belkin

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     9B797CFD1C70935B62C35EE
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
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 
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

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
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
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[    1.692217] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    1.692248] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.692275] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.692299] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.692324] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.748513] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[   17.208616] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   17.286513] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   19.635599] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   19.635802] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   19.636054] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

****************** done ******************


```

---

### Post by Iowan on 2014-02-02
At the bottom right of your post is a group of "buttons". 
You can use the "Edit Post" button to change an existing post. :)

---

### Post by nitkov on 2014-02-02
Thank you lowan, I thought I have posted twice but I guess I did not and this last post has come out right

---

### Post by nitkov on 2014-02-02
Thank you varunedra

---

### Post by varunendra on 2014-02-02
```

[   19.635599] b43-phy0 ERROR: [COLOR="#FF0000"]Firmware file "b43/ucode15.fw" not found[/COLOR]
[   19.635802] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   19.636054] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

While being connected via cable, please run the following command in a terminal to install the required firmware -
```
sudo apt-get install firmware-b43-lpphy-installer
```
..then either reboot, or manually reload the driver -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```
Is the WiFi working now?

---

### Post by nitkov on 2014-02-02
ok, so I have followed the link in the last line of the report , followed their instructions for installation and my wifi is working now. Thank you guys I really appreciate your help

---

### Post by nitkov on 2014-02-02
thank you varunedra, it seems like we posted at the same time. I just followed that link at the bottom of report and followed instructions there. My wifi is working now. Thank you so much

---

### Post by varunendra on 2014-02-03
Awesome! You sure know your way around in Linux :D

Please mark the thread as [SOLVED] now that it is.

---

### Post by NerillDP on 2014-05-13
Hi, I'm new here and just wanted to say thanks to varunendra for the above assistance to enable wifi. Followed your instructions and everything worked to a tee. This looks like a great place to find the answers needed from patient and knowledgeable people. I've worked in the Microsoft IT world for several years (including help desk - which I loved BTW), and I always treated people how I would like to be treated. It's nice to see that same attitude here. Since I'm fairly new to linux et.el. I'm glad I found this place.

---

### Post by Tj_Tjarks on 2014-10-02
I am new to Lubuntu and this worked perfectly for me. Thanks!

---

### Post by varunendra on 2014-10-02
Hi Tj_Tjarks, Welcome to the forums! :)

Glad it could help you out. Be aware that the "Additional Drivers" program may offer you another driver (proprietary 'STA' driver) - DON't install that one, it is not good for your card. Just keep that in mind, and your card will keep working from now on.

Hope you'd enjoy your new OS, as well as the nice forums we have here.

Regards.

---


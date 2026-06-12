---
title: "no wifi on Power Book G4"
date: 2014-05-02
forum: Networking &amp; Wireless
---

### Post by gulmer on 2014-05-02
I'm back with new install 12.04 on my Apple PPC. No wifi, ran Varun's script. Did not install any drivers, yet.  
########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

##### kernel #####

Linux mauri-laptop 3.2.0-61-powerpc-smp #92-Ubuntu SMP Mon Mar 31 23:51:53 UTC 2014 ppc ppc ppc GNU/Linux

##### lspci #####

0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Apple Inc. AirPort Extreme [106b:004e]
	Kernel driver in use: b43-pci-bridge

0002:20:0f.0 Ethernet controller [0200]: Apple Inc. UniNorth 2 GMAC (Sun GEM) [106b:0032] (rev 80)
	Kernel driver in use: gem
	Kernel modules: sungem

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 002 Device 003: ID 05ac:030a Apple, Inc. Internal Trackpad
Bus 004 Device 002: ID 1267:004d Logic3 / SpectraVideo plc 

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            gem
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.113
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             198.60.22.2
    DNS:             198.60.22.22
    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

wlan0     14 channels in total; available frequencies :
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

##### lsmod #####

b43                   368262  0 
mac80211              472371  1 b43
cfg80211              192449  2 b43,mac80211
bcma                   26036  1 b43
ssb                    51915  1 b43

##### modinfo #####

filename:       /lib/modules/3.2.0-61-powerpc-smp/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     AD7EDC8698E96450CAACDB2
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
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.2.0-61-powerpc-smp SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.2.0-61-powerpc-smp/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     B0A62A7287CF438A6B47529
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-61-powerpc-smp SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-61-powerpc-smp/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     884A5D9F31288DA53AFA96D
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
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
vermagic:       3.2.0-61-powerpc-smp SMP mod_unload modversions 

##### modules #####

snd_powermac
apm_emu
snd-powermac
therm_adt746x

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

[/etc/modprobe.d/blacklist.local.conf]
blacklist snd-aoa-codec-tas
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-i2sbus
blacklist snd-aoa-soundbus
blacklist snd-aoa

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x106b:/sys/devices/pci0002:20/0002:20:0f.0 (gem)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0001:10/0001:10:12.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    2.201658] b43-pci-bridge 0001:10:12.0: enabling device (0004 -> 0006)
[    2.201704] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.201713] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.201722] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.201774] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.201782] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.272893] ssb: Sonics Silicon Backplane found on PCI device 0001:10:12.0
[   17.146002] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   17.267277] Registered led device: b43-phy0::tx
[   17.267507] Registered led device: b43-phy0::rx
[   17.267661] Registered led device: b43-phy0::radio
[   24.749768] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   24.749781] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   24.749788] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   24.750294] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

---

### Post by gulmer on 2014-05-02
I followed the instruction in script, went to the [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and followed that instuctions sudo apt-get install firmware-b43-installer, now I've got a icon on panel that reads "wireless connection has no connectivity".

---

### Post by Hadaka on 2014-05-02
Hi,looks like you are where you were before.
remove usb dongle then from a wired connection
connected to the inernet...pleas do
```
sudo apt-get update
sudo apt get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by gulmer on 2014-05-03
OK, done, rebooted, get a message that wifi found, need to go to network manager to make connections. I can't find a network manager. Seems like the next step would be to get a network/wireless manager to set up the wireless connection with router, password and WPA security, etc.

---

### Post by Hadaka on 2014-05-03
thats a good thing, now all you need to set up
is the network mgr stuff.
click the wireless icon upper right corner next to envelope
then click EDIT your connection and make it look like the attached.

[ATTACH=CONFIG]252792[/ATTACH][ATTACH=CONFIG]252793[/ATTACH][ATTACH=CONFIG]252794[/ATTACH]

---

### Post by gulmer on 2014-05-04
Well,well,well, as soon as I changed the panel from the bottom to the top, I got a wireless icon I could click on and put in the necessary info to connect, and now, after all that, I have a good wifi connection. Thank you for your help, now I need to get the browser(Firefox) fixed, all the page of a site does't load right away, I have to hold the left mouse button down and swipe the page to get everything to show up, weird.

---

### Post by Hadaka on 2014-05-04
Finally !!!   great glad to hear it.

---


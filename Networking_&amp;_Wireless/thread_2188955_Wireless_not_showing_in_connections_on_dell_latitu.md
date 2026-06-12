---
title: "Wireless not showing in connections on dell latitude d630"
date: 2013-11-20
forum: Networking &amp; Wireless
---

### Post by Jigawatt on 2013-11-20
It doesn't show that there are any active wireless connections on my computer. The wireless light also is not on. I did get a prompt to install drivers for it, but after a restart I still had the same problem. 

Thanks.

---

### Post by varunendra on 2013-11-20
Welcome to the forums Jigawatt !

Please open a terminal (Ctrl-Alt-T), run the following command (you may copy paste this), and post back its output -
```
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Jigawatt on 2013-11-21
Btw I cut on my laptop today, and it says wireless is enabled and my wifi light is on now. I think the code you gave me was to check and see if it was detecting it and if it had drivers and what not.Oh and its still not picking up the router in my house. Here was my reply from the terminal.

```

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

```

---

### Post by varunendra on 2013-11-21
Yeah, it was just for checking your hardware and driver. If you have an ethernet (cable) connection available to reach internet, please try -
```
sudo apt-get install linux-firmware-nonfree
```

If you don't have a cable connection available, download the linux-firmware-nonfree package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Copy it back to your Ubuntu computer and double-click to install.

Reboot and see if you can detect and connect to your router. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Jigawatt on 2013-11-21
The non free driver code did not work after a reboot. Its still not showing up. I ran the Wireless code from your signature. 
Here is the reply
```


*************** info trace ***************

***** uname -a *****

Linux hairymanback-Latitude-D630 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:31:16 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453919  2 b43,mac80211
ssb_hcd                12781  0 
bcma                   39810  1 b43
ssb                    51554  2 b43,ssb_hcd

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
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.188
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     No scan results


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

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.8.0-33-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E127A51EDC8F44D2C2A8F15
alias:          ssb:v4243id0819rev*
alias:          ssb:v4243id0817rev*
alias:          ssb:v4243id0808rev*
depends:        ssb
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.8.0-33-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.8.0-33-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.440092] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    2.440110] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    2.440121] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    2.440131] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    2.440141] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    2.504117] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   11.887815] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.928032] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   23.488058] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   23.572553] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.573368] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

---

### Post by varunendra on 2013-11-21
I can notice only two things that don't seem right to me -
> **Jigawatt said:**
> ```

***** lsmod *****

b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453919  2 b43,mac80211
**[COLOR="#FF0000"]ssb_hcd[/COLOR]**                12781  0 
bcma                   39810  1 b43
**ssb                    51554  2 b43,[COLOR="#FF0000"]ssb_hcd[/COLOR]**

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: **[COLOR="#FF0000"]eth0  [Wired connection 1][/COLOR]** -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             **[COLOR="#FF0000"]connected[/COLOR]**
  Default:           yes

```

First, the Network Manager is designed to ignore or disconnect the wireless by default if a wired connection is detected. So disconnect the cable connection and try the wireless again. It may sometimes take upto 2-4 minutes to get ready after disconnecting the cable, so you may have to wait that long before trying the wireless again.

Second, I have no idea what that ssb_hcd module is there for. If disconnecting the cable doesn't help, try this -
```
sudo modprobe -rv ssb_hcd b43 ssb
sudo modprobe -v b43
```
Then check if you can scan available networks -
```
sudo iwlist wlan0 scan
```
If yes, can you connect now?

---

### Post by Jigawatt on 2013-11-22
The first time I checked for the available networks in terminal it didnt work. I tried it again and now I am successfully running off wireless! 
Thanks Alot!!!!!

---

### Post by varunendra on 2013-11-22
Glad you sorted it out. :)

---


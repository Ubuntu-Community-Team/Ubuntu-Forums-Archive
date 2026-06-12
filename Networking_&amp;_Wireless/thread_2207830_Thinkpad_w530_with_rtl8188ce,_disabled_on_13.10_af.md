---
title: "Thinkpad w530 with rtl8188ce, disabled on 13.10 after upgrade to 3.11"
date: 2014-02-25
forum: Networking &amp; Wireless
---

### Post by tylik on 2014-02-25
My primary box, a Lenovo Thinkpad w530, dropped all references to even having wifi through network management, after an upgrade to 3.11.0-17 (Or, at least, I am now on 3.11, and had just rebooted after installing updates, and this does not appear to be a unique problem.) I'm on Kubuntu 13.10. It has a rtl8188ce wifi card, which I can still see via lspci:

```
Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

Or as described by iwconfig:

```
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
```

Relevant dmesg stuff:

```
[   23.129146] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   23.467432] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   23.467589] rtlwifi: wireless switch is on
```

and 
```

[   23.215334] realtek: No valid SSID, checking pincfg 0x40138205 for NID 0x1d
[   23.215335] realtek: Enabling init ASM_ID=0x8205 CODEC_ID=10ec0269
```

Things I have tried:

Removing and re modprob'ing rtl8192se (which contains the appropriate driver) with a variety of different tags suggested on the forum. 

Booting into an older kernel (3.9, in particular a version that had been confirmed by another user as fixing the problem). 

Compiling and installing FreedomBen's drivers, as per the instructions here: [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

Reinstalling the kernel. Reinstalling all the drivers. 

... probably a few other things. To no avail. It has been days. I haven't yet tried the 3.12 kernel, though that's probably next. When I can make more time for futzing with this.

Help? When I'm not near a wired connection I'm mostly tethering through my phone or tablet, and it's both cumbersome and a little embarrassing.

---

### Post by varunendra on 2014-02-25
Ew! That sounds very painful!

But first of all, Welcome to the fourms tylik ! :)

Since you have already tried so many things, I'm not sure I can offer any better help. But on the other hand, I also wonder if trying multiple things improperly may have further messed up the wireless. Let's try to find out.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should give us all the info to make a good start.

---

### Post by tylik on 2014-02-26
Thanks. Yeah, I've been trying to be fairly clean in my grubbing around, but, um, there was at least one late night that I can't entirely vounch for. (I didn't throw anything out of any windows, and no one has found any bodies. I count these things as victories.) If you have any ideas, please let me know. This is driving me nuts.

```


*************** info trace ***************

***** uname -a *****

Linux Sujata 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21f3]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

***** iw reg get *****

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.22.139.1    0.0.0.0         UG    0      0        0 eth1
129.22.139.0    0.0.0.0         255.255.255.128 U     1      0        0 eth1

***** lsmod *****

wl                   4207760  0 
lib80211               14381  1 wl
rtl8192ce              53550  0 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
rtl8192c_common        48877  1 rtl8192ce
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              480503  3 wl,mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         129.22.139.88
    Prefix:          25 (255.255.255.128)
    Gateway:         129.22.139.1

    DNS:             129.22.104.25
    DNS:             129.22.4.32
    DNS:             129.22.104.132
    DNS:             129.22.4.31



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.1.1
search cwru.edu

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

filename:       /lib/modules/3.11.0-17-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8F7DAD3B5887F2048AC7550
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     817F63398F5E31706193BFC
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E6EB1F4DDC335E171E2711F
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   20.434348] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   20.574459] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.574594] rtlwifi: wireless switch is on
[   21.336350] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.337806] wl: module verification failed: signature and/or required key missing - tainting kernel
[   25.232643] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   25.784852] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.785079] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.786492] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[42630.803600] rtlwifi: wireless switch is on
[42631.106517] usb 1-1.2: device firmware changed
[42673.185504] rtlwifi: wireless switch is on
[52765.389433] rtlwifi: wireless switch is on
[52768.601138] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[52768.601171] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[54176.344998] e1000e: eth1 NIC Link is Down
[62692.240802] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

****************** done ******************

```

---

### Post by varunendra on 2014-02-26
Erm.. please explain -
> **tylik said:**
> ```

***** lsmod *****

**[COLOR="#FF0000"]wl [/COLOR]**                  4207760  0 
lib80211               14381  1 wl
rtl8192ce              53550  0 
....
cfg80211              480503  3 **[COLOR="#FF0000"]wl[/COLOR]**,mac80211,rtlwifi

....

***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (**[COLOR="#FF0000"]iwl4965[/COLOR]**)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```
what is "wl" doing up there, and where is the iwl4965 card? Is this installation a cloned image from some other system? Has it undergone some hardware change? Please explain in detail if possible.

In the meanwhile, please try the simple fixes/tweaks -

**1)** Remove your current udev rules file -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
It'll be regenerated automatically, with only relevant entries. Reboot after removing it.

**2)** Try turning the Power-Management off -
```
sudo iwconfig wlan0 power off
```
I'm assuming the interface name "**wlan[COLOR="#FF0000"]1[/COLOR]**" will change to "**wlan0**" after removing the current udev rules file. If not, change the interface name in above command to whatever it is. Keep an eye on "iwconfig" output afterwards to make sure the Power Management remains off.

**3)** Try the available parameters temporarily, as suggested in this post - [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912)

**PS:**
Does your Thinkpad's BIOS have a feature called **IOMMU** ?

---

### Post by tylik on 2014-02-27
I don't think I can explain wl. Box is about a year and a half old, clean build at that time, I think I've upgraded it since then without completely flattening and rebuilding. Never used another wireless card with it. 

1) Deleted udev rules file, no change. 

2) When attempting to turn off power management I got:
 
```
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```

3) No change after trying these various parameters. (Which, in fact, I've tried before, but I was hoping.)

Oh, and I didn't see IOMMU in the BIOS anywhere.

---

### Post by varunendra on 2014-02-27
> **tylik said:**
> I don't think I can explain wl. Box is about a year and a half old, clean build at that time, I think I've upgraded it since then without completely flattening and rebuilding. Never used another wireless card with it. 
Good! Because that means we can safely get rid of the wl driver then.

Please do -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot, and retry points 2) and 3) in my previous post. If they still don't help, no problem. We still have hopes, but first try these and confirm if they seem to help or not. If not, please report back with a fresh output of wireless_script.

Since the wl driver is currently conflicting over resources with the correct driver, I'm quite hopeful that removing it should definitely help improving the situation, at least a little bit if not much.

---

### Post by tylik on 2014-02-27
No changes in any case. Here is the fresh output of wireless_script:

```


*************** info trace ***************

***** uname -a *****

Linux Sujata 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21f3]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0b05:4d03 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
6: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

***** iw reg get *****

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

***** lsmod *****

rtl8192ce              53550  0 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
rtl8192c_common        48877  1 rtl8192ce
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              480503  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.201
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


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



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.1.1

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

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8F7DAD3B5887F2048AC7550
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     817F63398F5E31706193BFC
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E6EB1F4DDC335E171E2711F
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   20.383994] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   21.491388] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   21.491537] rtlwifi: wireless switch is on
[   24.801896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.214215] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[  378.730446] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  378.730854] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  378.731188] rtlwifi: wireless switch is on
[  378.739207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  400.516641] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  400.516649] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  400.516783] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  400.516932] rtlwifi: wireless switch is on
[  400.521282] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  429.771452] rtl8192ce: rtl8192ce: Power Save off (module option)
[  429.771455] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  429.771461] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  429.771815] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  429.772161] rtlwifi: wireless switch is on
[  429.777795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  466.900214] rtl8192ce: rtl8192ce: Power Save off (module option)
[  466.900228] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  466.900452] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  466.900650] rtlwifi: wireless switch is on
[  466.905340] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  498.071431] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  498.071591] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  498.071758] rtlwifi: wireless switch is on
[  498.079333] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************

```

---

### Post by varunendra on 2014-02-27
Uh oh, the hardware switch is off, at least as per the system report -
> **tylik said:**
> ```
***** rfkill *****

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
6: **phy0: Wireless LAN**
	Soft blocked: no
	**Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**

```

Please try the switch or key combination whatever you have to toggle the wireless on/off. Check the wireless state with -
```
rfkill list
```
If the hardware switch does not change the wireless state (both hard and soft blocks to "no"), try this command -
```
sudo rfkill unblock all
```
Also check the Thinkpad's BIOS to make sure the wireless is enabled from there, and if it already is, try resetting the BIOS to defaults.

If none of these help, please post the output of -
```
lsmod
```

---

### Post by tylik on 2014-02-28
So, the hardware switch doesn't turn it on. (Weirdly, it turns off the soft blocking on bluetooth. Who knew? And yes, this is supposed to be the wifi switch.)

"Sudo rfkill unblock all" also does not reset the hardblocking. (Thanks for the command, though - I'd been wondering how to do that.)

lsmod outputs:

```
Module                  Size  Used by
cuse                   13274  3 
dm_crypt               22832  1 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  4 
bnep                   19704  2 
bluetooth             372041  10 bnep,rfcomm
binfmt_misc            17468  1 
nvidia               9451843  0 
joydev                 17377  0 
rndis_host             14503  0 
cdc_ether              14351  1 rndis_host
usbnet                 39525  2 rndis_host,cdc_ether
arc4                   12608  2 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431720  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2194 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  1099 ghash_clmulni_intel,aesni_intel,ablk_helper
mii                    13934  1 usbnet
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
wmi                    19070  0 
snd_hda_codec_realtek    56405  1 
snd_hda_intel          52267  2 
snd_hda_codec         188738  2 snd_hda_codec_realtek,snd_hda_intel
rtl8192ce              53550  0 
microcode              23656  0 
rtl_pci                26641  1 rtl8192ce
snd_hwdep              13602  1 snd_hda_codec
thinkpad_acpi          81113  1 
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
rtlwifi                63229  2 rtl_pci,rtl8192ce
nvram                  14362  1 thinkpad_acpi
rtl8192c_common        48877  1 rtl8192ce
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192ce
snd_seq_midi           13324  0 
psmouse                97655  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
serio_raw              13413  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              480503  2 mac80211,rtlwifi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
lpc_ich                21080  0 
mei_me                 18421  0 
mei                    77782  1 mei_me
snd                    69141  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
tpm_tis                19123  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
mmc_block              35880  0 
i915                  661339  2 
i2c_algo_bit           13413  1 i915
firewire_ohci          40327  0 
drm_kms_helper         52710  1 i915
ahci                   25819  2 
e1000e                254604  0 
firewire_core          64534  1 firewire_ohci
sdhci_pci              19014  0 
libahci                32009  1 ahci
sdhci                  42898  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
drm                   297056  3 i915,drm_kms_helper,nvidia
ptp                    18580  1 e1000e
pps_core               19057  1 ptp
video                  19318  1 i915
```

ETA: Oh, and in either the BIOS settings I had or the defaults, there is mention of my ethernet card, but not of a wireless card, disabled or otherwise. (And I haven't updated by bios recently. Possibly ever on this machine - if I have a chance today, I'll check to see if there is an update.)

(Thanks for all you help, BTW.)

---

### Post by varunendra on 2014-02-28
Did you check the BIOS or tried to reset it?

Some BIOS have this feature where they automatically disable the wireless as soon as an Ethernet connection is detected (although so far I have seen it only in some HP models). If your model has any such feature, make sure it is turned off. You seem to be using a USB adapter that is emulated as an Ethernet device.

There are no usual suspects in the lsmod, although there are several drivers that are strange to me (not suspicious though), and the "thinkpad_acpi" driver looks interesting. If BIOS settings or resetting BIOS altogether don't help, please post back the outputs of :
```
grep -H [[:alnum:]] /sys/module/thinkpad_acpi/parameters/*
cat /proc/cmdline
```

---

### Post by tylik on 2014-02-28
I checked the BIOS, and then reset it to defaults, and checked again (and noticed no differences related to networking, and only differences in settings I've set on purpose). The only networking setting is whether it automatically turns on networking on boot (it does). And, as I mentioned, there is a reference to the ethernet card, but not the wireless card. (OTOH, I don't remember looking closely at the BIOS networking panel in the past, so I can't say that it has changed.)

Currently, when I'm at home, I'm mostly connecting this box by tethering via USB cable to my Asus tf700t (an android convertible tablet) - or sometimes my phone. When I'm at work I'm mostly on the wired network. Having this disconnected at boot does not change the outcome that I have seen.

Of the first:
```
/sys/module/thinkpad_acpi/parameters/brightness_enable:2
/sys/module/thinkpad_acpi/parameters/brightness_mode:4
/sys/module/thinkpad_acpi/parameters/dbg_bluetoothemul:0
/sys/module/thinkpad_acpi/parameters/dbg_uwbemul:0
/sys/module/thinkpad_acpi/parameters/dbg_wlswemul:0
/sys/module/thinkpad_acpi/parameters/dbg_wwanemul:0
/sys/module/thinkpad_acpi/parameters/enable:Y
/sys/module/thinkpad_acpi/parameters/experimental:0
/sys/module/thinkpad_acpi/parameters/fan_control:N
/sys/module/thinkpad_acpi/parameters/force_load:N
/sys/module/thinkpad_acpi/parameters/hotkey_report_mode:0
/sys/module/thinkpad_acpi/parameters/id:ThinkPadEC
/sys/module/thinkpad_acpi/parameters/index:-536870912
/sys/module/thinkpad_acpi/parameters/volume_capabilities:0
/sys/module/thinkpad_acpi/parameters/volume_control:N
/sys/module/thinkpad_acpi/parameters/volume_mode:3
```

and the second:

```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=bfd025e5-2314-424e-ab79-631775f2be30 ro quiet splash vt.handoff=7
```

---

### Post by varunendra on 2014-03-01
> **tylik said:**
> 
/sys/module/thinkpad_acpi/parameters/**dbg_wlswemul:[COLOR="#FF0000"]0[/COLOR]**
[/code]

Okay, I searched, and read, and searched and read and on and on... and it seems to be a mystery with thinkpad_acpi that keeps occurring from time to time but even the developers don't seem to be very confident yet on what all the thinkpad's firmware does, when and why, or how to get around it.

===================================================
**[COLOR="#800000"][Description part for my own reference, _Skip reading_ unless you are fond of getting bored and confused][/COLOR]**
There are some helpful clues however, although not very promising. For now, after whatever I could find and read about this driver, it seems to be indeed the culprit for the wireless hardblocked state, and for most part, it is a big Thanks to the weird ways lenovo/ibm does things which are almost never helpful, just "different" (and restrictive, from a different context).

Anyway, these are the module parameters which I am interested in testing -
```

parm:           hotkey:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           cmos:Simulates thinkpad-acpi procfs command at module load, see documentation
[B]parm:           dbg_wlswemul:Enables WLSW emulation (uint)
parm:           wlsw_state:Initial state of the emulated WLSW switch (bool)[/B]
parm:           dbg_uwbemul:Enables UWB switch emulation (uint)
parm:           uwb_state:Initial state of the emulated UWB switch (bool)

```
There are some other things that I may like to test, based on these references :
[http://www.thinkwiki.org/wiki/Thinkpad-acpi](http://www.thinkwiki.org/wiki/Thinkpad-acpi)
[http://ibm-acpi.sourceforge.net/README](http://ibm-acpi.sourceforge.net/README)

..but I'm sure that as a simple user, you would be interested in getting your wireless working, and not being someone's testing mule especially when they don't know themselves what they are doing :P

Besides, I'm not sure how far I can go with the testings since there are almost no clear references (or I couldn't find/understand them) to ensure that we are even working in the right direction.
**[COLOR="#800000"][/END of Description/Reference Part][/COLOR]**
===================================================

So, what you should try now -

First, read this thread thoroughly, try what was suggested with the hardware switch and see if we can reach the "hard blocked : no" state : [http://ubuntuforums.org/showthread.php?t=1750431](http://ubuntuforums.org/showthread.php?t=1750431)

I'd also recommend to add yourself to the "Affected" list of the bug report the OP linked to there.

If the suggestions there don't help, I would like to try something that our legendary senior Mr. Chili555 noticed and attempted 3 years ago on that thread, only a bit differently.

That is, trying a few driver parameters, only in permanent mode instead of temporary mode on a running system. Since acpi/wmi functions are often critical basic level system functions, sometimes they may not be tested correctly in 'Temporary' mode (that is - remove the driver --> reload it with a parameter on the running system). So I'd prefer to test any parameter in the permanent mode by writing it to a .conf file. Accordingly, ONLY if the suggestions in the linked thread don't help, please try this -

*(**[COLOR="#FF0000"]Important :[/COLOR]** keep a live CD/USB handy in case a wrong parameter crashes the acpi driver and Ubuntu fails to boot. We can reset that by simply deleting the .conf file using the live CD/USB. Very unlikely, but just in case..)*

Open a terminal and run (you may copy-paste) this command -
```
echo "options thinkpad_acpi dbg_wlswemul=1 wlsw_state=Y" | sudo tee /etc/modprobe.d/thinkpad_acpi.conf
```
This will create a .conf file "thinkpad_acpi.conf" in the /etc/modprobe.d directory, containing the parameters.

Reboot and check -
```
rfkill list
grep -H [[:alnum:]] /sys/module/thinkpad_acpi/parameters/*
```
Is the hard blocked gone? Does our new parameter "wlsw_state" show up in the second command's output? If yes, what is its state (value)?

Along with the above report, please also post back the output of -
```
find /proc/acpi -maxdepth 4 -type f
```

**PS:** Do not forget to try the reboot variations with the hardware switch on/off as suggested in the linked thread. Sometimes these ridiculous looking routines can do miracles, because of how ridiculously the firmware was designed or implemented.

---

### Post by tylik on 2014-03-01
Actually, I'm not averse to playing testing mule. Used to be a software engineer (though for the longest time I was a performance analyst working with high capacity internet servers, rah) and heavens knows I benefit enough from the community. If this can help nail this issue, I'm game. Or at least, as game as I have time for. (I'm working on a doctorate in neurbiology, teaching martial arts, and living in a zendo. I am not without time, but it will have to get done around the other things.)

...and speaking of time limited, I'll have to wait a few hours to get onto this, as we're having an introductory workshop fairly soon and I need to get set up for it. OTOH, if you see this in the meantime, and want to prioritize another course of action, do let me know.

---

### Post by varunendra on 2014-03-01
I started a conversation about this with Dr. chili555 in the meantime, and we think the course of action so far is okay.

However, he suggested one more command that may or may not give us something interesting. So to the list of previously requested outputs/details, please also add this one -
```
dmesg | grep -i '\<dmi\>'
```
This will capture any and all messages that contain the word "DMI" (ignoring the case), not the words like H**DMI** or **dmi**decode etc.

If no outputs appear, then just to make sure it was not the filter's fault, run a simpler form -
```
dmesg | grep -i dmi
```
..and manually discard any "HDMI" type messages.

Based on the results of these experiments, we may try a few others later..

---

### Post by tylik on 2014-03-01
Just trying that:
```
[    0.000000] DMI: LENOVO 2436CTO/2436CTO, BIOS G5ET30WW (1.08 ) 06/01/2012
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad W530
```

---

### Post by chili555 on 2014-03-01
It's about 4:00 am at Varun's house, so let me pinch-hit for a moment. Please try:```
sudo modprobe -r thinkpad_acpi
sudo rfkill unblock all
rfkill list all
```Thanks.

---

### Post by tylik on 2014-03-01
```
FATAL: Module thinkpad_acpi is in use.
```

Trying to think of a way around this...

---

### Post by chili555 on 2014-03-01
I just noticed it has a few dependencies, snd and nvram. It is possible that a few things might not work as expected  if you remove it; for example, the button that raises and lowers the volume on the keyboard might not work.  If you are willing to experiment, blacklist it:```
sudo -i
echo " blacklist thinkpad_acpi"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot.```
sudo rfkill unblock all
rfkill list all
```

If there are too many things wrong, then remove the blacklist:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove the offending line, proofread, save and close gedit. Then:```
sudo modprobe thinkpad_acpi
```

---

### Post by tylik on 2014-03-01
```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

Also, the screen light intensity control still woks, which makes me wonder if it took...

[But checking in blacklist.conf shows that it's there, and rebooting and retrying everything just shows that it's still hard-blocked.]

---

### Post by varunendra on 2014-03-01
> **chili555 said:**
> It's about 4:00 am at Varun's house, so let me pinch-hit for a moment..
Yup, it would have been around 4-4:30 am when you posted. But even now that I'm up (8:40 am now), I'd appreciate if you still don't mind holding my hands through this, I could use any and all help/ideas with this.

> **tylik said:**
> Also, the screen light intensity control still woks, which makes me wonder if it took...
Based on my experience with blacklisting of my wmi driver (asus_nb_wmi) here, I believe that is normal. Some functions (like volume control, touchpad enable/disable) stop working when I blacklist it, but the brightness control works even since the BIOS screen, so maybe it is controlled at firmware (BIOS) level.

But still, I'd like to see the part of the blacklist file that contains the blacklisting, especially if blacklisting it seems to have NO DIFFERENCE on any hotkey control. I don't know if this matters or not, but the original command suggested by dr. chili contained a space before "blacklist" -
> **chili555 said:**
> ```
echo **" b**lacklist thinkpad_acpi"  >>  /etc/modprobe.d/blacklist.conf
```
So if some functions have stopped working, you did it right and the above doesn't matter. If you notice no change in any hot key control, then probably the blacklisting didn't work.

Easy to check -
```
lsmod | grep thinkpad
```
Does it show up there? If not, blacklisting worked, and I'd suggest to try the same "physical switch" power off > reboot > power it on again > rfkill unblock commands... etc. as was suggested in the thread I linked to earlier.

Also, have you tried the driver parameters yet? If not, try them if our experiments with the blacklisting doesn't seem to produce desired results. I am willing to experiment with all six parameters I had quoted, but the suggested two look most promising.

---

### Post by tylik on 2014-03-02
When I went to check blacklist.conf, I noticed and removed the space, and rebooted again. 

```
lsmod | grep thinkpad
``` pulls up nothing. So I'm pretty sure it took. I don't have a volume control hot key. The hotkey to put it to sleep works, as does the hotkey to turn on the keyboard light, and the hotkey to turn on wifi hasn't worked for a while. The hotkey to turn on the camera doesn't appear to work, but then I haven't tended to use it, so I have no control to compare against. Still, thinkpad_acpi pretty clearly isn't loaded at the moment, so on that side we're good to go.

However, 
```
sudo rfkill unblock all
rfkill list all
```

still brings up

```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
```

I have tried the parameters suggested in this post: [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912) several times now, though I'm happy to repeat them if you have suggestions for using them in some other context.

---

### Post by chili555 on 2014-03-02
Please raise your right hand. Place your left hand on my copy of C/C++ Programmers Bible, autographed by Linus Torvalds, and swear that switch #5 here is set to enable wireless: [http://media.cnetcontentsyndication.com/FTP/ContentCast/Lenovo/inlinecontent/laptops/thinkpad/w530/cnet_lenovo_w530_gallery_01.jpg](http://media.cnetcontentsyndication.com/FTP/ContentCast/Lenovo/inlinecontent/laptops/thinkpad/w530/cnet_lenovo_w530_gallery_01.jpg)

So help you, Linus?

---

### Post by tylik on 2014-03-02
....

....

(It would have had to be a copy of Stroustrup's C++, in terms of what I have handy. But, um, I suppose I have to take the fifth.)

Yeah, um, everything's fine here, nothing to see. 

I could just cry. (And yes, I was totally unaware of that switch, and had been attempting to use the hotkey.)

---


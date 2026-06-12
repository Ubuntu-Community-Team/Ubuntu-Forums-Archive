---
title: "wifi not detected on Dell Inspiron n4030 laptop using ubuntu 13.10"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by amith3 on 2014-02-24
i use ubuntu 13.10 on dell inspiron n4030 laptop. i can detect wifi tethered from my phone. but ubuntu is not detecting wifi in my college(dlink wifi modem) what may be the problem?
when executing wireless script, I got this
```


*************** info trace ***************

***** uname -a *****

Linux amith-Inspiron-N4030 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
13:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Dell Device [1028:0466]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 002 Device 004: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:6488 Microdia 
Bus 001 Device 012: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 011: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 010: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 009: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

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

wl                   3999432  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              401436  1 wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

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
    Address:         192.168.42.27
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
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
WirelessEnabled=false
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

filename:       /lib/modules/3.11.0-12-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   12.777888] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.816213] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.933505] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   16.293901] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  205.668323] atl1c 0000:13:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  248.832210] atl1c 0000:13:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[ 1631.843087] ERROR @wl_dev_intvar_get : error (-1)
[ 1631.843094] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************

```

---

### Post by varunendra on 2014-02-25
Welcome to the forums Amit!

When you are in the college and the wireless networks are available, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by amith3 on 2014-03-06
I think code tag didn't work. How to use it ?

---

### Post by varunendra on 2014-03-06
You have used backslash (\) in the closing tag, use forward shash (/) instead. :)

---

### Post by amith3 on 2014-03-07
well why is the wifi not working?
any idea?

---

### Post by varunendra on 2014-03-07
Oh sorry, the apparent problem was so similar to another one I had answered probably moments before yours post that I thought I had already advised you too.

For starters, your Wireless seems to be disabled from Network Manager menu -
```
***** rfkill *****

0: phy0: Wireless LAN
    **Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    **Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
    Hard blocked: no

....<snip>....

***** NetworkManager.state *****
[main]
NetworkingEnabled=true
**WirelessEnabled=[COLOR="#FF0000"]false[/COLOR]**
WWANEnabled=true
WimaxEnabled=true
```
So make sure that "Enable Wireless" option in nm-applet menu has a tick mark before it. Click it to enable it. Then check -
```
rfkill list
```
There should be no hard or soft block on the wireless interfaces (the two quoted interfaces are actually the same card - one is usually the card, the other its indicator).

Secondly, you are using the proprietary STA driver that often doesn't work well with this card. The native one is usually better for it. To use the native one instead, purge the current one -
```
sudo apt-get purge bcmwl-kernel-source
```
The native "brcmsmac" driver will load automatically since next boot.

If these suggestions don't help the connectivity, please post the script report when you are in college network, as I asked in my first post.

---

### Post by amith3 on 2014-03-10
Thank you. use of native driver done the trick.problem is solved.

---

### Post by amith3 on 2014-03-10
i use android phone for posting.can not see any option to make thread as solved. how to do it?

---

### Post by mörgæs on 2014-03-10
It's under Thread Tools.

---

### Post by varunendra on 2014-03-10
> **mörgæs said:**
> It's under Thread Tools.
..which is the link above the top post on the page.

..Or, maybe **mörgæs** can do it for you. :p

---


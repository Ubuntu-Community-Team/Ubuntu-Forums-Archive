---
title: "WiFi Disconnects, When Connected: No Internet"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by MasterRolfe on 2013-12-11
Hi All!

I'm running 13.10, fully updated, on a Lenovo B590.  Normally, I have no issues with WiFi and Internet connections.  I've just started house-sitting someone else's place, and the WiFi connection to their router is messing me around.  I'm sure there is a working Internet connection, because the owner runs his business from his house.

My laptop can connect to the WiFi, but it won't load anything while connected.  After a while, the connection tends to disappear, and the laptop starts searching again.  Signal strength is very good, so it's not that.

I don't think it matters much, but the Internet is beamed to the house via satellite, not regular cables.  I understand this means there's a bit of a delay, but the owner's computers work fine, so my laptop should too.

I've tried a few solutions that pop up on a Google search, but none seem to work.  They all seem to be solving either the disconnecting WiFi problem, or the No Internet problem, not the two combined.

Any help would be appreciated.

---

### Post by MasterRolfe on 2013-12-11
I just connected my Android phone to the troublesome WiFi network without any problem. So the problem definitely lies in Ubuntu, but only when connecting to this one network.

---

### Post by varunendra on 2013-12-12
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by MasterRolfe on 2013-12-12
Thanks!

Here's the output. I ran the script while connected via WiFi to my cellphone generated hotspot.  I hope that won't affect anything?



```
*************** info trace ***************


***** uname -a *****


Linux Devon-Laptop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5002]
    Kernel driver in use: r8169


***** lsusb *****


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:21f4 Broadcom Corp. 
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 007: ID 12d1:1037 Huawei Technologies Co., Ltd. Ideos
Bus 001 Device 003: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


eth1      IEEE 802.11abg  ESSID:"devonrolfe"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


wl                   4207474  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              479757  1 wl


***** nm-tool *****


NetworkManager Tool


State: connected (global)


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




- Device: eth1  [devonrolfe] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Coetzer:         Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA
    TP-LINK_E618F0:  Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 84 WPA2
    *devonrolfe:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA


  IPv4 Settings:
    Address:         192.168.43.221
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1


    DNS:             192.168.43.1






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


eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"devonrolfe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A6465766F6E726F6C6665
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_E618F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000E54502D4C494E4B5F453631384630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1604051100000000000000000000000000000000000000
                    IE: Unknown: 341604051100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D4D523334323010240003312E3010420003312E301054000800060050F20400011011001E576972656C657373204E2033472F344720526F75746572204D5233343230100800020086103C000101104900140024E26002000101600000020001600100020001




***** resolv.conf *****


nameserver 127.0.0.1


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


filename:       /lib/modules/3.11.0-14-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   19.009912] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.080097] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   19.222553] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   20.715525] Bluetooth: can't load firmware, may not work correctly
[ 9302.476940] ERROR @wl_dev_intvar_get : error (-1)
[ 9302.476953] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************



```

---

### Post by varunendra on 2013-12-12
> **MasterRolfe said:**
> I ran the script while connected via WiFi to my cellphone generated hotspot.  I hope that won't affect anything?
No it won't. :)

Your wireless card usually works better with the native "brcmsmac" driver than with the proprietary one you are currently using -
```

02:00.0 Network controller [0280]: Broadcom Corporation **BCM4313** 802.11bgn Wireless Network Adapter **[14e4:4727]** (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: **[COLOR="#FF0000"]wl[/COLOR]**

```
Please try removing it, which would automatically cause the native one to load at next boot -
```
sudo apt-get purge bcmwl-kernel-source
```

Reboot after this and see if you can connect normally. If still can't, please post a fresh report of the wireless_script.

---

### Post by MasterRolfe on 2013-12-12
Cool.  I did as you said.

Now,  the troublesome network doesn't even show up as an option to connect to.  Neither does the neighbour's network that I used to be able to see.  However, if I turn on my phone's WiFi Hotspot, I can see and connect to it, but the strength of the signal is very low, even when the phone is actually lying on my laptop

Here's the output of your WiFi script.  I noticed that the line you pulled out previously is still exactly the same.  I tried running that purge command again, but it claimed the package doesn't exist.



```
*************** info trace ***************


***** uname -a *****


Linux Devon-Laptop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0608]
	Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5002]
	Kernel driver in use: r8169


***** lsusb *****


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0a5c:21f4 Broadcom Corp. 
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 011: ID 12d1:1039 Huawei Technologies Co., Ltd. Ideos (tethering mode)
Bus 001 Device 003: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  2 b43,brcmsmac
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.42.135
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129




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
  Driver:            brcmsmac
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
plugins=ifupdown,keyfile,ofono
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


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
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


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   19.137730] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   19.137764] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   19.137791] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   19.137843] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   19.150812] bcma: bus0: Bus registered
[   21.607064] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   21.607071] b43: probe of bcma0:0 failed with error -524
[   22.038357] Bluetooth: can't load firmware, may not work correctly
[   22.314079] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   22.319198] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   27.245239] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   27.245250] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   27.245860] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.247159] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  104.118123] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  104.118144] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  104.118850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  136.897110] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  136.897133] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  136.897830] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.304626] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  145.304638] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  145.305288] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  203.911958] wlan0: authenticate with <MAC address removed>
[  203.914383] wlan0: send auth to <MAC address removed> (try 1/3)
[  203.925282] wlan0: authenticated
[  203.925457] brcmsmac bcma0:0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  203.929451] wlan0: associate with <MAC address removed> (try 1/3)
[  203.943564] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  203.944233] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  203.944237] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  203.944245] wlan0: associated
[  203.944271] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  204.470201] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  221.182134] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[  221.184030] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  221.185204] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  221.185221] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  264.618097] wlan0: authenticate with <MAC address removed>
[  264.620562] wlan0: send auth to <MAC address removed> (try 1/3)
[  264.627655] wlan0: authenticated
[  264.628052] brcmsmac bcma0:0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  264.629068] wlan0: associate with <MAC address removed> (try 1/3)
[  264.657100] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  264.658076] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  264.658086] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  264.658104] wlan0: associated
[  264.791375] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  281.162631] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  281.162652] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  281.162658] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  282.100077] wlan0: authenticate with <MAC address removed>
[  282.102237] wlan0: send auth to <MAC address removed> (try 1/3)
[  282.129490] wlan0: send auth to <MAC address removed> (try 2/3)
[  282.211069] wlan0: send auth to <MAC address removed> (try 3/3)
[  282.271293] wlan0: authentication with <MAC address removed> timed out
[  297.065352] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  979.472460] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  979.472471] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  979.473072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  981.219554] wlan0: authenticate with <MAC address removed>
[  981.222180] wlan0: send auth to <MAC address removed> (try 1/3)
[  981.231836] wlan0: authenticated
[  981.232427] brcmsmac bcma0:0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  981.234957] wlan0: associate with <MAC address removed> (try 1/3)
[  981.250107] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  981.250776] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  981.250780] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  981.250787] wlan0: associated
[  981.250964] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  981.376078] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1035.910489] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1035.910510] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1035.910516] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1051.357633] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

---

### Post by varunendra on 2013-12-12
I see a conflict over resources here :
```

***** lsmod *****

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
**[COLOR="#FF0000"]b43[/COLOR]**                   387185  0 
mac80211              596969  2 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac
cfg80211              479757  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac,mac80211
**[COLOR="#FF0000"]ssb                    57932  1 b43[/COLOR]**
bcma                   46670  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac

```

To me it seems like you have tried some custom changes in some system files to make the b43 driver load even though it is not correct for your card. If you wish to find the problem and fix it properly, please post back the output of -
```
egrep -v '^#|^$' /etc/{modules,rc.local}
```

Alternatively, we can 'forcibly' prevent the b43 driver from loading just like the previous driver did - by blacklisting it -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot again and see if you have any better news for me. :)

---

### Post by MasterRolfe on 2013-12-13
I did try some other fixes before I posted here.  It could be one of them that's set the driver as such.  That'll teach me to keep track of my changes. :)

Here's the output:

```
devon@Devon-Laptop:~$ egrep -v '^#|^$' /etc/{modules,rc.local}
/etc/modules:loop
/etc/modules:lp
/etc/modules:rtc
/etc/rc.local:exit 0

```
I'm going to try the blacklist option as well.  Will report on the result.

---

### Post by MasterRolfe on 2013-12-13
I did the blacklisting, and not much has changed.  Signal strengths are still pretty low.  I'm sitting right next to the troublesome router now, so I can connect, but still can't actually use the Internet,

Here's the output of the script again.  I've noticed that both the problems you highlighted earlier have changed.


```
*************** info trace ***************


***** uname -a *****


Linux Devon-Laptop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0608]
	Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5002]
	Kernel driver in use: r8169


***** lsusb *****


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:21f4 Broadcom Corp. 
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"devonrolfe"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=6 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:74   Missed beacon:0




***** rfkill *****


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


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




- Device: wlan0  [devonrolfe] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           6 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TP-LINK_E618F0:  Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 66 WPA2
    *devonrolfe:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA


  IPv4 Settings:
    Address:         192.168.43.221
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1


    DNS:             192.168.43.1






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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"devonrolfe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000008041b2d
                    Extra: Last beacon: 1116ms ago
                    IE: Unknown: 000A6465766F6E726F6C6665
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_E618F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f2ac49c9a
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000E54502D4C494E4B5F453631384630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1604051300000000000000000000000000000000000000
                    IE: Unknown: 341604051300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D4D523334323010240003312E3010420003312E301054000800060050F20400011011001E576972656C657373204E2033472F344720526F75746572204D5233343230100800020086103C000101104900140024E26002000101600000020001600100020001




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
blacklist b43
blacklist ssb


***** modinfo *****


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   17.202735] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   17.202768] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   17.202794] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   17.202847] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   17.214587] bcma: bus0: Bus registered
[   19.243715] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   19.248662] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   19.846923] Bluetooth: can't load firmware, may not work correctly
[   22.405844] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.405856] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   22.406499] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.406806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.338058] wlan0: authenticate with <MAC address removed>
[   24.342033] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.343916] wlan0: authenticated
[   24.345556] wlan0: associate with <MAC address removed> (try 1/3)
[   24.354479] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   24.355098] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   24.355101] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   24.355108] wlan0: associated
[   24.355116] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.289939] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   71.291006] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   71.291013] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   74.942938] wlan0: authenticate with <MAC address removed>
[   74.945102] wlan0: send auth to <MAC address removed> (try 1/3)
[   74.947947] wlan0: authenticated
[   74.950476] wlan0: associate with <MAC address removed> (try 1/3)
[   74.957772] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   74.958410] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   74.958414] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   74.958427] wlan0: associated
[  120.346438] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  120.347619] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  120.347636] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  124.018577] wlan0: authenticate with <MAC address removed>
[  124.020887] wlan0: send auth to <MAC address removed> (try 1/3)
[  124.023993] wlan0: authenticated
[  124.025794] wlan0: associate with <MAC address removed> (try 1/3)
[  124.129932] wlan0: associate with <MAC address removed> (try 2/3)
[  124.137389] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  124.139016] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  124.139025] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  124.139042] wlan0: associated
[  126.617061] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  126.618850] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  126.618866] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  127.454111] wlan0: authenticate with <MAC address removed>
[  127.456366] wlan0: send auth to <MAC address removed> (try 1/3)
[  127.458305] wlan0: authenticated
[  127.461405] wlan0: associate with <MAC address removed> (try 1/3)
[  127.472820] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  127.473544] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  127.473553] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  127.473570] wlan0: associated
[  152.046260] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  152.049050] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  152.049067] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  159.570246] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  159.570267] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  159.570990] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  161.307691] wlan0: authenticate with <MAC address removed>
[  161.307835] wlan0: send auth to <MAC address removed> (try 1/3)
[  161.309815] wlan0: authenticated
[  161.313066] wlan0: associate with <MAC address removed> (try 1/3)
[  161.316936] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  161.318588] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  161.318597] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  161.318613] wlan0: associated
[  161.318666] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  165.616027] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  257.617789] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  257.617809] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  257.617815] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  260.092727] wlan0: authenticate with <MAC address removed>
[  260.095076] wlan0: send auth to <MAC address removed> (try 1/3)
[  260.109201] wlan0: authenticated
[  260.112119] wlan0: associate with <MAC address removed> (try 1/3)
[  260.223023] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  260.223610] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  260.223619] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  260.223636] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  260.223664] wlan0: associated
[  368.083932] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[  368.084113] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  368.088148] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  368.088165] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  369.198782] wlan0: authenticate with <MAC address removed>
[  369.201223] wlan0: send auth to <MAC address removed> (try 1/3)
[  369.210323] wlan0: authenticated
[  369.210988] brcmsmac bcma0:0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  369.214127] wlan0: associate with <MAC address removed> (try 1/3)
[  369.241414] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  369.242431] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  369.242441] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  369.242456] wlan0: associated
[  369.428159] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)


****************** done ******************

```

---

### Post by varunendra on 2013-12-13
I can see many things that may be worth trying, unfortunately, all of them are to be made in the router. For example, the slow speed and low signal detection can be caused by an improperly implemented N-band and/or TKIP encryption. But both of these can be changed only in the router, not in the computer.

Can you try a Live CD/USB with the default driver to see how it works in the live session?

Alternatively, I am now wondering if we'd have to fall back to the sta driver. It doesn't support N-channel and has some other issues as well (with this particular card), but it seems not supporting N-channel can actually be an advantage in this case.

Please try the Live CD/USB with the default (brcmsmac) driver first if that is an available option (it is highly recommended, since a live session would be fresh, without customizations you might have made during your previous attempts).

To consider reverting back to the sta driver, let us see which versions are available. If you have a cable connection available (or other means to connect to internet), run both of the following commands. If not, skip the first one -
```
sudo apt-get update
apt-cache show bcmwl-kernel-source | grep Version
```
Post back the output of the second command above.

---

### Post by MasterRolfe on 2013-12-13
Okay.  I wasn't able to get hold of a LiveUSB.  However, I've spent the day setting up PuppyLinux on an AcerAspire One A101, and that connects perfectly to the router.  Been able to download a couple of programs.  To me this looks like the problem doesn't lie with the router, but I may be mistaken.  Now that I'm connected to the network, I could download the Live USB iso if we'd still like to try that option.

Here's the output of the second command:

```
devon@Devon-Laptop:~$ apt-cache show bcmwl-kernel-source | grep Version
Version: 6.30.223.141+bdcom-0ubuntu1

```

---

### Post by varunendra on 2013-12-14
Which driver PuppyLinux was using? I hope the following commands will work in the same way on it -
```
lspci -nnk | grep -iA2 net
lsmod
```
Their outputs will tell us about the driver currently in use, as well as all other driver that are loaded.

I'm not familiar with PuppyLinux, but I assume its package manager should also have a way to determine the driver version. If the driver turns out to be the sta driver (wl), that will come handy.

By the way, the wl driver version you got in Ubuntu is the latest one. So it should have significant improvements, but so far I don't have any proof of it working better for BCM4313 card than current versions of brcmsmac. You are the first person to report back to me that the brcmsmac is worse, so I suspect some other custom settings or broken packages in the backgrounds may be causing the trouble.

---

### Post by MasterRolfe on 2013-12-14
Puppy Linux is apparently based on Ubuntu. Here are the outputs.

```

sh-4.1# lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k

```

```

sh-4.1# lsmod
Module                  Size  Used by
joydev                  6492  0 
iptable_mangle          1189  0 
iptable_nat             2666  0 
nf_nat                 10083  1 iptable_nat
ipt_REJECT              1485  1 
nf_conntrack_ftp        4020  0 
nf_conntrack_irc        2359  0 
iptable_filter           958  1 
xt_state                 895  4 
nf_conntrack_ipv4       7063  7 iptable_nat,nf_nat
nf_conntrack           36999  6 iptable_nat,nf_nat,nf_conntrack_ftp,nf_conntrack_irc,xt_state,nf_conntrack_ipv4
nf_defrag_ipv4           755  1 nf_conntrack_ipv4
ip_tables               7321  3 iptable_mangle,iptable_nat,iptable_filter
aes_generic            25730  2 
i915                  183740  2 
drm_kms_helper         17823  1 i915
drm                   106327  3 i915,drm_kms_helper
i2c_algo_bit            3539  1 i915
usbhid                 18009  0 
fan                     2478  0 
snd_hda_codec_realtek   165209  1 
snd_hda_intel          14978  0 
snd_hda_codec          38539  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            26845  0 
snd_mixer_oss           9963  1 snd_pcm_oss
snd_pcm                45385  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy            907  0 
snd_seq_oss            18888  0 
snd_seq_midi            3156  0 
snd_rawmidi            11924  1 snd_seq_midi
arc4                     962  2 
snd_seq_midi_event      3592  2 snd_seq_oss,snd_seq_midi
ecb                     1377  2 
snd_seq                32379  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wmi                     4337  0 
fbcon                  27736  69 
snd_timer              11986  2 snd_pcm,snd_seq
snd_seq_device          3601  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tileblit                1509  1 fbcon
snd                    30859  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath5k                 105381  0 
font                    6916  1 fbcon
mac80211               99898  1 ath5k
ath                     6106  1 ath5k
soundcore               3403  1 snd
snd_page_alloc          4645  2 snd_hda_intel,snd_pcm
bitblit                 3514  1 fbcon
r8169                  25792  0 
mii                     2650  1 r8169
cfg80211               90319  3 ath5k,mac80211,ath
serio_raw               2928  0 
softcursor               805  1 bitblit
shpchp                 21148  0 
pcspkr                  1179  0 
pci_hotplug            18286  1 shpchp
led_class               1733  1 ath5k
i2c_i801                6146  0 
intel_agp              19189  1 
agpgart                18904  2 drm,intel_agp
squashfs               15984  0 
sg                     19093  0 
uhci_hcd               15444  0 
battery                 7164  0 
thermal                 9263  0 
aufs                  110466  0 
fuse                   42549  0 
nls_iso8859_1           2937  0 
nls_cp437               4465  0 
uvcvideo               44782  0 
videodev               27339  1 uvcvideo
v4l1_compat             9930  2 uvcvideo,videodev
video                  14642  1 i915
i2c_core               11497  6 i915,drm_kms_helper,drm,i2c_algo_bit,i2c_i801,videodev
output                  1120  1 video
evdev                   5517  0 
button                  3522  1 i915
ac                      2143  0 
processor              24987  2 
ehci_hcd               25830  0 
usbcore                91279  5 usbhid,uhci_hcd,uvcvideo,ehci_hcd

```

---

### Post by varunendra on 2013-12-14
Are these outputs from the same computer? The earlier one reported a Broadcom card, while this one reports an Atheros card -
> **MasterRolfe said:**
> ```

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k

```

Either the card, or the whole computer is changed. Which is the case? And which one we need to work on?

---

### Post by MasterRolfe on 2013-12-15
Sorry, I should have been a bit more clear about that. I'm setting up a whole new laptop for someone with Puppy Linux,  and that one connects flawlessly to the troublesome router.

My own laptop refuses to access the internet through that router. But since every other device I've connected to the router (Android phone, Puppy Linux) works well, I'm inclined to think the problem lies in my laptop.

That last output was from the Puppy Linux machine.

---

### Post by varunendra on 2013-12-15
Well, I can think of only 3 options for you at this point -

1) Revert to the previous driver to get to the point we started from. To install it -
```
sudo apt-get install bcmwl-kernel-source
```
..or 'Activate' the proprietary driver from "Additional Drivers" application. Both lead to the same thing - installing the sta driver again.

2) Get or create a live media (usb or cd) to test the native driver's performance and hopefully confirm a better performance to proceed further.

3) Do a fresh install, without installing "3rd party software" or "Updates" during the installation to avoid anything non-default. Then start everything fresh and only switch to the sta driver if the native one is proved to be inefficient.

I can provide plenty of pages of information worth tens of hours' reading to prove that the current settings in the router are not 'Optimal' for 'Any' driver, be it windows, osx or Linux. But neither that is going to solve anything, nor am I too much inclined to fixing those first.

Even though the router settings are not optimal, I am already suspicious of something wrong with the settings in the laptop itself and that's why we should focus on try things differently on that very laptop, not on different devices.

We may try digging up everything that can be even remotely related with wireless settings and performance, but that can be very time consuming and let me warn you, I am extremely irregular on the forums. :P

Let me know how you'd like to proceed and I'd be happy to help as long as I am available. :)

---

### Post by MasterRolfe on 2013-12-16
Ok great!  Thanks for your help!  I've reinstalled the original driver, and it looks like it's back to where we started.

I think I'm going to find myself an Ethernet cable and just connect the good old fashioned way.  I'm not going to try make changes to the router, because it isn't mine to fiddle with.

Thanks again for your help!

---


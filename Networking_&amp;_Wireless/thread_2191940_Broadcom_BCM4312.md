---
title: "Broadcom BCM4312"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by qscaxz0 on 2013-12-04
i am new to linux and i just started using ubuntu. the problem is that the laptop shows that it is connecting but always fails. could you help me?


*************** info trace ***************


***** uname -a *****


Linux stein121-Lenovo 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Lenovo Device [17aa:389e]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 5986:0241 Acer, Inc BisonCam, NB Pro
Bus 001 Device 004: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


eth1      IEEE 802.11abg  ESSID:"SINGTEL-0647"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


brcmsmac              529624  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
bcma                   40966  1 brcmsmac
mac80211              513247  1 brcmsmac
wl                   3999432  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              401436  3 wl,brcmsmac,mac80211


***** nm-tool *****


NetworkManager Tool


State: connecting


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




- Device: eth1  [SINGTEL-0647] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    SINGTEL-5010:    Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SINGTEL-A86C:    Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    kumar:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    CLTCT:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Home_Network:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WEP
    Fuzzio:          Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SINGTEL-8540:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    SINGTEL-2453:    Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Thomas:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    wireless_x:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    SINGTEL-4518:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SINGTEL-0647:    Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2






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


No way to aquire root rights found.


***** resolv.conf *****




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


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
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
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 


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






***** udev rules *****


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   13.943596] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.023544] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.340597] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[ 2614.806306] ERROR @wl_dev_intvar_get : error (-1)
[ 2614.806324] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************

---

### Post by varunendra on 2013-12-04
Welcome to the forums qscaxz0 !

Your outputs are very unusual and so is your driver configuration. Please tell us in detail what all you have tried so far, because what I can see in the outputs is a bit confusing.

The wl driver appears to be installed and loaded, but the blacklist file it creates is non-existent and a conflicting, irrelevant driver (brcmsmac) is loaded as well. Also, the modinfo part didn't show anything about the wl driver, implying that it is probably gone (did you uninstall it but didn't reboot before running the script?).

With a wired connection, please try this -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv brcmsmac
sudo modprobe -v b43
```
Can you scan and connect to wireless networks now?

If you don't have a wired connection available either, download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)
..and double-click to install, then simply reboot and see if you can connect.

And post back the outputs of -
```
egrep -v '^#|^$' /etc/modules
egrep -v '^#|^$' /etc/rc.local
```

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by qscaxz0 on 2013-12-04
thanks for helping me fix my internet problem.
for the codes u gave me i got:
egrep -v '^#|^$' /etc/modules
lp
egrep -v '^#|^$' /etc/rc.local
exit 0

---

### Post by varunendra on 2013-12-05
The outputs look fine, no entries that I suspected there might be.

Did you install the "linux-firmware-nonfree" package? Could you connect after reboot?

---

### Post by mörgæs on 2013-12-05
Moved to a new thread. Please don't add to an existing one if your hardware is different.

---


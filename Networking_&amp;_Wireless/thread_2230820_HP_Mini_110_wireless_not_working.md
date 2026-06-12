---
title: "HP Mini 110 wireless not working"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by gooberfoob on 2014-06-21
I installed Lubutu on my HP Mini 110, and the wireless does not seem to be working. The blue light on the front that indicates its on or off is currently showing to be on (blue). I have downloaded Wicd Network Manager, and downloaded the broadcom-sta from the package manager. I was reading a post on here and a user had a wireless script to download. I downloaded it and nothing seemed to of happened. I will post a link for my wireless results, the script I downloaded created a network results text file. 




########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux jhag2-HP-Mini-110-1000 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:02:19 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: wl
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Kernel driver in use: atl1c

##### lsusb #####

Bus 001 Device 002: ID 174f:1105 Syntek SM-MS/Pro-MMC-XD Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search PK5001Z

##### nm-tool #####

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
    Address:         192.168.0.138
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             205.171.2.226

- Device: wlan0 ----------------------------------------------------------------
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

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### lsmod #####

wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl

##### modinfo #####

filename:       /lib/modules/3.13.0-29-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-29-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### modules #####

lp

##### blacklist #####

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   13.046485] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.063617] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.164106] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.565225] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   40.117427] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   45.117993] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   50.117623] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   58.116444] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   88.197413] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   90.200420] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  116.239953] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  119.239186] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  127.237402] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  137.235267] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  205.307846] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  210.305021] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[36255.667603] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[36335.737629] ERROR @wl_dev_intvar_get : error (-1)
[36335.737644] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############

---

### Post by wildmanne39 on 2014-06-21
Please do:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by wildmanne39 on 2014-06-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2014-06-21
If you read the sticky at the top, you will see that you've installed the wrong driver. You seem pretty resourceful, so would you give it another look and try to fix it? If you get stuck, I'll be glad to help.

---

### Post by Hadaka on 2014-06-21
Hi, the driver you have loaded for..
BCM4312 802.11b/g LP-PHY [14e4:4315]
is not correct. With the ethernet cable attached
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #ignore any moans or groans 
```
then do.
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
you also might want to remove wicd and restore network mgr.
Boot...remove the cable and test.
thanks.\

* we all got here at once..

---

### Post by gooberfoob on 2014-06-21
I will uninstall wicd, is it just not good to use ? Before unistalling it I did use it to look up my wireless, and finally my wireless showed up, but when I put my password in and confirmed multiple time that I entered it correctly, I would get "bad password" maybe this is part of why I am being advised to remove wicd. I will set up my wifi in the network configuration (default gui application). The above recommendations have been perfect.. just still trying to get connected, also if anyone wants to teamviewer into my computer, I am ok with that. I use teamviewer all the time and I think its the beeeeeessss kneeeeesss.

---

### Post by gooberfoob on 2014-06-21
Ok, I now just dont understand why this is not working. (FRUSTERATION LEVEL 10) I love linux, but it frustrates the heck out of me when it come to getting anything network/wireless to work.

---

### Post by chili555 on 2014-06-21
Please confirm you have removed Wicd, removed bcmwl-kernel-source and installed firmware. With the ethernet detached, may we see:```
nm-tool
```

---


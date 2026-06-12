---
title: "Wifi Connects but Internet Disabled"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by bhargav2904 on 2014-04-20
Hey ,

I am new to Ubuntu. Recently installed Ubuntu Desktop 14.04 . While the installation Wifi and internet both were working fine. The problem came when i had to re-boot, after which the Wifi connected successfully though without any actual net service.
Kindly guide me through this problem. I went through many threads, nothing worked (I may have chewed on more than i could](*,))

I have a Dell Inspiron N 5010, Ubuntu 14.04 installed along with Windows 7. Hoping for some resolution to this ... 
Thanks !!!

---

### Post by kc1di on 2014-04-20
Hello bhargav2904 and welcome to Ubuntu- Please go to[ this thread ]("http://ubuntuforums.org/showthread.php?p=12350385#post12350385")and download and run the wireless script according to the instructions found there.
Then post the results here.

---

### Post by bhargav2904 on 2014-04-20
Hi kc1di,
I executed the script to and got the following result.

```
Code:
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux krbhargava-Inspiron-N5010 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 006: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 005: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 19d2:1008 ZTE WCDMA Technologies MSM K3570-Z
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6461 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


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
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: ttyUSB3  [Vodafone Vodafone Connect] ---------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1, qmi_wwan
  State:             connected
  Default:           yes


  Capabilities:


  IPv4 Settings:
    Address:         10.36.80.73
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64


    DNS:             10.169.30.244
    DNS:             10.170.30.245


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
    BEAM427570:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA


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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"BEAM427570"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A4245414D343237353730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606070000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160


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


wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


##### modules #####


lp
rtc


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


##### udev rules #####


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   16.126933] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.129709] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   16.179828] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   16.324392] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  185.184968] ERROR @wl_dev_intvar_get : error (-1)
[  185.184973] ERROR @wl_cfg80211_get_tx_power : error (-1)


########## wireless info END ############
```

---

### Post by wildmanne39 on 2014-04-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by praseodym on 2014-04-20
Hi,

> ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 [COLOR="#FF0000"]ppp0[/COLOR]
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
```
Are you connected via Modem or router? Add the login/PW of your ISP into the router interface, check the manual for that. Afterwards remove your wlan profile and create a new one in "Infrastructure" mode.

---

### Post by bhargav2904 on 2014-04-21
[COLOR=#000000]Hi praseodym,

Thanks. It Worked !! Also, i had tried changing the security Type from WPA Personal to WPA & WPA2 Personal. Thanks alot !!! [/COLOR]\\:D/

@Wildman,

Will keep your suggestion in mind. Amateur mistake.:)
Thank you.

---


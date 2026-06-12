---
title: "Acer Aspire One D270: No Wireless Connection"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by jb181991 on 2014-11-25
I have a newly installed ubuntu 14.04 LTS in my Acer Aspire ONE D270.. i tried this link [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385) but I end up nothing. I Also tried the wireless_scipt to RUN but nothing happen, still I can't connect..

when I enter the code: [FONT=lucida console]l[/FONT][FONT=lucida console][FONT=lucida console][FONT=lucida sans unicode][FONT=lucida console]spci -n | egrep '0200|0200' | awk '{print$3}'[/FONT]

[FONT=arial]the reply code would be:    [FONT=lucida sans unicode]10ec:8136

[FONT=arial]&#8203;PLEASE HELP ME..[/FONT]
[/FONT][/FONT]
[/FONT][/FONT][/FONT]

---

### Post by chili555 on 2014-11-25
The purpose of the wireless script is to gather information so we can assist you. It is not to magically diagnose and fix your wireless, although that would be awesome!

Please look in your user directory and find the file it produced. It will be  a file named wireless-info.txt or wireless-info.tar.gz. Please attach it to your reply using the paperclip tool in the reply box. Thanks.

---

### Post by grahammechanical on 2014-11-25
Nothing = Nothing. Nothing information in = Nothing advice out

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Do you at present have a wired (ethernet) connection to the router? If you do then there should be a Network Manager icon in the top panel. Click the icon. Does the drop down menu show a list of WiFi networks or wireless access points? Is there a tick mark against Enable WiFi?

If there are WiFi networks listed then that proves that the wireless adapter is switched on and that there is a driver for the wireless adapter and that the wireless adapter is scanning for wireless access points and is broadcasting to and receiving radio signals from wireless access points in range.

If Enable WiFi is not ticked then the wireless adapter is switched off. 

Simple checks that can eliminate obvious causes.

Regards.

---

### Post by praseodym on 2014-11-25
10ec:8136 is a wired device (Atheros, driver r8169). Please show

```
lspci -nnk
```

completely

---

### Post by chili555 on 2014-11-25
> **praseodym said:**
> 10ec:8136 is a wired device (Atheros, driver r8169). Please show

```
lspci -nnk
```

completelyI think the OP made a mistake with his code. I think it's supposed to be:```
 lspci -n | egrep '0200|02[COLOR="#FF0000"]8[/COLOR]0' | awk '{print$3}'
```However, the wireless_info will tell us a lot more.

---

### Post by jb181991 on 2014-11-25
ohh i'm sorry .. here it is.



```
########## wireless info START ##########


Report from: 25 Nov 2014 22:53 PHT +0800


Booted last: 25 Nov 2014 21:58 PHT +0800


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:061f]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e042]
	Kernel driver in use: wl


##### lsusb #############################


Bus 001 Device 002: ID 04f2:b367 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0951:1643 Kingston Technology DataTraveler G3
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  1 acer_wmi
video                  19476  2 acer_wmi,gma500_gfx


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.8.102  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe8b:8ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:4050
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13958 (13.9 KB)  TX bytes:123274 (123.2 KB)
          Interrupt:17 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"trams"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'trams' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.1     0.0.0.0         UG    0      0        0 wlan0
192.168.8.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search [www.smartbrosettings.net](www.smartbrosettings.net)


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [trams] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *trams:          Infra, <MAC 'trams' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 93 WPA2


  IPv4 Settings:
    Address:         192.168.8.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.8.1


    DNS:             192.168.8.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/trams]] (600 root)
[connection] id=trams | type=802-11-wireless
[802-11-wireless] ssid=trams | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Manila (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'trams' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"trams"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ERROR:102079' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ERROR:102079"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 6936ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   16.093252] usb 5-1: Direct firmware load failed with error -2
[   16.097916] Bluetooth: can't load firmware, may not work correctly
[ 2837.744876] ERROR @wl_dev_intvar_get : error (-1) (repeated 3 times)


########## wireless info END ############
```

---

### Post by chili555 on 2014-11-25
You have the same device, the same problem and require the same fix as here: [http://askubuntu.com/questions/553155/unable-to-connect-to-mixed-b-g-n-wifi-network-on-ubuntu/553253#553253](http://askubuntu.com/questions/553155/unable-to-connect-to-mixed-b-g-n-wifi-network-on-ubuntu/553253#553253)

---

### Post by jb181991 on 2014-11-25
sir, i enter the co[FONT=courier new]de lspci -nnk and [/FONT]this is the result

```

 00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf2] (rev 03)    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be2] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: gma500
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: rtsx_pci

```

---

### Post by jb181991 on 2014-11-25
> **chili555 said:**
> I think the OP made a mistake with his code. I think it's supposed to be:```
 lspci -n | egrep '0200|02[COLOR=#FF0000]8[/COLOR]0' | awk '{print$3}'
```However, the wireless_info will tell us a lot more.



here's the result of ```
lspci -n | egrep '0200|02[COLOR=#FF0000]8[/COLOR]0' | awk '{print$3}'
```


```
10ec:8136
14e4:4727
```

---

### Post by wildmanne39 on 2014-11-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jb181991 on 2014-11-25
ok sir thank you so much..

---

### Post by jb181991 on 2014-11-25
> **chili555 said:**
> You have the same device, the same problem and require the same fix as here: [http://askubuntu.com/questions/553155/unable-to-connect-to-mixed-b-g-n-wifi-network-on-ubuntu/553253#553253](http://askubuntu.com/questions/553155/unable-to-connect-to-mixed-b-g-n-wifi-network-on-ubuntu/553253#553253)

sir, it works.. THANK YOU SO MUCH..

---

### Post by mörgæs on 2014-11-25
Please mark the thread 'solved'.

---


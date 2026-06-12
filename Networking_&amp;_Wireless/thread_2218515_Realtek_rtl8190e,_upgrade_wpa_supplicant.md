---
title: "Realtek rtl8190e, upgrade wpa supplicant"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by MintyFreshLinux on 2014-04-21
How do i setup wpa_supplicant for ubuntu? I'm running a dual boot setup with windows 7 64-bit on my primary hdd and ubuntu 14.0.4 on my secondary hdd. I don't have a working internet connection as i'am for ed to use wireless. I've already tried looking up tutorials for this but theres nothing that really clarifies the installation and configuration process. Please help!

---

### Post by chili555 on 2014-04-23
As far as I know, wpa_supplicant is set up perfectly already. Simply click the Network Manager icon, see your network and connect. If that is not the case, you probably have some other problem that we should work on first. Please post the results of the wireless script here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by MintyFreshLinux on 2014-04-23
Soon after I posted this I found a tutorial on how to configure wpa_supplicant, and I did up to a point but I'm having issues connecting to my network so I will go to that link you specified and post my wpa_supplicant.conf. Thanks!

---

### Post by MintyFreshLinux on 2014-04-23
The thread you sent me is already closed, but I followed the instructions and I ran the wireless script. I'll post my results here if that's okay,



```
########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux anthony-vm 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 05)
	Subsystem: Intel Corporation Device [8086:0000]
	Kernel driver in use: e1000e


03:01.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
	Kernel driver in use: ndiswrapper
03:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]


##### lsusb #####


Bus 002 Device 004: ID 046d:0819 Logitech, Inc. Webcam C210
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 10f5:0230 Turtle Beach 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet dhcp
pre-up wpa_supplicant -Bw -Dwext -wlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


##### iwconfig #####


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    2WIRE201:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    LisaJae:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    ATT346:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    HOME-1842:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2


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


No way to aquire root rights found.


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
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


ndiswrapper           283985  0 


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### modules #####


lp
rtc
ndiswrapper


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


# PCI device 0x8086:0x10f0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8190 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   11.023828] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   11.024621] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.524790] ndiswrapper: driver net819xp (Realtek Semiconductor Corp.,07/01/2009,1677.1.0708.2009) loaded
[   12.599971] ndiswrapper: using IRQ 22
[   13.246570] wlan0: ethernet device <MAC address removed> using NDIS driver: net819xp, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8190 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8190.5.conf
[   13.246597] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   15.550988] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.551131] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############



```


Trying to connect with the GUI doesn't work, Ubuntu will start connecting and then just drop the connection.

I also tried this:
```
Sudo wpa_supplicant -wext -iwlan0 -c/etc/wpa_supplicant.conf
```

and I got this error:
 
```

Successfully initialized wpa_supplicant
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="2WIRE201" auth_failures=1 duration=10

```


Also here's my wpa_supplicant.conf
[CODE]
network={
        ssid="2WIRE201"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk="key removed"
}
[CODE]

Please help!!!

---

### Post by MintyFreshLinux on 2014-04-23
The thread you sent me is already closed, but I followed the instructions and I ran the wireless script. I'll post my results here if that's okay,



```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux anthony-vm 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 05)
    Subsystem: Intel Corporation Device [8086:0000]
    Kernel driver in use: e1000e


03:01.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
    Kernel driver in use: ndiswrapper
03:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]


##### lsusb #####


Bus 002 Device 004: ID 046d:0819 Logitech, Inc. Webcam C210
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 10f5:0230 Turtle Beach 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet dhcp
pre-up wpa_supplicant -Bw -Dwext -wlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


##### iwconfig #####


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    2WIRE201:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    LisaJae:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    ATT346:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    HOME-1842:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2


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


No way to aquire root rights found.


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
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


ndiswrapper           283985  0 


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### modules #####


lp
rtc
ndiswrapper


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


# PCI device 0x8086:0x10f0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8190 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   11.023828] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   11.024621] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.524790] ndiswrapper: driver net819xp (Realtek Semiconductor Corp.,07/01/2009,1677.1.0708.2009) loaded
[   12.599971] ndiswrapper: using IRQ 22
[   13.246570] wlan0: ethernet device <MAC address removed> using NDIS driver: net819xp, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8190 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8190.5.conf
[   13.246597] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   15.550988] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.551131] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############



```


Trying to connect with the GUI doesn't work, Ubuntu will start connecting and then just drop the connection.

I also tried this:
```
Sudo wpa_supplicant -wext -iwlan0 -c/etc/wpa_supplicant.conf
```

and I got this error:
 
```

Successfully initialized wpa_supplicant
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="2WIRE201" auth_failures=1 duration=10

```


Also here's my wpa_supplicant.conf
```

network={
        ssid="2WIRE201"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk="key removed"
}

```

Please help!!!

---

### Post by MintyFreshLinux on 2014-04-23
Sorry I was trying to edit my original post because I didn't close my code tag, don't know how I ended up posting twice

---

### Post by chili555 on 2014-04-23
> Trying to connect with the GUI doesn't work, Ubuntu will start connecting and then just drop the connection.I suspect the GUI is confused about who or what is in charge here. I'd suggest you comment out everything in /etc/network/interfaces except loopback:```
auto lo
iface lo inet loopback
#iface lo inet dhcp <-- this is way wrong, by the way.
#pre-up wpa_supplicant -Bw -Dwext -wlan0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant
```Reboot and see if the GUI, also known as Network Manager, performs better. Can you click on your network, supply the WPA2 password and connect?

I assume this is your network:> 2WIRE201:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2If this is a router over which you have administrative control, I suggest you change it to WPA2 only and not mixed mode WPA and WPA2. 

If that doesn't help, let's see:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```I will have a couple of other ideas if we are unsuccessful.

You have a very nice, neat ndiswrapper install! Usually, guys show up here with a train wreck and we have 15 posts of remedial work to do before we can start over. 

Great work so far.>  I followed the instructions and I ran the wireless script. I'll post my results here if that's okay,Perfect; that's the intent.

---

### Post by MintyFreshLinux on 2014-04-23
Okay so I changed the router from mixed mode to WPA2-PSK and I commented out those lines but I still can't connect through the GUI or the CLI. Here's my syslog.

```
anthony@anthony-vm:~$ 
anthony@anthony-vm:~$ 
anthony@anthony-vm:~$ cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
Apr 23 18:26:59 anthony-vm NetworkManager[1009]: <warn> Connection disconnected (reason -3)
Apr 23 18:26:59 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: associated -> disconnected
Apr 23 18:26:59 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 23 18:27:09 anthony-vm wpa_supplicant[1214]: wlan0: No network configuration found for the current AP
Apr 23 18:27:09 anthony-vm wpa_supplicant[1214]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=3 locally_generated=1
Apr 23 18:27:09 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: inactive -> associated
Apr 23 18:27:09 anthony-vm NetworkManager[1009]: <warn> Connection disconnected (reason -3)
Apr 23 18:27:09 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: associated -> disconnected
Apr 23 18:27:09 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 23 18:27:20 anthony-vm wpa_supplicant[1214]: wlan0: No network configuration found for the current AP
Apr 23 18:27:20 anthony-vm wpa_supplicant[1214]: wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=3 locally_generated=1
Apr 23 18:27:20 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: inactive -> associated
Apr 23 18:27:20 anthony-vm NetworkManager[1009]: <warn> Connection disconnected (reason -3)
Apr 23 18:27:20 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: associated -> disconnected
Apr 23 18:27:20 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 23 18:27:20 anthony-vm avahi-daemon[936]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr 23 18:27:20 anthony-vm avahi-daemon[936]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::208:54ff:fe9c:8b8f.
Apr 23 18:27:20 anthony-vm avahi-daemon[936]: Withdrawing address record for fe80::208:54ff:fe9c:8b8f on wlan0.
Apr 23 18:27:20 anthony-vm NetworkManager[1009]: <info> (wlan0): supplicant interface state: inactive -> disabled
Apr 23 18:27:39 anthony-vm wpa_supplicant[1214]: wlan0: Reject scan trigger since one is already pending
anthony@anthony-vm:~$ 



```

---

### Post by chili555 on 2014-04-23
Does NM list the available networks? Does it ask for the WPA2 password?

Please try this for /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid 2WIRE201
wpa-psk <your_key_in_clear_text>
```Reboot and let us see:```
iwconfig
sudo ifdown wlan0 && sudo ifup -v wlan0
dmesg | grep wlan
```The -v flag ought to give us some clues as to whats going wrong, if anything.

---

### Post by MintyFreshLinux on 2014-04-23
Should I append that code to /etc/network/interfaces or overwrite it?

---

### Post by chili555 on 2014-04-23
> **MintyFreshLinux said:**
> Should I append that code to /etc/network/interfaces or overwrite it?Overwrite it; change this:```
auto lo
iface lo inet loopback
#iface lo inet dhcp <-- this is way wrong, by the way.
#pre-up wpa_supplicant -Bw -Dwext -wlan0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant
```To this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid 2WIRE201
wpa-psk <your_key_in_clear_text>
```

---

### Post by MintyFreshLinux on 2014-04-23
dmesg | grep wlan(gedit:2382): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(gedit:2382): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
anthony@anthony-vm:~$ clear
anthony@anthony-vm:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


anthony@anthony-vm:~$ 
anthony@anthony-vm:~$ sudo ifdown wlan0 && sudo ifup -v wlan0
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1


dhclient -1 -v -pf /run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases wlan0 	
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/wlan0/00:08:54:9c:8b:8f
Sending on   LPF/wlan0/00:08:54:9c:8b:8f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0x54f4c977)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x54f4c977)

---

### Post by MintyFreshLinux on 2014-04-23
Whoops forgot to put on those code tags, sorry about that.

---

### Post by chili555 on 2014-04-23
> Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1Ugly!

Please try:```
sudo rm -rf /var/run/wpa_supplicant
sudo ifdown wlan0 && sudo ifup -v wlan0
```Any improvements?

---

### Post by MintyFreshLinux on 2014-04-23
> **chili555 said:**
> Ugly!

Please try:```
sudo rm -rf /var/run/wpa_supplicant
sudo ifdown wlan0 && sudo ifup -v wlan0
```Any improvements?


After I changed /etc/network/interfaces and rebooted Ubuntu took extra long to boot and while it was booting it said something along the lines of "getting network connections". When I got in I entered the command in the quotes about and rebooted with no change, except now Ubuntu won't scan for wireless networks at all.

---

### Post by MintyFreshLinux on 2014-04-23
Weirdest thing happened, I booted back into Ubuntu, opened firefox and I had internet, but I clocked the wireless icon and it didn't show that was connected or even scanning for any networks. I rebooted again to see if it was a fluke, and when I opened firefox I wasn't connected to the internet. I'm not exactly sure what happened. Oh to correct my last post Ubuntu says "Waiting for Network Configuration". It does this every time I reboot now.

---

### Post by MintyFreshLinux on 2014-04-23
could there be something wrong with my wpa_supplicant.conf file maybe?

---

### Post by chili555 on 2014-04-23
If you declare the wireless details in /etc/network/interfaces, Network Manager won't recognize or act on the declared interface. That's why you don't see networks in the GUI. > could there be something wrong with my wpa_supplicant.conf file maybe?Let's find out:```
sudo mv /etc/wpa_supplicant.conf /etc/wpa_supplicant.bak
```Reboot.

Any improvement?

---

### Post by MintyFreshLinux on 2014-04-23
Nope I guess there wasn't as soon as I moved the wpa_supplicant file back everything seemed to work. I'm hoping it will consistenly connect from on now. I'm wondering if the extra long startup is normal of out of the ordinary, when its saying "waiting for network configuration" and "waiting 60 more seconds for network configuration"

---

### Post by MintyFreshLinux on 2014-04-23
I rebooted two more times, the first time resulted in no connection, the second resulted in a connection and I'm logged into Ubuntu now, also the boot was super quick. I'm not sure whats happening but I'm going to guess this might be my wireless card as it sometimes disconnects while I'm in windows. But i think for the most part this problem is solved. just one question, when I boot up and my computer doesn't immdiately aquire the connection what commands can I use to connect to my network?

---

### Post by chili555 on 2014-04-23
> when I boot up and my computer doesn't immdiately aquire the connection what commands can I use to connect to my network?You will probably need:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The -v flag will let you see dhclient get an IP address instead of timing out as above...hopefully.

---

### Post by MintyFreshLinux on 2014-04-23
I figured out the flaky connection issue, it's my ISP AT&T, which I've had numerous network issues with. I'll deal with them tomorrow. But right now I have a connection and I'am ecstatic! THANK YOU SO SO MUCH!!! I never ever been able to get Linux to do wireless before and I've tried multiple times before on different machine I've owned throughout the years and gave up and never thought to ask a question on the forums. My intention was to install Linux so I can study for my Linux+ exam, but I'am just super stoked to be using Ubuntu, I feel like I did as a kid when I first started playing around with windows 98 having this brand new shiny operating system to use. So again, thank you, you are AWESOME!!! Have a great night!!!

---

### Post by chili555 on 2014-04-24
Great news! We're glad it's working now. 

There are a few of these devices out there and, as far as I know, ndiswrapper is the only way to get it going. The most daunting part of the process is finding and extracting the Windows XP .inf and .sys files. Would you please tell us where you got them, or, even better, zip them up and attach them to your reply?

---

### Post by MintyFreshLinux on 2014-04-24
> **chili555 said:**
> Great news! We're glad it's working now. 

There are a few of these devices out there and, as far as I know, ndiswrapper is the only way to get it going. The most daunting part of the process is finding and extracting the Windows XP .inf and .sys files. Would you please tell us where you got them, or, even better, zip them up and attach them to your reply?

The drivers? I got them from the Realtek site under downloads>Wireless LAN IC's>WLAN NIC>802.11n> MAC/BBP/Software>8192E>Windows driver auto installation program WinXP/VIsta

I used the 64-bit XP driver in the WinX64 folder

I also included a zip file below with the 8192E drivers. As far as that neat ndsiwrapper installation goes, I just used the .deb packages from the Debian repository and I download/installed the ndiswrapper source, dkms, common, and utils in that order.

Thank you again, being able to use Ubuntu for everyday stuff as well as for studying for that exam is really cool. I'll be installing counter strike global offensive as well, I don't know if you play games but if you do add me on steam my steam id is Deaglez_are_fun

---


---
title: "Belkin F9L1101v2 not working driver"
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by legion2 on 2014-03-15
Hey guys, i was trying to get my Belkin F9L1101 to work, did a huge job researching about the windows drivers use via ndiswrapper etc. So i reinstalled Ubuntu (i use 13.10) and did this: 
[COLOR=#000000]
[/COLOR]```
sudo apt-get install build-essential linux-headers-generic git
git clone [https://github.com/lwfinger/rtl8192du.git](https://github.com/lwfinger/rtl8192du.git)
cd rtl8192du
make
sudo make install 
sudo modprobe 8192du[COLOR=#222222][FONT=Verdana] 
[/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]But my computer is impossible to connect to internet via Ethernet because it is in different room so i had to use flash drive to manually install linux-header-generic going back and forth between my laptop and PC... 
so then the wireless networks appeared in the right top corner (the names and signal strength) like it supposed to be, but with my attempt to connect to my home network i failed: it tried to connect (the wireless network was flashing) then nothing happened, plus with my any try to iwconfic or ifconfig or anything else the terminal just hangs, same with any other sudo commands. Just need internet running on this PC. Please help guys, thanks in advance!

---

### Post by varunendra on 2014-03-16
Welcome to the forums legion2!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by legion2 on 2014-03-16
Here is what i get in the wireless_info.txt:

```



########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


##### kernel #####


Linux legion-MS-7640 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7640]
    Kernel driver in use: r8169


##### lsusb #####


Bus 003 Device 005: ID 050d:110a Belkin Components 
Bus 003 Device 006: ID 0000:0000  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 002: ID 3938:1031  
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####




##### rfkill #####




##### iw reg get #####

```

---

### Post by varunendra on 2014-03-17
The report you uploaded is incomplete. Either there is some error in the script you downloaded or some error while executing it.

Please delete the script and the current report, download the script fresh again and re-run it.

See this post for an idea of how a complete report should look like (of course yours may be quite different, but should contain all the sections as this one) : [http://ubuntuforums.org/showthread.php?t=2211426&p=12958396#post12958396](http://ubuntuforums.org/showthread.php?t=2211426&p=12958396#post12958396)

---

### Post by legion2 on 2014-03-17
I reinstalled Ubuntu and ran the script again and this time it seems to be complete:
```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux legion-MS-7640 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7640]
	Kernel driver in use: r8169


##### lsusb #####


Bus 003 Device 002: ID 050d:110a Belkin Components 
Bus 003 Device 005: ID 0000:0000  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 002: ID 3938:1031  
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
	(57240 - 63720 @ 2160), (N/A, 0)


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


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


##### lsmod #####


##### modinfo #####


##### modules #####


lp
rtc


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


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #####


########## wireless info END ############

```

---

### Post by varunendra on 2014-03-18
Please follow the same procedure as in your first post to install the 8192du driver. If it does not work, post the script report with that driver installed.

---

### Post by legion2 on 2014-03-18
So i installed the driver as above and that is the script before restart:
```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux legion-MS-7640 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7640]
	Kernel driver in use: r8169


##### lsusb #####


Bus 003 Device 002: ID 050d:110a Belkin Components 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 002: ID 3938:1031  
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0000:0000  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


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


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
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
  Driver:            rtl8192du
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    The Clubhouse:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 91 WPA
    Team Awesome:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA2
    WiFiRSU_96950:   Infra, <MAC address removed>, Freq 2447 MHz, Rate 22 Mb/s, Strength 58 WPA2
    HP-Print-BA-Deskjet 2540 series: Infra, <MAC address removed>, Freq 2412 MHz, Rate 1 Mb/s, Strength 60 WPA2
    Bunny's Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2


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


wlan0     20 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


8192du                664367  0 


##### modinfo #####


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/8192du.ko
version:        v4.2.1_7122.20130408
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5DCC204FE26766573724A5E
alias:          usb:v2019pAB2Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApE194d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p8102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp120Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp110Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DDp96A6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DDp954Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p664Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8193d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4904d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4903d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0193d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8111d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8194d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8193d*dc*dsc*dp*ic*isc*ip*in*
depends:        
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           debug:Set debug level (0-7) (default 1) (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


##### modules #####


lp
rtc


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


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192du)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[  330.464069] r8192du: Loaded firmware file rtlwifi/rtl8192dufw.bin of 32302 bytes
[  332.039560] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.040073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.061173] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.188033] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.208713] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############

```

But when i restarted the computer it took like 20 minutes to restart so i made forced restart and that is the script after restart:
```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux legion-MS-7640 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7640]
	Kernel driver in use: r8169


##### lsusb #####


Bus 003 Device 002: ID 050d:110a Belkin Components 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 002: ID 3938:1031  
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0000:0000  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####




##### rfkill #####




##### iw reg get #####

```

i guess something get stuck somewhere

---

### Post by varunendra on 2014-03-19
Yeah, apparently something did.

Please run these commands manually and post back the outputs or errors they return -
```
iwconfig
iw reg get
sudo iwlist scan
dmesg | grep rtl | tail -40
```

---

### Post by legion2 on 2014-03-19
iwconfig makes the terminal to hang, the cursor is active and you can type in stuff but the process is running obviously in the background.

---

### Post by legion2 on 2014-03-19
Should I try the same procedure with stable version of Ubuntu? Or it doesn't matter?

---

### Post by varunendra on 2014-03-19
What do you mean by "stable version"? The one you are apparently using (13.10) IS a stable version. If you mean LTS (12.04), I don't think it would make any difference, because the current point release (12.04.4) of the LTS would come with the same kernel version that is used in 13.10.

It seems the driver is causing some trouble.

When the current terminal seems to be hung, can you open a new one and run commands in it? If yes, please check dmesg -
```
dmesg | grep rtl | tail -40
```

---

### Post by legion2 on 2014-03-20
Here is the output on the second terminal:
```

[COLOR=#000000]legion@legion-MS-7640:~$ dmesg | grep rtl | tail -40
[/COLOR][    9.579526] usbcore: registered new interface driver rtl8192du
[   14.190875] r8192du: Loaded firmware file rtlwifi/rtl8192dufw.bin of 32302 bytes
[   40.208206] r8192du: Loaded firmware file rtlwifi/rtl8192dufw.bin of 32302 bytes

```

---

### Post by varunendra on 2014-03-21
Sorry, I'm lost with no hints, and am a bit short of time for a few days to dig too deep.

Could you please try the driver on a Live session? Either 12.04.4 or 13.10. If you have to download a fresh ISO, I'd recommend 12.04.4.

Keep in mind that a Live session is volatile, unless you are running it from a USB with "Persistence". So you can't test changes that require a reboot.

---


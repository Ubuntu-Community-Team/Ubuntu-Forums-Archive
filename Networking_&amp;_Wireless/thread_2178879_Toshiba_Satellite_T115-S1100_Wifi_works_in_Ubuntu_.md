---
title: "Toshiba Satellite T115-S1100: Wifi works in Ubuntu 12.04 LTS but not Lubuntu 13.04"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by rob24 on 2013-10-05
Hi all. Thanks for the help in advance. I have recently installed lubuntu 13.04 on my toshiba satellite t115-s1100. It is on a different hdd then my Ubuntu 12.04lts. I cannot get the wireless to work on my lubuntu install. I have attached the wifi stats to this thread for both installs (lspci -v, iwconfig, and lshw -c network). Ubuntu 12.04lts had no issues with my realtek rtl8187se, as it worked right away without any fiddling.

On lubuntu, it sees the network and I can attempt to connect but it always tells me the password is bad (when it is not). Even with no password I get the same. I tried Linux Mint 15 MATE and kubuntu and the same thing happened. What's going on here?

---

### Post by rob24 on 2013-10-05
I have tried installing all ndiswrapper packages and using windows xp driver. Did not work. Tried ignoring IPv6 settings. Did not work. Tried turning off router waiting 10 seconds then turning back on. Nothing. Tried MANY restarts. Nothing. Connects to via ethernet cable just fine. Got all the latest updates to see if something would help, but nothing did. Hope this adds a little more meat to my issue.

---

### Post by varunendra on 2013-10-07
Welcome to the forums rob24 !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by rob24 on 2013-10-07
Hi thanks. Here is the output. Sorry for the late reply. 

```


*************** info trace ***************


***** uname -a *****


Linux rob-Satellite-T115 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Toshiba America Info Systems Device [1179:ffe0]
    Kernel driver in use: atl1c
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
    Kernel driver in use: r8180


***** lsusb *****


Bus 001 Device 002: ID 1b1c:1ab1 Corsair 
Bus 002 Device 003: ID 04f2:b19a Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****




***** lsmod *****


r8187se               155774  0 
eeprom_93cx6           13168  1 r8187se


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Lechuga:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    1945 Nstar:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA2
    ATT136:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    TREND:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA




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


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"ATT136"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=46/100  Signal level=-63 dBm  Noise level=-83 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1156ms ago
          Cell 02 - Address: <MAC address removed>
                    ESSID:"1945 Nstar"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=68/100  Signal level=-48 dBm  Noise level=-98 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 85ms ago
          Cell 03 - Address: <MAC address removed>
                    ESSID:"Lechuga"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=73/100  Signal level=-44 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 67ms ago




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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/staging/rtl8187se/r8187se.ko
description:    Linux driver for Realtek RTL8187SE WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     80687440CA33AEECC50A757
alias:          pci:v000010ECd00008199sv*sd*bc*sc*i*
depends:        eeprom_93cx6
staging:        Y
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           ifname:string
parm:           hwwep: Try to use hardware WEP support. Still broken and not available on all cards (int)




***** udev rules *****


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0 (r8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   17.204572] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   17.270100] r8187se: 
[   17.270107] r8187se: Copyright (c) 2004-2005, Andrea Merello
[   17.270109] r8180: Initializing module
[   17.270112] r8180: Wireless extensions version 22
[   17.270114] r8180: Initializing proc filesystem
[   17.270147] r8180: Configuring chip resources
[   17.270160] r8180 0000:08:00.0: enabling device (0000 -> 0003)
[   17.276831] rtl8180_init:Error channel plan! Set to default.
[   17.276836] r8180: Channel plan is 0
[   17.276844] r8180: MAC controller is a RTL8187SE b/g
[   17.279002] r8180: usValue is 0x104
[   17.318047] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   17.346930] r8180: IRQ 17
[   17.349254] r8180: Driver probe completed
[   22.337503] r8180: Bringing up iface
[   22.535992] r8180: Card successfully reset
[   23.275345] r8180: WIRELESS_MODE_G
[   23.298401] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.324187] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

---

### Post by varunendra on 2013-10-08
I think the dmesg part in the last pretty much tells the whole story (I'm experimental ! Don't expect too much from me..), but -
> **rob24 said:**
> ```

wlan0     802.11b/g  ESSID:"**[COLOR="#FF0000"]g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A[/COLOR]**"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I'm sure YOU DID NOT put that weird ESSID there, did you?

Please try deleting the existing connection, and create a new one saving the correct SSID, security key in the Network Manager itself, then try to reconnect.

**PS:**
Did you also try to install any proprietary drive directly from Realtek's site?

---

### Post by rob24 on 2013-10-09
I deleted it and created a new one. Same problem remains. I have not tried to install the proprietary driver from realtek's site. Should I? Can you provide that link if I should? Thank you very much for helping me out!

---

### Post by varunendra on 2013-10-10
I tried to compile the proprietary one here. It is from 2009 and is incompatible with the current kernels. I couldn't find a patch for it, so looks like the windows xp driver with ndiswrapper may be your best hope. How did you install it earlier? I recommend this post here : [http://askubuntu.com/a/216123](http://askubuntu.com/a/216123)

Post back if that does not work or there is some problem following it, and I may be able to help with that.

---

### Post by rob24 on 2013-10-10
When i get to number 3 in step 2 it gives me error 127 and error 2 when i try "make" command.  (make[1]: gcc: command not found loadndisdriver is error 127)...hmm..thanks again!

---

### Post by varunendra on 2013-10-10
Building a binary requires you to have linux-headers and gcc-libraries installed. Accordingly, with a temporary internet connection, please try -
```
sudo apt-get install linux-headers-generic build-essential
```
Then extract the files from the downloaded ndiswrapper package and start fresh. If you still get errors, post back the entire output of "make" command.

---

### Post by rob24 on 2013-10-11
Thanks that worked, but I still have the exact same problem. Can see the network but password is bad not matter what. Also, I tried other networks and still same problem. Below is the new output from the wireless script:



```
*************** info trace ***************


***** uname -a *****


Linux rob-Satellite-T115 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring


***** lspci *****


07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Toshiba America Info Systems Device [1179:ffe0]
	Kernel driver in use: atl1c
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
	Kernel driver in use: ndiswrapper


***** lsusb *****


Bus 002 Device 003: ID 04f2:b19a Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****




***** lsmod *****


ndiswrapper           192638  0 


***** nm-tool *****


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
    1945 Nstar:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    ATT136:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Lechuga:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2




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


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Lechuga"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00074C656368756761
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001900000000000000000000000000000000000000
                    IE: Unknown: 3D1601001900000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 02 - Address: <MAC address removed>
                    ESSID:"1945 Nstar"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A31393435204E73746172
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD270050F204104A0001101044000102104700101DA10A2521A650651F94B507775287D1103C000103
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    ESSID:"ATT136"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006415454313336
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




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
blacklist r8187se


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.8.0-31-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.58
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     2F19DFC5820B1214E84CFEB
depends:        
vermagic:       3.8.0-31-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)




***** udev rules *****


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0 (r8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x148f:0x2770 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[  548.090811] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  548.159403] ndiswrapper: driver net8187se (Realtek Semiconductor Corp.,10/28/2009,5.9109.1028.2009) loaded
[  548.159476] ndiswrapper 0000:08:00.0: enabling device (0000 -> 0003)
[  548.235836] ndiswrapper: using IRQ 17
[  548.892468] wlan0: ethernet device <MAC address removed> using NDIS driver: net8187se, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8199.5.conf
[  548.892498] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  548.941089] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  548.953437] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  583.117755] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```

---

### Post by varunendra on 2013-10-12
> **rob24 said:**
> Thanks that worked, but I still have the exact same problem. Can see the network but password is bad not matter what.
Everything in the report looks okay to me, although these can be improved -
```

  Wireless Access Points 
    1945 Nstar:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    [B]ATT136:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 [COLOR="#FF0000"]WPA WPA2[/COLOR]
    Lechuga:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 [COLOR="#FF0000"]WPA WPA2[/COLOR][/B]

```

If your access-point is one of the two highlighted above, try changing the encryption type (in the router/access-point) to pure WPA2-PSK (AES/CCMP). Currently it is WPA/WPA2 mixed mode with TKIP, which can be a problem sometimes.

If it is the "**1945 Nstar**" one, try changing its SSID (again, in the router) to something that doesn't contain spaces, something like "1945_Nstar" or just "Nstar". Additionally, you may try changing its channel from 6 to 1 or 11, usually these work better with Linux.

If the above don't help, make sure "IPv6" is set to "Ignore" in the connection settings in Network Manager, or try permanently turning it off following [post=12640479]this post[/post].

---

### Post by peter-rosenberg-dk on 2014-01-03
The post recommended by Varunendra, has been updated by myself.
I would not recommend NDISWrapper, as long as Chipset is supported by Ubuntu, as my finding shows here: [http://askubuntu.com/a/399677/231460](http://askubuntu.com/a/399677/231460)
The weird looking ESSID indicates it advertises on the IPV6 layer, I think. Maybe you should disable the IPV6 in the network profile for the AP and just allow IPV4 pick an address via DHCP.

---

### Post by varunendra on 2014-01-04
> **peter-rosenberg-dk said:**
> I would not recommend NDISWrapper, as long as Chipset is supported by Ubuntu..

+1

Ndiswrapper is our last resort and we don't hope much from it unless otherwise confirmed by other users.

Btw, welcome to Ubuntu Forums Peter! :)

---


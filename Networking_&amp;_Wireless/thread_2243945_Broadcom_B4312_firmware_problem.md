---
title: "Broadcom B4312 firmware problem"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by John Pye on 2014-09-12
Ubuntu 14.14 Dell Inspiron mini 10V 

Since yesterday network manager reports "Device not ready (firmware missing)".  I have followed instructions at [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) without success. 

Output of wireless-info.txt-

```


########## wireless info START ##########

Report from: 12 Sep 2014 12:08 BST +0100

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 i686 i686 GNU/Linux

, ro, quiet, splash, 

##### desktop #####

GNOME Flashback (Metacity)

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 008: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 mac80211,b43
bcma                   25651  1 b43
ssb                    50691  1 b43

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe98:65a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7489880 (7.4 MB)  TX bytes:1083596 (1.0 MB)
          Interrupt:43 Base address:0x2000 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0

##### resolv.conf #####

nameserver 194.168.4.100
nameserver 194.168.8.100
nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

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

##### iwlist scan #####

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

##### module infos #####

[b43]
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     74A0B0F56BB16FBD5C5AFAE
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.2.0-29-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

[bcma]
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     5EE36FC87632277EDFDE242
depends:        
intree:         Y
vermagic:       3.2.0-29-generic SMP mod_unload modversions 686 

[ssb]
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
depends:        
intree:         Y
vermagic:       3.2.0-29-generic SMP mod_unload modversions 686 

##### module parameters #####

[b43]
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 0
verbose: 2

##### /etc/modules #####

lp

##### blacklists #####

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

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x0bb4:0x0303 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    7.024360] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.038317] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    7.069054] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    7.069084] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    7.069111] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    7.069529] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    7.188766] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   10.199405] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.311344] Registered led device: b43-phy0::tx
[   10.311665] Registered led device: b43-phy0::rx
[   10.311978] Registered led device: b43-phy0::radio
[   17.144656] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   17.144670] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   17.144680] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   17.145397] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.998084] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   21.998097] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   21.998107] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   28.478722] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   28.478735] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   28.478745] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   28.527009] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   28.527023] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   28.527033] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 3119.802886] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 3147.182693] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3147.182730] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 3147.200592] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[ 3147.200617] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[ 3147.200639] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[ 3147.200661] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[ 3147.264622] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 3147.401820] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 3147.481924] Registered led device: b43-phy0::tx
[ 3147.482019] Registered led device: b43-phy0::rx
[ 3147.482110] Registered led device: b43-phy0::radio
[ 3147.614465] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 3147.614478] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 3147.614489] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 3147.615603] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

Many thanks

---

### Post by chili555 on 2014-09-12
With a temporary internet connection, please open a terminal and do:

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```

After it's done, reboot and tell us if it's working.

---

### Post by John Pye on 2014-09-12
Thanks for the help. 

 I've run the commands and then tried rebooting both with wired connection and without during the reboot but no apparent change. 

Thanks John

---

### Post by chili555 on 2014-09-12
What does this tell us?```
rfkill list all
dmesg | grep b43
sudo ls -al /lib/firmware/b43 | grep ucode5.fw
```

---

### Post by John Pye on 2014-09-12
Hi Again
I'm getting -

rfkill list all
```



0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
dmesg | grep b43
```

[    7.009330] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.009364] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    9.843497] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.951608] Registered led device: b43-phy0::tx
[    9.951711] Registered led device: b43-phy0::rx
[    9.951801] Registered led device: b43-phy0::radio
[   16.854798] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   16.854811] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   16.854820] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   22.084360] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   22.084373] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   22.084382] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   28.079232] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   28.079245] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   28.079255] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   33.080681] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   33.080693] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   33.080703] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   38.079787] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   38.079802] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   38.079812] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   43.079814] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   43.079827] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   43.079837] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```
sudo ls -al /lib/firmware/b43 | grep ucode5.fw - nothing just back to the prompt

Thanks, John

---

### Post by chili555 on 2014-09-12
Please go back to post #2 and try again. Were there errors, warnings, sparks, smoke??

---

### Post by John Pye on 2014-09-13
Hi again

No change, this is what came up in the terminal

```

dell@dell-laptop:~$ sudo apt-get update
[sudo] password for dell: 
Ign http://archive.canonical.com trusty InRelease
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://gb.archive.ubuntu.com trusty-updates InRelease                      
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gb.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://gb.archive.ubuntu.com trusty Release                                
Hit http://gb.archive.ubuntu.com trusty-updates Release                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://gb.archive.ubuntu.com trusty/main Sources                           
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://gb.archive.ubuntu.com trusty/restricted Sources                     
Hit http://gb.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages           
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages                 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages               
Ign http://ppa.launchpad.net trusty/main Translation-en              
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com trusty/main Translation-en          
Hit http://security.ubuntu.com trusty-security Release               
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en     
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://security.ubuntu.com trusty-security/main Sources          
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en      
Ign http://download.ebz.epson.net lsb3.2 InRelease
Hit http://gb.archive.ubuntu.com trusty-updates/main Sources
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com trusty-updates/universe Sources     
Hit http://security.ubuntu.com trusty-security/multiverse Sources    
Hit http://gb.archive.ubuntu.com trusty-updates/main i386 Packages   
Hit http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en  
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://security.ubuntu.com trusty-security/universe Sources      
Hit http://download.ebz.epson.net lsb3.2 Release.gpg
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://download.ebz.epson.net lsb3.2 Release
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Reading package lists... Done

```

and

```

dell@dell-laptop:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra compiz-plugins-extra compiz-plugins-main
  epiphany-browser-data fonts-arphic-uming fonts-vlgothic gnome-search-tool
  gwibber-service hyphen-en-us libquvi-scripts libquvi7 libwebkit2gtk-3.0-25
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  printer-driver-hpijs
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

```

Thank you for taking the time to help, John

---

### Post by chili555 on 2014-09-13
This is crazy! The firmware needed by your device isn't included in the method prescribed by Broadcom themselves! Several of us are investigating and chatting about your very case! 

While we look for a better method, please use the method at post #11 here. [http://ubuntuforums.org/showthread.php?t=2243562&page=2](http://ubuntuforums.org/showthread.php?t=2243562&page=2) I just verified that your firmware, ucode15.fw,* is* included. 

We will continue to learn and refine our methods in the face of The Great Firmware Crisis!

---

### Post by jeremy31 on 2014-09-13
It appears this method extracts the ucode15.fw


```
sudo apt-get install firmware-b43-installer b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgsoap3
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
Need to get 30.4 kB of archives.
After this operation, 154 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main b43-fwcutter amd64 1:018-2 [26.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/multiverse firmware-b43-installer all 1:018-2 [3,960 B]
Fetched 30.4 kB in 0s (79.9 kB/s)                 
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 392056 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a018-2_amd64.deb ...
Unpacking b43-fwcutter (1:018-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a018-2_all.deb ...
Unpacking firmware-b43-installer (1:018-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up b43-fwcutter (1:018-2) ...
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2014-09-13 07:57:22--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: ‘broadcom-wl-5.100.138.tar.bz2’


100%[======================================>] 13,514,651  1.14MB/s   in 12s    


2014-09-13 07:57:35 (1.04 MB/s) - ‘broadcom-wl-5.100.138.tar.bz2’ saved [13514651/13514651]


Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
jeremy@jeremy-Lenovo-G710 ~ $ 

```

---

### Post by chili555 on 2014-09-13
I just tried it; it works! Awesome! Thanks, Jeremy.

---

### Post by Arsemyth on 2014-09-13
Hi, 

I had exactly the same problem this morning... Dell Inspiron laptop, no wireless adaptor. 

I just ran Jeremy's solution and it sorted everything out.  

Thanks!

Roger

---

### Post by jcjanko on 2014-09-13
Hello everyone. 

I also wanted to chime in that my daughter's wifi on her d530 disappeared after she updated it. I was using linux-firmware-nonfree, and it no longer worked. I had also tried bcmwl-kernel-source, with no luck. Jeremy's solution got it back up and running as well. Thank you very much!

Jason

---

### Post by John Pye on 2014-09-13
Success!

I tried Jeremy's method first as it looked quicker but that didn't work. In case it is useful for you, though I can't get the actual text from the terminal back to post as I went straight on to try the other method, I think it said something like I had the newest version of both firmware-b43-installer and b43-fwcutter installed. 

It appears the b43 directory already existed though as the first command resulted in-

```

dell@dell-laptop:~$ sudo mkdir /lib/firmware/b43
[sudo] password for dell: 
mkdir: cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists

```

I ran the next 2 and it didn't even need a reboot to start working.  

Once again thanks to all who have helped. 

Thanks, John

---

### Post by chili555 on 2014-09-13
> **John Pye said:**
> Success!

I tried Jeremy's method first as it looked quicker but that didn't work. In case it is useful for you, though I can't get the actual text from the terminal back to post as I went straight on to try the other method, I think it said something like I had the newest version of both firmware-b43-installer and b43-fwcutter installed. 

It appears the b43 directory already existed though as the first command resulted in-

```

dell@dell-laptop:~$ sudo mkdir /lib/firmware/b43
[sudo] password for dell: 
mkdir: cannot create directory ‘/lib/firmware/b43’: File exists

```

I ran the next 2 and it didn't even need a reboot to start working.  

Once again thanks to all who have helped.  Most of the problems seem to have been in the UK maybe Dr Chili and Varun should be on the New Year's Honours list.  Arise Sir Chili and Sir Varun! 

Thanks, JohnGlad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by EricG1793 on 2014-09-29
I don't understand Jeremy's solution. Is it simply a matter of:

```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

Or are there other steps involved as well that I'm missing? I have a Latitude D530.

---

### Post by jeremy31 on 2014-09-29
> **EricG1793 said:**
> I don't understand Jeremy's solution. Is it simply a matter of:

```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

Or are there other steps involved as well that I'm missing? I have a Latitude D530.
It is that simple if you had previously used linux-firmware-nonfree

If this is a new install, follow the steps in the Broadcom sticky post

---


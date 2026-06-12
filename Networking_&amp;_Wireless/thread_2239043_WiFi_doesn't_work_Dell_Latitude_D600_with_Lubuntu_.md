---
title: "WiFi doesn't work Dell Latitude D600 with Lubuntu 14.04 LTS"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by bartek6 on 2014-08-11
Hello Everybody!

I've problem with Wifi on my Dell Latitude D600.  Operational system Lubuntu 14.04 LTS is installed succesfull with fake PAE. Wired connections works perfectly, but wireless doesn't. After instalation I've opened Terminal and put follow commands:

Step 1) sudo apt-get update

Step 2) sudo apt-get install firmware-b43-installer

Step 3) cd /cdrom/pool/main/b/b43-fwcutter/
sudo dpkg -i b3-fwcutter*

Step 4) Copying downloaded file to home folder 

Step 5) tar xfvj broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o

When system is starting I've no error commands. I can see aplet with Wired, and Wireless indicator. When I click on Wirelees connection I can see my home network and put password, but connections isn't starting. 

Password is 100% corect. Previously I've succesfull installed Lubuntu 14.04 LTS on HP nc6120 and I can use wifi. I've tried instal Wifi with 2 wireless PCI card.

What can I to do more?

---

### Post by chili555 on 2014-08-11
Mind if we have a peek at your device details?```
lspci -nn | grep 0280
```Thanks.

---

### Post by bartek6 on 2014-08-19
There you are:
"02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)"

---

### Post by varunendra on 2014-08-19
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by bartek6 on 2014-08-20
There you are:

```


########## wireless info START ##########

Report from: 20 Aug 2014 17:30 CEST +0200

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, forcepae, quiet, splash, vt.handoff=7

##### desktop #####

Lubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
    Subsystem: Dell Device [1028:8126]
    Kernel driver in use: tg3

02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Broadcom Corporation Device [14e4:0453]
    Kernel driver in use: b43-pci-bridge

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

./wireless_script: line 103: pccardctl: command not found

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe78:a781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1221125 (1.2 MB)  TX bytes:165853 (165.8 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Wi-Fi_BMH:       Infra, <MAC addr Wi-Fi_BMH>, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA
    dlink123:        Infra, <MAC addr dlink123>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    PLAY-ONLINE-0664:Infra, <MAC addr PLAY-ONLINE-0664>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    DOM :            Infra, <MAC addr DOM >, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             194.204.159.1
    DNS:             194.204.152.34

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

##### iw reg get #####

./wireless_script: line 141: iw: command not found

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

Channel occupancy:

     1   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.437 GHz (Channel 6)
     2   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Wi-Fi_BMH>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Wi-Fi_BMH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006da9d37f
                    Extra: Last beacon: 336ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr dlink123>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"dlink123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a0005f0b0
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr PLAY-ONLINE-0664>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"PLAY-ONLINE-0664"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000290c7554c
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwislo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

e Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr DOM >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"DOM "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a30a45396
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
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

[bcma]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

##### module parameters #####

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
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

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16a6 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4320 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    2.934968] ssb: Found chip with id 0x4306, rev 0x03 and package 0x00
[    2.934987] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.934999] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.935011] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.935023] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.935034] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.948594] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[   14.018238] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   14.040424] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 2
[   20.591553] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   20.695380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############



```

---

### Post by Hadaka on 2014-08-20
Hi, with a wired connection please do..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe b43
```
disconnect the wired connection
boot
is it working now?

---

### Post by bartek6 on 2014-08-21
No :( Still the same. When system is starting I've no error commands. I can see aplet with  Wired, and Wireless indicator. When I click on Wirelees connection I can  see my home network and put password, but connections isn't starting. Password is 100% corect - works with 3 another home devices.

---

### Post by Hadaka on 2014-08-21
Hi, please edit your wireless network connection and make it look exactly like the attached
[ATTACH=CONFIG]255697[/ATTACH][ATTACH=CONFIG]255698[/ATTACH][ATTACH=CONFIG]255699[/ATTACH]
...........wireless.....................IPv4..............................IPv6

click save on all
then boot

then go into your router settings and get rid of the TKIP setting
set it wpa2 ccmp

---

### Post by bartek6 on 2014-08-24
chili555, varunendra, Hadaka are true Lubuntu expert. I've done step by step all what you adviced me. Now wifi is working properly. Only putting additionaly DNS servers to 8.8.8.8 and 8.8.4.4 was unnecesary. Thanks a lot!

---

### Post by Hadaka on 2014-08-24
Glad it is working for you !
we are pleased and thank you for your
kind words.

---

### Post by bartek6 on 2014-09-14
On my personal D600 Wifi works perfectly, but now I've similar problem with Dell D600 of my parents.


After putting in terminal
```

lspci -nn | grep 0280

```

I've following output

```

02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller [14e4:4324] (rev 02)

```

and after putting in terminal 
```

wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script && ./wireless_script

```

I've this output

```


########## wireless info START ##########

Report from: 14 Sep 2014 13:50 CEST +0200

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, forcepae, quiet, splash, vt.handoff=7

##### desktop #####

Lubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
    Subsystem: Dell Latitude D400 [1028:865d]
    Kernel driver in use: tg3

02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller [14e4:4324] (rev 02)
    Subsystem: Dell Truemobile 1400 [1028:0001]
    Kernel driver in use: b43-pci-bridge

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:c10a A4 Tech Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

./wireless_script: line 103: pccardctl: command not found

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

b43legacy             104081  0 
mac80211              546051  1 b43legacy
cfg80211              409394  2 mac80211,b43legacy
ssb                    51854  1 b43legacy

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe3b:ce0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1044335 (1.0 MB)  TX bytes:364608 (364.6 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43legacy
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Livebox-7004:    Infra, <MAC addr Livebox-7004>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    WiFi:            Infra, <MAC addr WiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA
    Orange_FunSpot:  Infra, <MAC addr Orange_FunSpot>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72
    NETIASPOT-A1D8F0:Infra, <MAC addr NETIASPOT-A1D8F0>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    FON_NETIA_FREE_INTERNET: Infra, <MAC addr FON_NETIA_FREE_INTERNET>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

##### iw reg get #####

./wireless_script: line 141: iw: command not found

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

Channel occupancy:

     2   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Livebox-7004>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Livebox-7004"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a622bc48a
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr Orange_FunSpot>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"Orange_FunSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a622b5bf1
                    Extra: Last beacon: 44ms ago
          Cell 03 - Address: <MAC addr WiFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000179539148
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[b43legacy]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
firmware:       b43legacy/ucode4.fw
firmware:       b43legacy/ucode2.fw
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43legacy wireless driver
srcversion:     6D2882100E447B34AFE53BC
depends:        mac80211,ssb,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           pio:enable(1) / disable(0) PIO mode (int)
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the firmware files to load. (string)

[ssb]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

##### module parameters #####

[b43legacy]
bad_frames_preempt: 0
pio: 0

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

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x165d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4324 (b43legacy)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    1.618405] ssb: Found chip with id 0x4306, rev 0x02 and package 0x00
[    1.618415] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[    1.618421] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    1.618427] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[    1.618433] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    1.618439] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[    1.618445] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    1.632758] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[   17.376118] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   17.424182] b43legacy-phy0: Loading firmware b43legacy/ucode4.fw
[   17.453268] b43legacy-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 1, Type 0, Revision 2)
[   17.454177] b43legacy: probe of ssb0:2 failed with error -95
[   17.854965] b43legacy-phy0: Loading firmware b43legacy/pcm4.fw
[   17.943037] b43legacy-phy0: Loading firmware b43legacy/b0g0initvals2.fw
[   26.412086] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   26.492261] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############


```

I can also add that after turning on notebook and before logging window this communicate is showed:

```

b43legacy-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 1, Type 0, Revision 2)

```

Can you help me once again? :-)

---

### Post by Hadaka on 2014-09-14
Hi, you should have created a new thread for this. but...
please do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
and set the network setting the same as you did the other one,
thanks

---


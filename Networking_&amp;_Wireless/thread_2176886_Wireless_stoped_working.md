---
title: "Wireless stoped working"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by CR4NFdA on 2013-09-26
Running Ubuntu 12.10. This PC has both wire and wireless. Been working good last eight mounths. Booted up today and first thing it wanted was my password for DropBox. It never asked for this before and DropBox is working fine. Five minutes later, it wanted the password for the wireless connection. Password is correct but still won't connect. I cancel it but it keeps popping up. A forum and internet search only has answers for intial setup and something about a bug, but wireless has been working. I removed the wireless from network connections, restarted the PC and added the wireless again. Still won't work. Any ideas?

Many thanks all....

mitch

---

### Post by varunendra on 2013-09-26
Sounds like a familiar issue, but don't remember the fix. Let's start by exploring the current settings.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by CR4NFdA on 2013-09-27
Thanks varun. Heres the info:


*************** info trace ***************

***** uname -a *****

Linux Asus 3.5.0-41-generic #64-Ubuntu SMP Wed Sep 11 15:36:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

***** lspci *****

00:0a.0 Bridge [0680]: NVIDIA Corporation CK804 Ethernet Controller [10de:0057] (rev f3)
    Subsystem: ASUSTeK Computer Inc. Device [1043:812a]
    Kernel driver in use: forcedeth
--
01:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Linksys WMP54G v4.1 [1737:0055]
    Kernel driver in use: rt61pci

***** lsusb *****

Bus 001 Device 003: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 005: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rt61pci                31790  0 
rt2x00pci              14519  1 rt61pci
rt2x00lib              54995  2 rt61pci,rt2x00pci
mac80211              535936  2 rt2x00pci,rt2x00lib
cfg80211              206797  2 rt2x00lib,mac80211
eeprom_93cx6           13345  1 rt61pci
crc_itu_t              12708  2 rt61pci,firewire_core

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.247.24.53
    DNS:             66.189.0.100
    DNS:             24.178.162.3


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    VIC-PC:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    JadeWillow-guest:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    JadeWillow:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2



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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"JadeWillow-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000324edf04c71
                    Extra: Last beacon: 1124ms ago
                    IE: Unknown: 00104A61646557696C6C6F772D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081500000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"VIC-PC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001df957defd2
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 00065649432D5043
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700105A548C24DC5E7ADE92D1B2426D7735581021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000


***** resolv.conf *****

nameserver 127.0.1.1
search gha.chartermi.net

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

filename:       /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     1A3F1C92F1913A1AA535E39
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       3.5.0-41-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     E1A18A15B40392F963C0FA3
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.5.0-41-generic SMP mod_unload modversions 

filename:       /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     E1428E8BC5BFFF099140FE6
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.5.0-41-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10de:0x0057 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:09.0/0000:01:06.0 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   23.263932] Registered led device: rt61pci-phy0::radio
[   23.263957] Registered led device: rt61pci-phy0::assoc
[   24.469555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.472518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************
mitch

---

### Post by varunendra on 2013-09-27
You should use the '**Code**' box to post the outputs. It preserves its formatting and makes your post cleaner, compact and more readable. Please follow the "Using Code Tags" link in my signature to see how.

> **CR4NFdA said:**
> 
  Wireless Access Points 
    VIC-PC:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    JadeWillow-guest:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    JadeWillow:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2

Which of the above is/are your access point(s)? The first and the last one are using WPA/WPA2 mixed mode which is not good for linux drivers. If these are your access points, please change the encryption in the router to pure WPA2-PSK only with AES. No mixed mode, no TKIP.

Having done that, please do the following in a terminal (Ctrl-Alt-T) in Ubuntu -
```
sudo modprobe -rv rt61pci
sudo modprobe -v rt61pci nohwcrypt=Y
```
Does it make the password prompt go away? If still not, try deleting the existing connection(s) from Network Manager and create new one, saving the correct security key and encryption settings under the "Wireless Security" tab in the connection settings.

I have a feeling that maybe this problem is related to something other than wifi settings, but please try above and let us know the result.

And since you mentioned it starting with Dropbox password prompt, have you tried disabling or quitting Dropbox applet yet?

---

### Post by CR4NFdA on 2013-09-28
Thanks again Varun. So sorry about the cut and paste. Still learning the ropes here. My access point is JadeWillow. I reset the router, a Linksys E2000 from mixed mode to WPA2 Personal. It seems to be working again. 
```

```
magpie@Asus:~$ sudo modprobe -rv rt61pci
[sudo] password for magpie: 
rmmod /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
rmmod /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
rmmod /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
rmmod /lib/modules/3.5.0-41-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-41-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.5.0-41-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
magpie@Asus:~$ sudo modprobe -v rt61pci nohwcrypt=Y
insmod /lib/modules/3.5.0-41-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.5.0-41-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-41-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.5.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko nohwcrypt=Y
magpie@Asus:~$ 

Anyways here's a post of those commands. For future reference, I removed the wireless connection from network manager first before I made changes to the router. Many thanks again and I'll mark this post as solved if I can figure out how. :p

---

### Post by varunendra on 2013-09-28
Wow! I wasn't expecting it to get solved so easily :)

Feel free to post back if it resurrect itself, since the "nohwcrypt=1" parameter is temporary, we didn't make it permanent. So either it is just the optimal encryption (WPA2), or it may return back on next boot. If it does, and running the same two 'modprobe' commands fixes it again, we can make that parameter permanent.

> **CR4NFdA said:**
> and I'll mark this post as solved if I can figure out how. :p
Apparently you did ! :P

---


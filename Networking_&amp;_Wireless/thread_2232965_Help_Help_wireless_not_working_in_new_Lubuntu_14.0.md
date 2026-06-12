---
title: "Help Help wireless not working in new Lubuntu 14.04 install"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by taff2 on 2014-07-05
I was instructed by forum admin to post this "script". Hopefully I've done it correctly (never posted a script before). The problem is that my wireless network/router will not take my password. It keeps asking for it over and over. I have correct password and no other devices in my house are having any troubles. This is a new install for me of Linux so i don't have anything to compare to as to the setup issues. My network shows up in the script as a2a301.



```
########## wireless info START ##########
##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux taff-Satellite-A10 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:47:59 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel driver in use: e100

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #####

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    THE FBI:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Home's Guest Network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Home`s Network:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    a2a301:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12

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

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"a2a301"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e409c039eb
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 0006613261333031
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A0001101044000102103B00010310470010B46163F2DE72650E7930EB2BEB2997AA10210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110000100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"THE FBI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dfa40cb7a1
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 000754484520464249
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700108726C427C02E0EBA3707C802A5C9817510210005436973636F1023000D4C696E6B7379732045343230301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180200F0240000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Home`s Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000be01570b17
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 000E486F6D656073204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710320
                    IE: Unknown: DD0E0017F2070001010660334BE734C7
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Home's Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000be01564a36
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 0014486F6D652773204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710208
                    IE: Unknown: DD0E0017F2070001010660334BE734C7

##### iwlist channel #####

eth1      11 channels in total; available frequencies :
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
          Current Frequency=2.457 GHz (Channel 10)

##### modinfo #####

##### modules #####

lp

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCMCIA device 0x0002:0x0156 (orinoco_cs)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   30.411984] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   30.417347] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  147.524614] eth1: Lucent/Agere firmware doesn't support manual roaming
[  152.890768] eth1: Lucent/Agere firmware doesn't support manual roaming
[  168.381654] eth1: Lucent/Agere firmware doesn't support manual roaming
[  204.280262] eth1: Lucent/Agere firmware doesn't support manual roaming
[  219.759352] eth1: Lucent/Agere firmware doesn't support manual roaming

########## wireless info END ############
[FONT=Verdana]
```[/FONT]

---

### Post by grahammechanical on 2014-07-05
Your password? Or the router's password/pass phrase/wireless key/WPA-PSK key? The driver is installed and the WiFI adapter is working. Otherwise there would not be any wireless access points in that printout.

We authenticate a connection to a wireless access point (router) not by putting in our user password but the wireless key/pass phrase for the router. You may find a record on a sticker on the bottom of the router.

Regards.

---

### Post by taff2 on 2014-07-05
It's the key on bottom of router (and only password/key I've ever used with router).

---

### Post by varunendra on 2014-07-06
> **taff2 said:**
> ```
eth1      **IEEE [COLOR="#FF0000"]802.11b[/COLOR]**  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
....
....
  Wireless Access Points 
    ....
    a2a301:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
....
....
eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"a2a301"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              **24 Mb/s; 36 Mb/s; 54 Mb/s**
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; **48 Mb/s**
                    ....
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                    ....
                        IE: WPA Version 1
                        Group Cipher : TKIP
```
Your old PCMCIA card does not support two things that your router is using -

1) WPA2 encryption (it is using WPA/WPA2 mixed mode),
2) 'g' mode network (it *seems* to be using b/g or b/g/n mode)

Accordingly, you may try these -

**1)** Change the encryption type in the router/access-point to pure WPA with TKIP. Your card simply can not support the WPA2 part which we usually recommend.

**2)** Try setting the router to only 'b' mode instead of b/g or b/g/n mode, whichever it is currently in. This will severely limit the speed but do it just for a test to see if the driver is any happier with it. If you are using other devices in the home that can support higher speeds, you might wish to revert this change after the test.

Reboot the router after saving any changes.

---


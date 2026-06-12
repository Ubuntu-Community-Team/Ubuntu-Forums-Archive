---
title: "Compaq 2190US , Belkin N150 F9L1001v1"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by jerry_c2 on 2014-04-21
I have an older Compaq 2190US laptop running Ubuntu 12.04 solely.  I have a belkin N150 F9L1001v1 usb wireless adapter.

My problem is that the computer sees available networks.  The usb adapter lights appropriately and when I first start the computer I can maybe get to 1 webpage before the computer stops giving me internet connection.  The wireless network icon and information still tells me I'm connected but I have no internet service.

I know other people have some issues with the driver for this adapter but it seems to be working.  Does anyone have any ideas as to what could be causing my internet connection problem?

---

### Post by varunendra on 2014-04-22
Welcome to the forums jerry_c2!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Run the script when the wireless adapter is plugged in and working.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by jerry_c2 on 2014-04-23
```
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux jerry-Presario-2100-DM745A 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:42:40 UTC 2014 i686 i686 i386 GNU/Linux

##### lspci #####

00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
    Subsystem: Hewlett-Packard Company Device [103c:002a]
    Kernel driver in use: natsemi

##### lsusb #####

Bus 001 Device 008: ID 0bda:8192 Realtek Semiconductor Corp. RTL8192U 802.11n Wireless Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"Hyatt"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.17.1.1      0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.17.0.0      0.0.0.0         255.255.0.0     U     2      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.0.1
```

After a little investigation, if I unplug the wireless adapter and plug it back in, the internet will work for a while.  I can continue to repeat this process and have some internet access.  There doesn't seem to be a specific amount of time that the adapter will continue to work.

```
##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Hyatt] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Hyatt:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 88
    Hyatt:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 88
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 58
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44
    Hyatt:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    Hyatt:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10
    *Hyatt:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    Hyatt:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    Hyatt:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7

  IPv4 Settings:
    Address:         172.17.140.100
    Prefix:          16 (255.255.0.0)
    Gateway:         172.17.1.1

    DNS:             4.2.2.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            natsemi
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
plugins=ifupdown,keyfile
dns=dnsmasq

```

more

```
[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=44/100  
          Cell 03 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=7/100  
          Cell 04 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=71/100  
          Cell 05 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 06 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 07 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  
          Cell 08 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  

```

```
          Cell 09 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=43/100  
          Cell 10 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 11 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  
          Cell 12 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=72/100  
          Cell 13 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=72/100  
          Cell 14 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=7/100  
          Cell 15 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 16 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=47/100  

```

```
          Cell 17 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=76/100  
          Cell 18 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=72/100  
          Cell 19 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=44/100  
          Cell 20 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=76/100  
          Cell 21 - Address: <MAC address removed>
                    ESSID:"PPR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  
          Cell 22 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  
          Cell 23 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=7/100  

```

```
          Cell 24 - Address: <MAC address removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=7/100  
          Cell 25 - Address: <MAC address removed>
                    ESSID:"Hyatt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  

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
          Current Frequency=2.412 GHz (Channel 1)

##### lsmod #####

r8712u                164103  0 

##### modinfo #####

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     748939744C6AAC44D12C356
alias:          usb:v0409p02B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp845Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3325d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3341d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3339d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0049d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0058d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4901d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3336d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3335d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3334d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3333d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3342d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p646Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0752d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0063d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0059d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE034d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1791d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*in*
depends:        
staging:        Y
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

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
blacklist rt2x00usb
blacklist rt2x00lib"

##### udev rules #####

# PCI device 0x100b:/sys/devices/pci0000:00/0000:00:12.0 (natsemi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0bda:0x8192 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

[\code]

##### dmesg #####

[   12.036850] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   12.083015] r8712u: Staging version
[   12.083095] r8712u: register rtl8712_netdev_ops to netdev_ops
[   12.083111] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[   12.105484] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[   12.105500] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[   12.105506] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   23.700289] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[   23.709277] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[   23.870475] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.872405] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.182715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.552249] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.089998] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[   37.102717] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[   38.118447] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[   87.869756] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6
[  378.683920] r8712u: Staging version
[  378.683986] r8712u: register rtl8712_netdev_ops to netdev_ops
[  378.683999] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[  378.689740] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[  378.689756] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[  378.689762] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  379.684394] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[  379.693470] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[  379.853641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  379.855388] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  380.169887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  391.999340] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  392.157261] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[  392.527523] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[  394.389856] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1011.259842] r8712u: Staging version
[ 1011.259911] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1011.259925] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[ 1011.266820] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[ 1011.266836] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[ 1011.266842] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1012.156254] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[ 1012.165223] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[ 1012.326396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1012.330822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1012.645700] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1023.898805] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1024.074672] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1025.418644] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1027.375016] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1027.418053] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1029.417468] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1183.060848] r8712u: Staging version
[ 1183.060916] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1183.060929] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[ 1183.066361] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[ 1183.066375] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[ 1183.066380] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1183.944972] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[ 1183.954022] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[ 1184.114206] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1184.115956] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1184.425452] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1195.868617] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1196.021551] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1197.494596] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1198.047991] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1210.859087] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1211.227352] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1211.404467] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1215.761578] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6
[ 1250.579496] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1250.940930] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1251.189235] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1267.946519] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6
[ 1310.403872] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1311.642378] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1311.696435] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1391.476961] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1391.577074] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1395.853253] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1420.025498] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6
[ 1490.508510] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1490.933846] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1493.331534] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1504.975779] r8712u: Staging version
[ 1504.975848] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1504.975863] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[ 1504.981517] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[ 1504.981531] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[ 1504.981537] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1505.945223] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[ 1505.954205] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[ 1506.113565] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1506.115368] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1506.425759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1517.838848] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1517.982771] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1519.520855] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1519.799070] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1520.648655] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6
[ 1756.875920] r8712u: Staging version
[ 1756.875983] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1756.875996] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[ 1756.881688] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[ 1756.881702] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[ 1756.881708] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1757.973482] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[ 1757.982488] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[ 1758.142738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1758.145166] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1758.457921] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1769.791083] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1769.855949] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1769.938988] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1771.967424] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1772.904186] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6
[ 1900.240843] r8712u: Staging version
[ 1900.240909] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1900.240923] usb 1-2: r8712u: USB_SPEED_LOW with 6 endpoints
[ 1900.246220] usb 1-2: r8712u: Boot from EFUSE: Autoload Failed
[ 1900.246236] usb 1-2: r8712u: MAC Address from efuse = <MAC address removed>
[ 1900.246242] usb 1-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1901.156832] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[ 1901.165870] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[ 1901.326085] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1901.327861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1901.642280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1912.877325] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1913.011249] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 0
[ 1913.220406] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 1
[ 1914.768507] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 5
[ 1915.721173] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address removed>, seq = 0, tid = 6

########## wireless info END ############[\code]


```

---

### Post by varunendra on 2014-04-24
Please download the attachment from post #29 here : [http://ubuntuforums.org/showpost.php?p=10339484](http://ubuntuforums.org/showpost.php?p=10339484)
..but don't follow the exact instructions from that post, as they need to be slightly changed for you. Here are the modified instructions for you -

[indent]**1)** Copy the downloaded zip file onto your Desktop > Right-click it > click "Extract here".

**2)** Open a terminal (Ctrl-Alt-T) and run the following commands to copy the extracted firmware files to correct place (case of letters is important, you may copy-paste these commands to avoid errors) -
```
sudo mkdir /lib/firmware/RTL8192U
cd Desktop/RTL8192U
sudo cp * /lib/firmware/RTL8192U/
sudo modprobe -rv r8712u r8192u_usb
sudo modprobe -v r8192u_usb
```[/indent]
If you see any errors while executing above commands, please report them back. If it works, we'll need a little more work to make it permanent. If it gives any errors *(I'm particularly suspicious about the 'r8192u_usb' driver)*, we may need to take some other route.

---

### Post by jerry_c2 on 2014-04-25
when i attempt to extract the zip file from the desktop I get the following message

[copy]rchive:  /home/jerry/Desktop/RTL8192U.zip
[/home/jerry/Desktop/RTL8192U.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/jerry/Desktop/RTL8192U.zip or
          /home/jerry/Desktop/RTL8192U.zip.zip, and cannot find /home/jerry/Desktop/RTL8192U.zip.ZIP, period.
[\copy]

---

### Post by varunendra on 2014-04-25
First, please correct the 'Code' tags in your posts, your earlier one was also messed up and was fixed by a moderator on my request.

It is normal forward slash (/) in the closing tag, and certainly 'Code', not 'Copy' within the braces.

Secondly, the error message sounds like a broken or corrupt download. Please delete the current zip file and download it again.

---

### Post by jerry_c2 on 2014-05-07
I'll try again

---

### Post by jerry_c2 on 2014-05-07
My apologies on the code tags.  Let me try it again.

---

### Post by jerry_c2 on 2014-05-07
My apologies on the code tags.  Let me try it again.

```

jerry@jerry-Presario-2100-DM745A:~$ sudo mkdir /lib/firmware/RTL8192U
mkdir: cannot create directory `/lib/firmware/RTL8192U': File exists
jerry@jerry-Presario-2100-DM745A:~$ cd Desktop/RTL8192U
bash: cd: Desktop/RTL8192U: No such file or directory
jerry@jerry-Presario-2100-DM745A:~$ sudo cp * /lib/firmware/RTL8192U/
cp: omitting directory `Desktop'
cp: omitting directory `Documents'
cp: omitting directory `Downloads'
cp: omitting directory `etc'
cp: omitting directory `Music'
cp: omitting directory `Pictures'
cp: omitting directory `Public'
cp: omitting directory `Templates'
cp: omitting directory `Videos'
jerry@jerry-Presario-2100-DM745A:~$ sudo modprobe -rv r8712u r8192u_usb
WARNING: /etc/modprobe.d/ath9k.conf line 1: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with '"blacklist'
jerry@jerry-Presario-2100-DM745A:~$ sudo modprobe -v r8192u_usb

```

---

### Post by varunendra on 2014-05-07
> **jerry_c2 said:**
> ```

jerry@jerry-Presario-2100-DM745A:~$ cd Desktop/RTL8192U
bash: cd: **[COLOR="#FF0000"]Desktop/RTL8192U: No such file or directory[/COLOR]**

```
..means you didn't extract the downloaded file onto your Desktop. Was the zip file downloaded and extracted correctly this time? Where? It certainly isn't on your Desktop.

---

### Post by jerry_c2 on 2014-05-12
okay, let's see if this gives you what you need.  if not, is there a simpler solution to wireless networking with ubuntu.  i've had similar issues with wireless before, just not with a belkin adapter.

```

jerry@jerry-Presario-2100-DM745A:~$ sudo mkdir /lib/firmware/RTL8192U
mkdir: cannot create directory `/lib/firmware/RTL8192U': File exists
jerry@jerry-Presario-2100-DM745A:~$ cd Desktop/RTL8192U
jerry@jerry-Presario-2100-DM745A:~/Desktop/RTL8192U$ sudo cp * /lib/firmware/RTL8192U/
jerry@jerry-Presario-2100-DM745A:~/Desktop/RTL8192U$ sudo modprobe -rv r8712u r8192u_usb
WARNING: /etc/modprobe.d/ath9k.conf line 1: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with '"blacklist'
jerry@jerry-Presario-2100-DM745A:~/Desktop/RTL8192U$ sudo modprobe -v r8192u_usb 

```

---

### Post by varunendra on 2014-05-13
Looks like everything went fine this time. The warning messages in the above output are unrelated to what we are trying, so I think they can be safely ignored for now. Is the problem still the same? If yes, or if there is some different problem now, please download this new (experimental) version of wireless_script : [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) , copy it to your Desktop, then open a terminal and run this new script as follows :
```
cd Desktop
chmod +x wireless_script
./wireless_script
```

..then post back the fresh report that it generates.

---

### Post by westie457 on 2014-05-13
@ varunendra 
The link you provided shows the wireless script with no option to download.

Work around.

Highlight all the the text in the browser window and copy.
Open a text editor > paste.
Save As ... wireless_script and close the editor.

In the terminal run the commands you posted.

Edit:  on the Desktop

Right-click > New Document > Empty Document - type wireless_script - hit Enter
Right-click this > Open With (default text editor is suggested) > paste
Save As ... wireless_script

---

### Post by varunendra on 2014-05-13
> **westie457 said:**
> @ varunendra 
The link you provided shows the wireless script with no option to download.

Yup, that is a "Direct Download" link, means you can use the "right-click > save as" option of the browser (right-click the link > click "Save as" or whatever similar option your browser gives).

To use the regular web interface of dropbox, where it shows the object as a file and provides a "Download" button, change the "dl." part in the URL to "www", which means the following URL : [https://www.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://www.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script)

Sorry for the confusion, exact steps were described in the guide post linked to the "Wireless Script" link in my signature, I forgot to mention it here.

---

### Post by westie457 on 2014-05-14
> **varunendra said:**
> Yup, that is a "Direct Download" link, means you can use the "right-click > save as" option of the browser (right-click the link > click "Save as" or whatever similar option your browser gives).


Ooh silly me! Completely forgot about the 'right-click > Save As' option in the browser.

---


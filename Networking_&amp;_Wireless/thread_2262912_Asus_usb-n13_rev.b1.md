---
title: "Asus usb-n13 rev.b1"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by PenterX on 2015-01-28
I want to get it work. With default driver it can see my networks but can't connect with Internet to my home network. I can only connect my own android hotspot...

---

### Post by chili555 on 2015-01-28
Please post all the useful information you gave me in your PM and also:```
lsusb
nm-tool
```

---

### Post by PenterX on 2015-01-28
Iwconfig```

eth0 no wireless extensions.

lo no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:"IVAN2" 
Mode:Managed Frequency:2.412 GHz Access Point: CC:5D:4E:DA:AF:7A 
Bit Rate=150 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thr=2347 B Fragment thr:off
Power Management:off
Link Quality=36/70 Signal level=-74 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

Yup, I forgot to say: it connects to my wifi but woth no internet

---

### Post by chili555 on 2015-01-28
And how about the other items I requested? The more information I have with fewer requests, the sooner we can uncover the solution.

---

### Post by PenterX on 2015-01-29
lsusb
```

 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 14cd:168a Super Top 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1532:0118 Razer USA, Ltd 
Bus 003 Device 002: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [IVAN2] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        10:C3:7B:CA:87:72

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DSL-2640U:       Infra, 9C:D6:43:3B:E8:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    Roman_D:         Infra, 78:24:AF:CB:C2:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    TP-LINK_Ruslan:  Infra, 10:FE:ED:8C:95:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    DOS-18:          Infra, 1C:7E:E5:31:62:B8, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *IVAN2:          Infra, CC:5D:4E:DA:AF:7A, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2

  IPv4 Settings:
    Address:         192.168.1.45
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        60:A4:4C:60:B4:7F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


{

```

---

### Post by chili555 on 2015-01-29
> - Device: wlan0  [IVAN2] ----
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yesThe driver rtl8192cu is notorious for being troublesome. Fortunately, there is a fix.

I suggest you follow the procedure outlined here: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

---

### Post by chili555 on 2015-01-29
> **PenterX said:**
> Tried that. Successfuly installed but still not worksNo matter what version you install, rtl8192cu is broken. Why are you unable to install headers and, for that matter, all the parts required for the fixed driver?

---

### Post by PenterX on 2015-01-29
No, I installed fixed driver after reinstalling sustem from 14.10 to 14.04lts
But it doesn't work. But the problem in linux,  it works at Win7 perfectly.

---

### Post by chili555 on 2015-01-29
Let's see:```
iwconfig
dmesg | grep rtl
rfkill list all
```Thanks.

---

### Post by PenterX on 2015-01-30
```
 
ivan@ivan-PC:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"IVAN2"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:5D:4E:DA:AF:7A   
          Bit Rate:300 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=61/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ivan@ivan-PC:~$ dmesg | grep rtl
[  162.828006] usbcore: registered new interface driver rtl8192cu
ivan@ivan-PC:~$ rfkill list all
ivan@ivan-PC:~$ 

```

O my god it works !!!!

Thanks!

---

### Post by chili555 on 2015-01-30
> **PenterX said:**
> O my god it works !!!!

Thanks!Awesome! Please use thread tools at the top to mark Solved.

Have fun!

---

### Post by PenterX on 2015-01-31
No. It worked first time pretty good but with slow speed (about 716kbps .I  have 3mbps)
And now it can't work good - it loading pages very long and system apps can't connect to internet to load (i mean apt-get)
What Can I do?
Oh just now it works as at standart driver

---

### Post by chili555 on 2015-01-31
> Oh just now it works as at standart driverMeaning what? The old broken driver is loading or the newly compiled driver?```
lsusb
```

---

### Post by PenterX on 2015-01-31
it work like i have old driver i mean ```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 14cd:168a Super Top 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1532:0118 Razer USA, Ltd 
Bus 003 Device 002: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by chili555 on 2015-01-31
My apologies for my mis-step. I really meant:```
lsmod
```Sorry.

---

### Post by PenterX on 2015-01-31
Wait a hour. I'm want to install Debian or Linux Mint. Ubuntu is looks like Win7 but I want something you for my eyes. And I very bad installed my ubuntu with uefi

---


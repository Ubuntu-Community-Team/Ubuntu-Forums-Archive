---
title: "Wifi not working after upgrading to 14.04"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by juandescals on 2014-05-01
Hello

(This would seem a deja vu...)

I upgraded to 14.04 and my wifi connections has dissapeared. So this is the wireless-script output:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux juandescalsPB 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se

##### lsusb #####

Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####


##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

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

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
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
  Driver:            rtl8192se
  State:             disconnected
  Default:           no
  HW Address:        1C:65:9D:7E:AC:D4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        1C:75:08:CD:E3:A6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             217.11.96.234
    DNS:             217.11.108.234



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

no-auto-default=1C:75:08:CD:E3:A6,

[ifupdown]
managed=false

##### iwlist #####



```

Thank you very much

---

### Post by grahammechanical on 2014-05-01
You most likely need to install a driver. Run

```
lshw -C network
```

This is part of what I get when I run that command

>   *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:15:af:0e:9b:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.65 link=yes multicast=yes wireless=IEEE 802.11bg


Notice that on my system there is a wireless driver. Do you see "driver=something" on your system? You could try opening System Settings>Software and Updates>Additional Drivers tab and see if it has a driver for your wireless adapter.

Regards.

---

### Post by juandescals on 2014-05-02
Well, now my wifi is working, I did this:

```

sudo sed -i '/^exit 0/i iwconfig wlan0 rate 11M' /etc/rc.local

```

as I solved the same problem on 13.10 as shown here: [http://ubuntuforums.org/showthread.php?t=2203443](http://ubuntuforums.org/showthread.php?t=2203443)

---


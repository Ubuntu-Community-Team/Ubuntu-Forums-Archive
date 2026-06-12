---
title: "Wifi hard-blocked on Thinkpad T420s [ubuntu 14.04]"
date: 2016-04-16
forum: Networking &amp; Wireless
---

### Post by Siets on 2016-04-16
Hi everybody,

I'm having a problem with my wifi. I'm using a Lenovo Thinkpad t420s which I installed Ubuntu 14.04 on earlier today. For some reason, the wifi says 'Wi-Fi is disabled by hardware switch'. I tried Fn+F5, Fn+ctrl+F5, rfkill unblock all, resetting the BIOS, no dice. The hardware switch is actually physically gone-- it was ripped out with a pair of needlenose pliers, so no help there. I tried using a wireless usb dongle (Edimax EW-7811Un 802.11n), and while it shows up in the list of network adaptors, it also says 'Wi-Fi is disabled by hardware switch'. That dongle doesn't actually have a hardware switch, so I'm kind of stuck. Any help would be appreciated.

lsusb:
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 003 Device 005: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig:
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rfkill list:
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by Siets on 2016-04-16
Hi, just wanted to let everybody know I fixed it-- I blacklisted the driver being used by the internal wifi card, iwlwifi, and that unblocked the usb dongle. Now the usb dongle works and everything is great :)

---


---
title: "no visible network on wifi ubuntu 20.04"
date: 2024-11-25
forum: Networking &amp; Wireless
---

### Post by ronen43tal on 2024-11-25
install ubuntu 20.04 and connect tplink usb wifi
did all the necessary instillation of drivers.
sudo lshw -C network:

*-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:10
       logical name: wlx242fdww08af0d1
       serial: 24:2f:d0:8a:f0:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88XXau driverversion=5.15.0-126-generic multicast=yes wireless=unassociated

unable to see any networks
sudo iwlist scan 
Failed to read scan data : Resource temporarily unavailable

when:
 sudo iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

wlx242fdww08af0d1  unassociated  ESSID:""  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---


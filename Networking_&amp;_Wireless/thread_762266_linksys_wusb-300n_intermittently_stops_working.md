---
title: "linksys wusb-300n intermittently stops working"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by teddan on 2008-04-21
After a semi random period of time my wireless usb adapter(wusb-300n) stops working. Here is my demg:
[   26.560000] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   26.720000] usb 4-1: reset high speed USB device using ehci_hcd and address 2 
[   26.892000] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco System 
s, Inc.,09/26/2007,1.0.7.2) loaded 
[   27.976000] wlan0: ethernet device 00:1a:70:b1:39:a6 using NDIS driver: netmw 
245, version: 0x1000402, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 13 
B1:0029.F.conf 
[   27.976000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2 
PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[   27.976000] usbcore: registered new interface driver ndiswrapper 

If I try “/etc/init.d/networking restart” it starts then when trying to get an address it hangs disabling my logitech wireless keboard but not my wireless mouse. Restarting is the only thing that helps. I checked /var/log/messages and nothing really stood out. This machine and NIC were working fine during it's precvious life as a Windows box so I don't think it is a hardware issues. This is not specific to when hibernate occurs etc. As an example when I try to scp files from another machine on the LAN networking dies after about 25 Mbs. Also other Wireless devices on LAN still work so it's not an issue with teh router which is  Netgear something or other. Any ideas would be appreciated. 

AMD Athlon 1500+ 2 Ubuntu 7.10 gutsy.  
iwconfig:
wlan0     IEEE 802.11g  ESSID:"stayout"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:2F:64:F1:1A   
          Bit Rate=216 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thanks in advance,
Ted

---


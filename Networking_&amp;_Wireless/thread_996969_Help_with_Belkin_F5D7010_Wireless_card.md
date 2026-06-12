---
title: "Help with Belkin F5D7010 Wireless card"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by msbealo on 2008-11-29
Hello,

Only in the last few days have I installed Ubuntu (8.10) for the first time. Everything looks good, but I'm having real difficulty with my Wireless card. 

I've search and search for information and help on this issue and have finally decided to post this question.

OK. I have an Acer Aspire 1350 with a PCMCIA Belkin F5D7010. I've been trying to get this working with ndiswrapper using the bcmwl5a.inf driver. 

The power light is on, I can see wireless networks but I can not connect. 

Here are various outputs:

:~$ lspci -nn
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

I therefore installed the bcmwl5a,inf drivers.

:~$ ndiswrapper -l
bcmwl5a : driver installed
	device (14E4:4320) present (alternate driver: ssb)

I'm using the driver from the R81433 package. This appears to be working.

:~$ lshw -C Network
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: 00:11:50:04:31:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,06/25/2004, 3.40.7 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

p:~$ dmesg |grep -e Network -e wlan
[   29.585133] wlan0: ethernet device 00:11:50:04:31:aa using NDIS driver: bcmwl5a, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   29.585720] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  118.170268] ADDRCONF(NETDEV_UP): wlan0: link is not ready


As I said above, I can see the available networks in the Network Manager (the icon my the clock) and if I do

:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 03 - Address: 00:1C:DF:41:8E:3B
                    ESSID:"xxxxxxxxxxx"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

Therefore at least something is working but I can't connect to the network.

:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:11:50:04:31:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:34000000-34002000 


My router is a Wireless Belkin Router which I can connect to with a wire. The security of the Belkin router is set for WPA/WPA2 and I can see the key so therefore know that I've got that bit right.

Could people please help me get the wireless card working. If you do reply to this could you please outline exactly what you mean as I'm not very good with Linux (despite having an on-off relationship for over ten years!)

Cheers,

Mark

---


---
title: "Slow Wireless Connection with DSL-G630"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by hansonlee on 2005-09-14
I am using D-link DWL-G630 cardbus wireless card, and use MADWIFI driver. The wireless card shows up, connected successfully to the access point, and IP address assigned. I can ping 4.2.2.2 and [www.google.com](www.google.com) without a problem with latency at about 16-20 ms. However, I can't connect to any site thru firefox. The status bar shows site connected and waiting for the site the response, but nothing happen afterward. Then I got the timeout error. Also, the time to resolve google's address seems much longer than wired connection, as well as the pauses between pings. I tested the wireless card and router on my brother computer (which runs XP) and they work fine. 

Anyone can solve the mystery?

My setting:
root@Hyperion:~/madwifi# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XXXXXXX"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:F3:87:A8
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX   Security mode:restricted
          Power Management:off
          Link Quality=30/94  Signal level=-65 dBm  Noise level=-95 dBm
          Rx invalid nwid:32  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

--------------------------------------------------------------------------------

root@Hyperion:~/madwifi# ifup ath0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:13:46:21:96:b9
Sending on   LPF/ath0/00:13:46:21:96:b9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
5 bad udp checksums in 6 packets
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.147 -- renewal in 37877 seconds.

--------------------------------------------------------------------------------

PINGING 4.2.2.2

root@Hyperion:~/madwifi# ping 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=247 time=6.01 ms
wrong data byte #8 should be 0x8 but was 0xc
#8      c 12 18 60 c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 29 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 4.2.2.2: icmp_seq=2 ttl=247 time=5.37 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=247 time=3.83 ms
wrong data byte #8 should be 0x8 but was 0xc
#8      c 12 18 60 c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 29 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 4.2.2.2: icmp_seq=4 ttl=247 time=3.68 ms
64 bytes from 4.2.2.2: icmp_seq=5 ttl=247 time=3.98 ms
wrong data byte #8 should be 0x8 but was 0xc
#8      c 12 18 60 c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 29 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 4.2.2.2: icmp_seq=6 ttl=247 time=3.60 ms

--- 4.2.2.2 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5019ms
rtt min/avg/max/mdev = 3.607/4.416/6.018/0.932 ms

--------------------------------------------------------------------------------

PINGING GOOGLE

root@Hyperion:~/madwifi# ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.7.99) 56(84) bytes of data.
64 bytes from 66.102.7.99: icmp_seq=1 ttl=242 time=13.1 ms
wrong data byte #8 should be 0x8 but was 0xc
#8      c 12 18 60 c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     28 29 2a 2b 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 66.102.7.99: icmp_seq=2 ttl=242 time=12.8 ms
64 bytes from 66.102.7.99: icmp_seq=3 ttl=242 time=13.2 ms
64 bytes from 66.102.7.99: icmp_seq=4 ttl=242 time=13.2 ms
64 bytes from 66.102.7.99: icmp_seq=5 ttl=242 time=12.9 ms
wrong data byte #8 should be 0x8 but was 0xc
#8      c 12 18 60 c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20 21 22 23 24 25 26 27
#40     e8 83 f 8 2c 2d 2e 2f 30 31 32 33 34 35 36 37
64 bytes from 66.102.7.99: icmp_seq=7 ttl=242 time=12.7 ms
64 bytes from 66.102.7.99: icmp_seq=8 ttl=242 time=23.1 ms
64 bytes from 66.102.7.99: icmp_seq=9 ttl=242 time=12.9 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 31084ms
rtt min/avg/max/mdev = 12.791/14.299/23.178/3.362 ms





My computer:

Acer Travelmate 345T, PIII-600, 128 MB

---

### Post by mlomker on 2005-09-14
Firefox works fine through the wired ethernet?  

I've seen some bizarre things in firefox, myself.  I find that when I switch network connections (from wired to wireless or back) that I have to close and then reopen firefox or it will hang forever.  I run KDE and Konqueror does not have that problem.

---

### Post by hansonlee on 2005-09-15
Yes, Firefox works just fine with the wired connection, but never with the wireless. I've tried starting with only wireless network, but that didn't work, either.

---

### Post by firecat53 on 2005-09-15
Hey...I also have the DWL-G630 and am using it successfully with Madwifi/wpa_supplicant.  I had to download and compile the most recent versions from the respective websites of the Madwifi drivers and wpa_supplicant in order to get it working. Are you using the Ubuntu repository version of Madwifi?  There's some good tutorials on the Madwifi site for compiling the drivers. I'm pretty new and I figured it out without (heh, heh) Too much trouble! I couldn't get it working at all without the new driver! 

good luck! Let me know if I can help more.

Scott

---

### Post by hansonlee on 2005-09-16
Thanks, firecat53, for the encouragement.

I compile the latest MADWIFI according to the instruction found on the website. I am not sure I did everything right, but the driver seems to work and detect the card upon booting. I wasn't using WPA encryption (just WEP), so I didn't install WPA_supplicant. Maybe we can compare the messages when using "ifup" (mine is in the original post)

---

### Post by firecat53 on 2005-09-17
So are you still observing the same behavior with the new driver? Anything different at all?

Scott

---

### Post by hansonlee on 2005-09-17
I was using the compiled MADWIFI driver

---

### Post by firecat53 on 2005-09-17
I understand you are using the most recent Madwifi driver that you compiled. Did you verify that when you loaded the new driver with modprobe that it actually loaded the new driver and not the old one? If you have the new driver loaded, did that change anything when you try to start the connection? Can you post outputs from your if/iwconfig, ifup and ping? 

Scott

---

### Post by hansonlee on 2005-09-18
Sorry I didn't make this clear. I was using the compiled MADWIFI from the beginning.
The ifup, ping etc are in the first post.


Added:  I am not sure how to use modprobe in this case. I just started to use linux system.

---

### Post by hansonlee on 2005-09-20
I did a clean installation of Ubuntu. Then proceed with the installation of MadWifi. Still the same problem. I can get an IP address from the router, but connection speed is ridiculously slow. It can still get the time synchornization to work as well.  Ping still works, and latency is low, but the pauses between each ping is extremely long compared to wired connection, as if the card is relucant to work. 

Here is my dmesg message, if there's any help,

ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: mac 7.8 phy 4.5 radio 5.6
ath0: 802.11 address: 00:13:46:21:96:b9
ath0: Use hw queue 0 for WME_AC_BE traffic
ath0: Use hw queue 1 for WME_AC_BK traffic
ath0: Use hw queue 2 for WME_AC_VI traffic
ath0: Use hw queue 3 for WME_AC_VO traffic
ath0: Atheros 5212: mem=0x10800000, irq=9
ath0: no IPv6 routers present

---


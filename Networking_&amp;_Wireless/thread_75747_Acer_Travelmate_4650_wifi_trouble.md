---
title: "Acer Travelmate 4650 wifi trouble"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by ked on 2005-10-14
I rearly give up something, but now I'm pretty close. No matter how much I try I can't connect to my wireless router when I use WEP. It works just fine with an open unsecured network. I'm using the ipw2200-1.0.6 driver.

Here is what I do:

$ sudo iwlist eth1 scan

          Cell 01 - Address: 00:C0:02:C2:AB:BC
                    ESSID:"<my wireless network>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key: on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=42/100  Signal level=-75 dBm
                    Extra: Last beacon: 239ms ago

$ sudo iwconfig eth1 essid <my wireless network>
$ sudo iwconfig eth1 key 0123456789
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"<my wireless network>"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr: off   Fragment thr: off
          Encryption key:1234-5678-90   Security mode: open
          Power Management: off
          Link Quality=42/100  Signal level=-75 dBm  Noise level=-86 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 463   Missed beacon: 4


sit0      no wireless extensions.

$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:58:d6:f9
Sending on   LPF/eth1/00:12:f0:58:d6:f9
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 192.168.1.104
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
$ 

As you can see - no sucess. (Without encryption everythings great.)

What puzzles me is that the key is changed from:

0123456789 to 0123-4567-89 (look in the output from the iwconfig command). And yes, I've tried:

$ sudo iwconfig eth1 key s:0123456789

without success. The iwconfig command then returns for the key:

Encryption key:3078-3132-3334-3536-3738-3900-00

HELP! What is wrong here????

---

### Post by dave1111 on 2005-10-14
I had to get ACPI working and load the acerhk-module which turned on the kill switch of the wlan. Before no wlan-light was blinking. I don't know if this is the case with the Travelmate 4650, I have the Aspire 1694.
Look here:
[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

---


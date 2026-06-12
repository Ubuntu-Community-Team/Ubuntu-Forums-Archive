---
title: "IP Addresses and aliases... I'm a n00b"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Boondock5 on 2007-10-28
I accidently deleted everything in the "Hosts" window in network settings for the wireless internet. Now i got no internet. it worked great before I did that.
I got the rest of the settings figured out, just completely at a loss now. Any help would be appreciated.
(Note; I'm on my wifes computer now, till I get mine back up. Ick! I'm sick of winders!)

---

### Post by Boondock5 on 2007-10-28
here is every bit of info I could find from the system in question;

boondock5@boondock5:~$ sudo iwlist
[sudo] password for boondock5:
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
boondock5@boondock5:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"MATTBURG"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:37:54:CB   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

boondock5@boondock5:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:37:54:CB
                    ESSID:"MATTBURG"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

boondock5@boondock5:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
boondock5@boondock5:~$ iwevent
Waiting for Wireless Events from interfaces...
boondock5@boondock5:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth1
boondock5@boondock5:~$ 



so what do I do now, I'm lost and hav'nt a clue what to do now.

Thanks in advance.

---


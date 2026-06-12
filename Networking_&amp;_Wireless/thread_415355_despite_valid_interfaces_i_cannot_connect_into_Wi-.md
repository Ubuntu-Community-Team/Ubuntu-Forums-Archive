---
title: "despite valid interfaces i cannot connect into Wi-fi network"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by szymon_g on 2007-04-20
hi.
i've installed FF in alternate mode yesterday.
i've setup network (network card is wi-fi : intel pro 3945abg) (this is my /etc/network/interface)

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid SpeedTouchBCE72F

and iwconfig see my card connected to wi-fi network
eth1      IEEE 802.11g  ESSID:"SpeedTouchBCE72F"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:AE:51:96   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=74/100  Signal level=-62 dBm  Noise level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


despite it i cannot connect to network... ping doesn't work (for 255.255.255.0 and for 'normal' addresses like [www.google.pl](www.google.pl))

the problem had occured after my router have been power-of by accident :-/.
before it i have good connection, with the same configuration.
i've tried ifup & ifdown but i still cannot make connection...

any suggestions?

szymon (simon)

---


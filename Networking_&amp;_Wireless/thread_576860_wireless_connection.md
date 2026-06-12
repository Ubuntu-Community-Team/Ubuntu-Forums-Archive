---
title: "wireless connection"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by bobheaps on 2007-10-15
I am new to LINUX.
I installed UBUNTU 7.04 on my desktop 2 months ago and really liked it. I installed the same on my partners laptop just over a week ago and everything is fine except the wireless part. We can access the internet via a wired connection but no luck via wireless. Everything worked OK under windows XP but I do not want to go back there,
I tried to read all the how-tos and got some help via the forum but still no luck 
Here is what I have done so far:-
Downloaded ndiswrapper and installed it
Got the windows driver 80211g.zip
installed all the packages I could find relating to wireless.
I then ran a number of apps as follows:- 
The Output of ndiswrapper -l is:-

root@msforcier-laptop:~# ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present
root@msforcier-laptop:~#

The Output of modprobe is:-
root@msforcier-laptop:~# modprobe ndiswrapper
root@msforcier-laptop:~#

The Output of iwconfig is:-
root@msforcier-laptop:~# iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=1 Mb/s
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:6D79-6163-6365-7373-706F-696E-74   Security mode:restricted
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@msforcier-laptop:~#

The Output ofdhcliednt is:-
root@msforcier-laptop:~# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6356
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0e:9b:89:81:52
Sending on   LPF/wlan0/00:0e:9b:89:81:52
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@msforcier-laptop:~#

---


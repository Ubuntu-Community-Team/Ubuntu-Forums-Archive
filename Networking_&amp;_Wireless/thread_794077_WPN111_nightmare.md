---
title: "WPN111 nightmare"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Richard_Au_2006 on 2008-05-14
Hello,

I have Netgear adapter WPN111.  Did a fresh install of Ubuntu 8.04.
'Out of the box' wireless network does not work.
I attempted to unplug/plug this USB network adapter but it did not help.
Then installed ndiswrapper with the Windows XP driver.  Now ndiswrapper -l reports that driver and hardware are present but again I cannot see my wireless anywhere. iwconfig simply reports on 'lo' and on 'eth0' nothing else.
wpasupplicant is also installed.
I attempted to remove NetworkManager did not help either.
Installed it back did not help.
Looking at lsmod against the usbcore I can only see ndiswrapper (and related entries) no other driver that clashes with ndiswrapper.
Any ideas how can I finally make my wireless work?

---

### Post by aolias on 2008-05-22
Hi I have the same wireless card and worked fine with Ubuntu 7.10
Check this post
[http://ubuntuforums.org/showthread.php?t=571188&page=50](http://ubuntuforums.org/showthread.php?t=571188&page=50)

With Ubuntu 8.04 the wireless is detected and it works when you do not use security, but wpa_supplicant is not working fine. Neither WPA nor WPA2

I am going to give up and reinstall 7.10

---

### Post by DrRSP on 2008-05-26
Hi,

Damn! This was the reason I upgraded to Harrdy Heron, in the hope that wireless would be a little more straight forward! I also found that I occasionally had a USB insufficient power warning. Although on the plus side the Netgear WPN 111 wireless adapter was recognised in device manager (once I downloaded it & why was it not included in the install??), but not listed in network manager.

I was then considering the ndiswrapper fix. I guess not, unless there is any further advice out there (please don't say go backwards!). Thanks.

---

### Post by DrRSP on 2008-10-29
**Situation:**
I'm still a newcomer to linux (even after the earlier posts), and finding wireless networking far too time consuming and frustrating!  I have a dell laptop with a Netgear WPN111 usb wireless adapter. I checked the ubuntu doc etc and appear to be going around in circles, although I did find the wifi docs wireless troubleshooting guide excellent. I lost the plot on notes on WPA (3.3.2) though.

Having installed ndiswrapper, WPA supplicant etc., I cannot get WPA to work. However, I can use manual configuration for an open unsecured connection.

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:96:19:bb
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe96:19bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2035599 (1.9 MB)  TX bytes:244261 (238.5 KB)

**Symptoms:**
Using network administration (manual configuration) WPA settings are:
Roaming unchecked
Wireless connection
EESID router1
WPA Personal (WPA and WPA2 on Router)
Password in ASCII (same as Router)

Driver OK, just for good measure, lshw:

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:96:19:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.52+NETGEAR,09/26/2005,1.5.0.21 multicast=yes wireless=IEEE 802.11g

Still no connection is found in iwconfig (below):

iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:96:19:bb
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0f:b5:96:19:bb
          inet addr:169.254.7.71  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

file:///etc/modprobe.d/ndiswrapper:
alias wlan0 ndiswrapper
file:///etc/network/interfaces:

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid router1

auto wlan0
file:///etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

**Finally**
I also note that I've edited my wireless network using the gnome nm-editor 0.6.6 from the launcher.... settings appear stored (in network interfaces above, could there be a clash for binding to ndiswrapper?).

Help! It was never this hard in windows, but I don't want to go back there! Is there simple step by step advice I've missed (I've looked and I'm now confused, with different network managers and auto start up configurations)... Either that or could some kind soul take pity. Thanks in anticipation.](*,)

---

### Post by aolias on 2008-11-10
[http://ubuntuforums.org/showthread.php?p=5670733](http://ubuntuforums.org/showthread.php?p=5670733)

But only works with WEP for me.

---

### Post by Mark224 on 2008-11-10
Have you created the /etc/wpa_supplicant.conf file?  I needed one to get WPA(2) working with manual configuration.  This file will contain your SSID & passphrase.

Have a look at the manual page.  When you have created this file then add the following line to /etc/network/interfaces
```

wpa-conf /etc/wpa_supplicant.conf

```
and reboot.

---


---
title: "Xubuntu Hardy Wicd wpa &quot;no wireless networks found&quot;"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by westfork on 2008-09-10
New user here, can't get wicd to find my wpa wireless net on an xubuntu hardy install on a fujitsu lifebook. I can connect if and only if I go into network settings, clear the wpa password, re-enter it, and apply. Would appreciate advice...

Hopefully useful info follows:

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:3B:66:DE
                    ESSID:"HOMENET"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Signal level=76/127  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001fcb8df2a41

:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:09:5b:e8:cc:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci ip=192.168.1.5 latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g

:~$ sudo cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid HOMENET

auto wlan0


:~$ sudo iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  Mode:Managed  Frequency:2.452 GHz  
          Access Point: 00:3B:6C:0F:66:ED  Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx [2]
          Link Signal level=79/127  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0

Thanks in advance!

---

### Post by Ludachrispeed on 2008-11-11
I'm having the same problem in ubuntu.  When you said you could change things in network settings... where is "network settings?"

Wicd was working yesterday... now it can't find any wireless networks.  I've tried reinstalling via Synaptic with no success.  Anyone have any ideas?

Thanks much

---


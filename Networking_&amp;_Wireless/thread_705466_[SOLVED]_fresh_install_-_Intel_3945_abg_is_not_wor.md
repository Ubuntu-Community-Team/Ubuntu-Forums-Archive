---
title: "[SOLVED] fresh install - Intel 3945 abg is not working"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by muellthos on 2008-02-23
Hi,

I have a new DELL Latitude D830 Notebook, with a Inter 3945abg. On this notebook should only run vmware-server. So I decided to install from the 7.10 alternative install CD. I istalled a "command line only" system. During the install I had connection over the wired interface. Now I can't get the WLAN to work. I read some threads here, including the sticky ones about supported cards and the WPA/LEAP Howto. 

I try to conncet to a Fritzbox WLAN (wide used in Germany)  with WPA-PSK, WPA2 TKIP.

Meanwhile I installed also xorg, kde-core, adept and after some failures KWLAN. This was the first tool which gave me a clue: It states: can't configure eth1 with iwconfig. This may be due an absent program or a misconfiguration. But I don't know, where to look.

I didn't found eth1 in /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

I put eth1 in there, but it made no difference.

If  I do an iwlist , I can find the interface 

eth1      Scan completed :
          Cell 01 - Address: 00:1A:4F:8F:53:E2
                    ESSID:"MUELLERIHT"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-29 dBm  Noise level=-29 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 200ms ago


Not having wireless is an absolute show-stopper for me.

Thomas

---

### Post by muellthos on 2008-02-26
Solved it by using the iwlwifi drivers, which I got somehow. What I've done is only blacklist the ipw3945 in /etc/modprobe.d/blacklist to prevent modprobe from loading it, and also put the iwl3945 in /etc/modules. Works for me so far.

Thomas

---


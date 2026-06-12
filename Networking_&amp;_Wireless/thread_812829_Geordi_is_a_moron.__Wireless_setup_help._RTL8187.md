---
title: "Geordi is a moron.  Wireless setup help. RTL8187"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by Geordi on 2008-05-30
Computer: Gateway MT 6452 Laptop
Operating system: Ubuntu 8.04 Hardy Heron - Kernel 2.6.24-17-generic
Hardware Issue: Unable to log in to WEP network w/ RTL8187 internal wireless card.

  For some reason a week ago, my wireless stopped working on my Gateway MT652 with a RTL 8187 internal wireless card.  Since then, I have done a lot of stupid things to try to get it running again.  I can't say for certain everything I did or didn't do, but here is what I know about my system right now.


Ndiswrapper is running and as far as I can tell, configured properly.  Programs such as wifi-radar can see all the available networks.

lsmod does list ndiswrapper.  I have loaded it with the win98 driver netrtuw.  I have removed the driver libcmd and can no longer find it.  Was it important? :mrgreen:

iwconfig has this to say:

[COLOR="Blue"]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]

Here is lshw -C network:


[COLOR="Blue"]WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d4:43:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.103 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:e3:c5:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.52+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
[/COLOR]

Finally, here are the customized contents of /etc/network/interfaces

[COLOR="Blue"]
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wmaster0

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-key [COLOR="Red"]I don't know how to stop the smilies!![/COLOR]
wireless-essid ktbug

auto wlan0[/COLOR]

Bear in mind that, being a moron I have half-assed my way though several terminal based guides here on the forums and have committed such atrocities as putting files in /etc/default named NetworkManager which only contain the phrase "exit." I would like to get that applet running again. :confused:

So, that's my problem in a nutshell.  My curiosity writes cheques my brain can't cash.

---

### Post by chili555 on 2008-05-30
Well, you seem to have a few conflicts here. > NetworkManager which only contain the phrase "exit." I would like to get that applet running againI think a lot of people have difficulty with Network Manager and so I would not be so anxious to get trouble working again. I'd suggest we work with wifi-radar for now.

Your */etc/network/interfaces* ffile look like it could be tweaked. I suggest amending it to:```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-key <ur_WEP_key>
wireless-essid ktbug
```Please do:```
sudo iwlist wlan0 scan
```Please make sure your ESSID is actually ktbug and not Ktbug or KTBug, etc. Wireless encryption will not accept 'close enough.' Amend your interfaces file as needed.

Finally, let's ttroubleshoot your WEP key. What is its length?
# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters

If your key is ASCII, precede the key in *interfaces* with s:, like this:```
wireless-key **s:**<ur_ASCII_key>
```When you restart networking:```
sudo /etc/init.d/networking restart
```do you connect?

---

### Post by Geordi on 2008-06-01
No connection for me.  After I enter:

[COLOR="Blue"]sudo /etc/init.d/networking restart[/COLOR]

I was told:
[COLOR="Blue"]
jarmitage@jarmitage-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 9255
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:b8:d4:43:64
Sending on   LPF/eth0/00:e0:b8:d4:43:64
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9325
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:c0:a8:e3:c5:0b
Sending on   LPF/wlan0/00:c0:a8:e3:c5:0b
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:b8:d4:43:64
Sending on   LPF/eth0/00:e0:b8:d4:43:64
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 38983 seconds.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:c0:a8:e3:c5:0b
Sending on   LPF/wlan0/00:c0:a8:e3:c5:0b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ][/COLOR]

And here are the results of [COLOR="Blue"]sudo iwlist wlan0 scan[/COLOR]

[COLOR="Blue"]
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:C5:D7:E1
                    ESSID:"Sandy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:18:F8:3C:F3:4F
                    ESSID:"DjHome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1A:70:4A:C2:F2
                    ESSID:"ktbug"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:6C:9C:03:D2
                    ESSID:"BFG90"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:06:25:E7:6A:E1
                    ESSID:"natallah"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:1F:33:34:BE:10
                    ESSID:"SpeedRacer"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK[/COLOR]

Other than that I followed the directions to a T with the exception of auto-enabling eth0 under my  /etc/network/interfaces.

Any more ideas?

---

### Post by chili555 on 2008-06-01
> DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 38983 seconds.Evidently you had your wired ethernet connected and tried the commands before you amended *interfaces.* Please detach the wire and do:```
sudo /etc/init.d/networking restart
```

---


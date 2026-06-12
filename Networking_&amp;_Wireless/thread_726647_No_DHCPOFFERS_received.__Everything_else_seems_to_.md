---
title: "No DHCPOFFERS received.  Everything else seems to look OK though."
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by kmatthews812 on 2008-03-16
I recently switched from Comcast to FIOS and, with a new router, now my wireless networking has stopped working.  Other than updating my ESSID and WEP key, I have changed nothing on my Gutsy system.  I also tried this with encryption turned off and had the same results of "no DHCPOFFERS received".  I have also tried setting up a static IP address, but had no success with that either.  

Everything seems to look OK.  My wireless card is recognized, and I can see my wireless network, but when I try to restart my network, it cannot obtain an IP address.  Here is the relevant outputs:

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:FB:61:5D
                    ESSID:"583Y6"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:8c:a9:9e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.51+Linksys,04/21/2005, 3.00.03 ip=192.168.1.61 latency=32 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                        
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9453
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:8c:a9:9e
Sending on   LPF/wlan0/00:12:17:8c:a9:9e
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:8c:a9:9e
Sending on   LPF/wlan0/00:12:17:8c:a9:9e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                          
      
                                                                                                                
$ sudo ndiswrapper -l
rt2500 : driver installed
        device (1814:0201) present (alternate driver: rt2500pci)


$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"583Y6"  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-109 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:XXXX-XXXX-XX   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


$ sudo cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key XXXXXXXXXX
wireless-essid 583Y6

auto wlan0





Any ideas on what I can do to fix this?  


Thanks,

Kev

---


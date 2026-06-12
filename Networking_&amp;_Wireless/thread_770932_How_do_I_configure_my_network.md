---
title: "How do I configure my network?"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Lourie2 on 2008-04-27
I am having difficulty in connecting with my Belkin USB adapter to the wireless network.  I tried to follow the procedure in the Sticky How To: Manual Network Configuration without the need for Network Manager, but have been unsuccessful.  The driver has been added correctly, and I can see the network I am to connect to. (See attachment for the results) Unable to attach a .txt file!!!, here follows:

[Code]
 *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:33:be:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52

wlan0     Scan completed :
 Cell 02 - Address: 00:1D:68:0A:45:B5
                    ESSID:"O2wirelessC23902"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

The problem starts when I hit the following commands:

lourie@lourie-IBM:~$ sudo ifconfig wlan0 down
[sudo] password for lourie: 
lourie@lourie-IBM:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1c:df:33:be:0b
Sending on   LPF/wlan0/00:1c:df:33:be:0b
Sending on   Socket/fallback
lourie@lourie-IBM:~$ sudo ifconfig wlan0 up
lourie@lourie-IBM:~$ sudo iwconfig wlan0 essid "O2wirelessC23902"
lourie@lourie-IBM:~$ sudo iwconfig wlan0 key HEX_KEY 2710DD3B8D
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "HEX_KEY".
lourie@lourie-IBM:~$ sudo iwconfig wlan0 key s:ASCII_KEY 2710DD3B8D
lourie@lourie-IBM:~$ sudo iwconfig wlan0 key 2710DD3B8D
lourie@lourie-IBM:~$ sudo iwconfig wlan0 mode Managed
lourie@lourie-IBM:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1c:df:33:be:0b
Sending on   LPF/wlan0/00:1c:df:33:be:0b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
lourie@lourie-IBM:~$ [Code]

How do I go forward from here?

---


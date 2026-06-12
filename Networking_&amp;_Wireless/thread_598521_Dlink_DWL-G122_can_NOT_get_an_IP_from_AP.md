---
title: "Dlink DWL-G122 can NOT get an IP from AP"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by romanchr on 2007-10-31
Hi all,

After running Suse for a while a decided to switch to REAL open source :KS and installed ubuntu server 7.10. The system identfies itself with 2.6.22-14-server.

Everything went fine except that I can not get my DWL-G122 (rev B1, F/H 1.00) running. I am not exactly sure what is missing fact is I can not get a IP from my AP.
Ubuntu recognised the usb device and made it available as wlan0. Here is the output of lsusb:
> Bus 001 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]

If I run lshw | grep -A 10 network I get the follwoing output: 
> *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:95:d0:54:f3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

That looks good to me. If I run iwlist wlan0 scan I get the following output:
> wlan0     Scan completed :
          Cell 01 - Address: 00:14:C1:0B:1D:E6
                    ESSID:"Hem"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-44 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000121f80bef9


Again looks rather promising. Based on what I knew (and googled) I extended /etc/network/interfaces with the following lines:
> iface wlan0 inet dhcp
wireless-essid my-essid
wireless-key s:my-10-digit-key
auto wlan0

Just for all security-leek-pointers: I know WEP is not what one could call secure but it will do fine for now :) .

Done that I run  sudo ifup wlan0 and get:
> There is already a pid file /var/run/dhclient.wlan0.pid with pid 4993
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:95:d0:54:f3
Sending on   LPF/wlan0/00:11:95:d0:54:f3
Sending on   Socket/fallback
christophr@linuxsrv:/tmp/RT73_Linux_STA_Drv1.0.4.0/Module$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:95:d0:54:f3
Sending on   LPF/wlan0/00:11:95:d0:54:f3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Now why do I not get an IP? (I can execute iwconfig wlan0 ap 00:14:C1:0B:1D:E6 without getting error messages)

What is the wmaster0?
And what does *unknown hardware address type 801* mean (my guess: its a driver thing???)

Since i spent quite a while googling I also tried to install ralink driver (tried 2570 and 73) but without any success. It feels like I could install them but not link to the network card.

Any help is greatly appreciated!

Best regards

romanchr

Ps: sorry for the wrong first post

---


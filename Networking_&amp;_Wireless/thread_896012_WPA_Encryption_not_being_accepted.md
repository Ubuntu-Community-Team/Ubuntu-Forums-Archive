---
title: "WPA Encryption not being accepted"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Ken Milburn on 2008-08-20
My wireless PCI card problem appears to associated with WPA encryption.

My system dual boots between winXP and Ubuntu 8.04
Winxp works correctly.

I have a pci D-Link WDA-13210 which uses the Atheros AR2413 chipset.
I have tried Ndiswrapper with the XP driver and now I have the madwifi 0.9.4 driver.  I get the same results from both drivers.

iwlist scan works and shows three signals in my area.

dmesg | grep -e iwl -e eth -e wlan
shows the encryption modes are support and reports 'wlan0 is not ready'.

Earlier I tried the router with no encryption and the wireless connected and worked.

I have tried without success to configure wpa_supplicant.  Reading the different posts I see reference to editing wpa_supplicant.conf which is to be in /etc/  or in an other post to be in /ect/wpa_supplicant/ so I tried it in both locations.  

I am now at a loss as to what to do next.

---

### Post by Ken Milburn on 2008-08-21
Situation update.
After a good nights sleep I started over again.
Following the Sticky posting "How To: Manual Network Configuration without the need for Network Manager" I discovered the following:
  1. My madwifi driver was not working  I got "Network:1 UNCLAIMED"
  2. My ndiswrapper with winxp driver does work.
  3. My logical name: wlan0
  4. Unencrypted Connection works.  I get the:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.2.3 from 192.168.2.1
DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 928144630 seconds.

However
   5. Attempts using encryption WEP or WPA1 or WPA2 do not work.
Using the command $ sudo dhclient -r wlan0

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:58:9b:78:0f
Sending on   LPF/wlan0/00:1e:58:9b:78:0f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

Using the command $ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:58:9b:78:0f
Sending on   LPF/wlan0/00:1e:58:9b:78:0f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

So, I take it that my DHCP doesn't want to talk to me if I use encryption.
The README at [www.isc.org/sw/dhcp/](www.isc.org/sw/dhcp/) had a couple of suggestions relating to sending all ones, which did not change the situation.

Any suggestions or should I repost referring to the DHCP problem?

---


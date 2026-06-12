---
title: "Weird Network Issues"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by Princey on 2007-02-28
I did a fresh install of Edgy after messing my previous installation up trying to get my HP ScanJet to work. Installed all updates after getting wired access to the net and proceeded to install my other apps. Things went smoothly until I rebooted. Opera no longer could connect to the Internet, neither Firefox however, I can connect using Konqueror :( :confused:

For some reason, no matter what I do I can't get wireless working (it worked under edgy before I did a clean re-install) no matter what I try. I have my wpa_supplicant file set up and pointed to in /etc/network/interfaces yet KnetworkManager has it greyed out. I can disable and enable it though in KnetworkManager, just not the option to imput the information that I have in the wpa_suppicant.conf file. If I disable the wired connection, I can connect to my router without a problem.

Here's the results from various tests:
```
iwconfig
```,
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:6406  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
,

```
cat /etc/network/interfaces
```,
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth0

auto ath0
iface ath0 inet dhcp
wpa-conf /home/emmjay/.wpa/wpa_supplicant.conf
SSID MCES Network
#auto wlan0
,

```
sudo /etc/init.d/networking restart
``` brings up > * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 5113
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:96:1a:aa
Sending on   LPF/ath0/00:13:46:96:1a:aa
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 6335
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:15:58:08:55:01
Sending on   LPF/eth0/00:15:58:08:55:01
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:15:58:08:55:01
Sending on   LPF/eth0/00:15:58:08:55:01
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.105 -- renewal in 238656 seconds.
There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:96:1a:aa
Sending on   LPF/ath0/00:13:46:96:1a:aa
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

Any ideas would be welcomed. The D-Link Card uses the atheros chipset.

---

### Post by Floppyjoe on 2007-02-28
> For some reason, no matter what I do I can't get wireless working (it worked under edgy before I did a clean re-install) no matter what I try. I have my wpa_supplicant file set up and pointed to in /etc/network/interfaces yet KnetworkManager has it greyed out. I can disable and enable it though in KnetworkManager, just not the option to imput the information that I have in the wpa_suppicant.conf file. If I disable the wired connection, I can connect to my router without a problem.

I think you need to have all the network interfaces disabled in order for network manager to work properly and it looks like that is what you did with the wired interface.

---

### Post by RomeReactor on 2007-02-28
> **Princey said:**
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

[B]iface eth0 inet dhcp

auto eth0[/B]

auto ath0
iface ath0 inet dhcp
wpa-conf /home/emmjay/.wpa/wpa_supplicant.conf
SSID MCES Network
#auto wlan0

I suggest you comment out the lines in **bold** so the file reads

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet dhcp

#auto eth0

auto ath0
iface ath0 inet dhcp
wpa-conf /home/emmjay/.wpa/wpa_supplicant.conf
SSID MCES Network
#auto wlan0
```

Reboot and see if that solves your problem.

---

### Post by Princey on 2007-02-28
If I disable the ethernet card, I'll be removing my only source to the internet at the moment and I've already tried that. I can ping my router using both cards. That still doesn't explain why I can't connect to the web using Firefox or Opera whereas using Konqueror I can.

---

### Post by Princey on 2007-02-28
> **Floppyjoe said:**
> I think you need to have all the network interfaces disabled in order for network manager to work properly and it looks like that is what you did with the wired interface.

I never had to disable the interfaces before I reformatted and everything worked fine. Disabling them in the network settings under KControl disables them completely. I've tried doing that but KnetworkManager is only able to enable it back again, not connect to the internet. I must add here that the wireless card and the ethernet do get correct IP addresses as assigned by the router.

---

### Post by Princey on 2007-02-28
Alright, I managed to solve the weird differences between Firefox, Opera VS Konqueror. Turned out that I edited the hosts file to block known adware sites and the pesky ad sites. Is there a way like under Windows that I can create a list of blocked sites?


-----------------------------
Update.

Got everything resolved. Removed Knetwork Manager completely along with some of the howto's I followed and resorted to an old howto I made for someone requesting help. Installed kwlan and pronto, there's net. Got a way to edit my hosts file as well. I'm now blocking the pesty ads and surfing using my wireless card at the moment.

---


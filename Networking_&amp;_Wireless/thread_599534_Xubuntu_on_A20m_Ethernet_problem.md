---
title: "Xubuntu on A20m Ethernet problem"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by tdb1001 on 2007-11-01
Recently installed Xubuntu 7.10 on my old A20m IBM Thinkpad. Prior to this install it had an older version of RedHat Fedora installed with which I had no problem accessing the internet.

The A20m is connected to the internet via an ethernet connection to a dumb 4-port hub to which a working desktop Ubunutu system is also connected. No problem accessing the internet on the desktop.

Since the Xubuntu install I am able to successfully ping my desktop system (due to avahi-autoip kicking in after dhclient3's attempts fail to dynamically assign an IP address) but I have no internet connectivity. Bringing up the Connection Information window shows the following:

[COLOR="RoyalBlue"]    Interface: Wired Ethernet (eth0)
    Speed:      10 Mb/s
    Driver:     3c59x

    IP Address:             0.0.0.0
    Broadcast Address: 0.0.0.0
    Subnet Mask:         0.0.0.0
    Default Route:        0.0.0.0
    Primary DNS:         0.0.0.0
    Secondary DNS:      0.0.0.0
    Hardware Address:  00:00:86:4b:fc:bd
[/COLOR]
Applications --> System --> Network --> Wired Connection --> Properties has Roaming mode enabled. Disabling roaming mode and setting Configuration to Automatic Configuration (DHCP) makes no difference.
Note: Applications --> System --> Network --> Modem Connection is Disabled.

lspci returns the following relevant info:

[COLOR="RoyalBlue"]Ethernet Controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
Communication Controller: 3Com Corporation Mini PCI 56K Winmodem (rev 20)
[/COLOR]
Manually running dhclient3 I get the following response:

[COLOR="RoyalBlue"]Listening on LPF/eth0/00:00:86:4b:fc:bd
Sending on LPF/eth0/00:00:86:4b:fc:bd
Sending on Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/COLOR]
Anyone have any idea what the problem is/might be? I'm at a loss as to what's going on here...

---

### Post by tdb1001 on 2007-11-01
Additionally I should mention that I've already tried the following:

[LIST]
[*]Swapped the ethernet cables with the desktop system (known to be working).
[*]Swapped the dumb hub port with the desktop system.
[*]Removed the hub and plugged the A20m directly into the broadband modem's ethernet port.
[/LIST]

---


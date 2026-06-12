---
title: "Wi-Fi troubles, but perhaps an easy one?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Cilionelle on 2007-06-15
I have gone through the help on setting up the driver for my Broadcom-based Dell 1300 wi-fi card, and it all seems to be working well.  It has a lovely shining light on the side, it smells the wireless network (ESSID: wireless), but is unable to connect.  I think it must be a DHCP thing, and this is the message I get when running *sudo ifup eth1*:

There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:c6:24:8d:2c
Sending on   LPF/eth1/00:10:c6:24:8d:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'd like to know where to go from here.  I have the right WEP key (what's the difference between ASCII and hexadecimal WEP keys?), the right network, but they don't seem to want to connect...  The other interesting piece of information is that the subnet mask on the router is set at 255.255.255.0

Is there anything I'm missing?  And I'd be happy to provide more information for anyone who could help out!

Cheers!

---

### Post by Cilionelle on 2007-06-15
Bump

---

### Post by rich.bradshaw on 2007-06-15
The hexadecimal WEP key is the one to use, the ascii one just helps you remember it.

Are you sure the router is set up to DHCP properly? Subnet mask is correct.

Try adding a new network that doesn't exist, say called test, no wep key. Wait for it to start connecting, then connect to the real one with the correct key etc. My broadcom only works if I do this...

---

### Post by wieman01 on 2007-06-15
Please post this:
> sudo gedit /etc/network/interfaces
> sudo ifdown -v eth1
> sudo ifup -v eth1
> sudo iwlist scan

---

### Post by Cilionelle on 2007-06-15
**sudo gedit /etc/network/interfaces** =

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid wireless
wireless-key s:CC982C3B9C



auto eth1

-------------------------

**sudo ifdown -v eth1** =

Configuring interface eth1=eth1 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
RTNETLINK answers: No such process
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 11691
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:c6:24:8d:2c
Sending on   LPF/eth1/00:10:c6:24:8d:2c
Sending on   Socket/fallback
ifconfig eth1 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant

-----------------------------

**sudo ifup -v eth1** =

Configuring interface eth1=eth1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:c6:24:8d:2c
Sending on   LPF/eth1/00:10:c6:24:8d:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

-----------------------------------

**sudo iwlist scan** =

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:60:64:05:8C:57
                    ESSID:"wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-48 dBm  Noise level=-62 dBm
                    Extra: Last beacon: 16ms ago

There.  That answer your questions?  I hope so.  I will, barring other advice on this, test out the dummy network option, but that seems a bit odd to me.  Surely makers of such fine OSs (OSii?) are capable of a more... normal solution!

cheers!

---

### Post by wieman01 on 2007-06-15
Now update "interfaces":
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid wireless
wireless-key [COLOR="Red"]YOUR_HEX_WEP_KEY[/COLOR]
And restart the network:
> sudo /etc/init.d/networking restart
Any better? Please post this as well:
> route

---

### Post by Cilionelle on 2007-06-15
Nope, same message:

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5449
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:c6:24:8d:2c
Sending on   LPF/eth1/00:10:c6:24:8d:2c
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:c6:24:8d:2c
Sending on   LPF/eth1/00:10:c6:24:8d:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

As for "route":

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1

(all nicely tabbed, of course!)

Any ideas?  Ta!

---

### Post by phonixor on 2007-06-15
Question can you see how much connection you have behind your SID?

cause if you cant... you have an incorrect driver...

---

### Post by Cilionelle on 2007-06-16
How do I find out "how much connection" I have "behind my SID"?  I'm not sure what you mean.  I believe the driver is correct, but there are two almost identical ones listed for the wi-fi card I have.

---

### Post by Cilionelle on 2007-06-16
Hey!  Just for you guys who might look this thread up in months to come, try out DarkN00b's "the Easy Way" instruction thread.  It seems to work very well (82% of people say it worked for them...) and helped me out heaps!

Cheers!

---

### Post by Daisybobs on 2007-06-16
I have to do this for my RT2500 wireless card to work:

Turn off the Network manager in Preferences --> Sessions

and run these in a terminal:

sudo /etc/init.d/networking stop
sudo ifconfig eth0 down
sudo killall -9 NetworkManager
sudo killall -9 NetworkManagerD
sudo killall -9 dhclient3
sudo ifconfig eth0 up

Once I've done that, wifi-radar works properly. These changes reset on reboot. (apart from disabling the Network Manager icon in Gnome panel).

---


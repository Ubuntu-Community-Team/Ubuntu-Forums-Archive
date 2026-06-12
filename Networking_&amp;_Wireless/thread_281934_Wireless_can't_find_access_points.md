---
title: "Wireless can't find access points"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by kernco on 2006-10-21
Hi,

I am running Edgy Eft on an Averatec 2260-EK1 laptop.  It has a Ralink wireless chip.  In the Gnome networking took and iwconfig, it shows wlan0 and wmaster0 interfaces.  The networking window says they aren't configured, though.  When I go to configure it, the dropdown menu for ESSID is empty.

/var/log/syslog has a bunch of blocks like this:
Oct 21 21:32:26 dobby dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 21 21:32:34 dobby dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 21 21:32:49 dobby dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 21 21:33:06 dobby dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 21 21:33:26 dobby dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Oct 21 21:33:27 dobby dhclient: No DHCPOFFERS received.
Oct 21 21:33:27 dobby dhclient: No working leases in persistent database - sleeping.

And /etc/resolv.conf has:
search myhome.westell.com
nameserver 192.168.0.1

I have Verizon DSL with a D-Link router.  The Verizon modem is a Westell and it's IP is 192.168.1.1 and the D-Link's IP is 192.168.0.1.

I've tried using the network-manager package without success also.

Thanks,
Colin Kern

---


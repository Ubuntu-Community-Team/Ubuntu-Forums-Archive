---
title: "STILL no wireless networking!"
date: 2004-12-14
forum: Networking &amp; Wireless
---

### Post by paul.hendrick on 2004-12-14
Right i've tried everything now, but i cant get wireless networking to work with Ubuntu.

Under windows xp and fedora core 3, everything worked fine.
no matter what i try with the ubuntu network-admin too, i cant get my wireless network cards to enable.

I can add the wlan0 device after installing the ndiswrapper sources. the module loads no problems and everything.
but the network-admin too WILL NOT enable the wlan device.

how can I do it from the command line? using iwconfig doesnt work, because the settings only stick for 5 seconds or so.

any ideas?

---

### Post by EdCrypt on 2004-12-14
I just needed to remember my SSID in the install and, when loged ionto gnome, it was just working. In windows i need to write the ip, gateway, etc etc... I don't have dhcp, it falis to find one on the install, btw.
What is your wireless net. card?

---

### Post by paul.hendrick on 2004-12-14
On the box of the PCI card it says it's a Belkin Wireless Desktop Network card. 
the Hal device manager detects it as:
Broadcom BCM94306

that card is in the Desktop machine, and works under windows, but refuses to work with ubuntu(with the drivers from the install cd).

the card in my laptop is detected as a neti2220 card, and again i'm using the official drivers.

---

### Post by EdCrypt on 2004-12-14
If you get this info from HAL, maybe that is  some problem in the configuration. Do you use DHCP? Or static IP?
There is no one more in this forum using this card? I use a Linksys...

---

### Post by paul.hendrick on 2004-12-14
i've verified everything under windows xp, and i'm using official drivers.
i'm trying to set up machine1 so that it uses eth0 to connect (wired) to my router, and the wlan0 device is for my laptop to connect to with it's wireless card. so i can go online with the laptop, without being wired. in the network-admin tool, i chose dhcp for my connection.
i've just made a post to the ubuntu-users mailing list, which is this:

Machine one:
Stock ubuntu kernel, ndiswrapper-0.12(built from sources), official
windows inf driver from the cd.

ndiswrapper -l shows:
bcmwl5  driver present, hardware present
AND the led is lit on the back of the computer box so the card is on.
network-admin WILL NOT allow me to enable this device. i've tried with
and without network keys, and with essid numerous names. i've played
with the wlan0 device in the /etc/network/interfaces a bit, and i've
tried keeping it with what the network-admin tool sets it to.
it is currently:
iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid linux_wlan
wireless_key s:*************
wireless_mode ad-hoc
auto wlan0

it's only with the ubuntu network-admin too i can make permanent changes
to the wlan0 connection, if i use the iwconfig command line the changes
only last 5 seconds until they're restored to the ones that ubuntu
network-admin made(though iwconfig command doesnt alter the interfaces
file).
if i do
iwconfig wlan0 essid on mode ad-hoc key s:blahblahblah essid
"linux_wlan"
i can do wlist wlan0 scan on MACHINE2, and those details are all picked
up. so the cards are talking, to a point.
however, because the iwconfig command only changes things for a matter
of seconds, i cant connect anything. i NEED to make the network-admin
setup the wlan0 device, and activate it. How can I? should I attach my
dmesg file or anything for people to have a look at?

if I do ifup wlan0 on machine1, I get the output pasted below.
thanks for reading.

Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:11:50:1b:d8:26
Sending on   LPF/wlan0/00:11:50:1b:d8:26
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---


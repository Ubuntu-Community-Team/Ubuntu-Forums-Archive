---
title: "Sudden network problems"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by darrenc on 2007-08-09
After my most recent update, I've lost my network access.  Everything I know to check looks correct, so I'm at a loss to try to fix it.

The settings have been constant for a couple years now, so I know it normally works with no problem.  The problem was present immediately upon reboot from the last update, so I'm sure some configuration file somewhere got changed, but I have no clue what it could be.  Here's the log of what was updated on my last update:

Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
firefox (2.0.0.5+1-0ubuntu1) to 2.0.0.6+1-0ubuntu1
firefox-gnome-support (2.0.0.5+1-0ubuntu1) to 2.0.0.6+1-0ubuntu1
gimp (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
gimp-data (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
gimp-python (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libgimp2.0 (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
libgl1-mesa-dri (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libgl1-mesa-glx (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libglu1-mesa (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libnspr4 (2:1.firefox2.0.0.5+1-0ubuntu1) to 2:1.firefox2.0.0.6+1-0ubuntu1
libnss3 (2:1.firefox2.0.0.5+1-0ubuntu1) to 2:1.firefox2.0.0.6+1-0ubuntu1
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
mesa-utils (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
python-launchpad-bugs (0.1.13) to 0.1.13.2
tcpdump (3.9.5-2) to 3.9.5-2ubuntu1
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4

I've downgraded most of these back to the prior version, with no change.

My network reports that it's up and running normally, but it has no contact whatsoever with anything outside my system - no router, no external hard drive, no other systems on the network, no internet gateway - nothing.

ifconfig reveals the following for eth0:

eth0      Link encap:Ethernet  HWaddr 00:50:2C:xx:xx:xx 
          inet addr:192.168.1.151  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:2cff:fe06:1b0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 

I can ping the network card with no problem:

ping 192.168.1.151
PING 192.168.1.151 (192.168.1.151) 56(84) bytes of data.
64 bytes from 192.168.1.151: icmp_seq=1 ttl=64 time=0.086 ms
64 bytes from 192.168.1.151: icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from 192.168.1.151: icmp_seq=3 ttl=64 time=0.052 ms
64 bytes from 192.168.1.151: icmp_seq=4 ttl=64 time=0.053 ms

--- 192.168.1.151 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.050/0.060/0.086/0.015 ms

But if I ping the router:

ping 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
From 192.168.1.151 icmp_seq=2 Destination Host Unreachable
From 192.168.1.151 icmp_seq=3 Destination Host Unreachable
From 192.168.1.151 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.101 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5000ms
, pipe 3


The router is up - the rest of the network is working normally, only this system isn't seeing it.  It's dual boot, and the network works just like normal in Windows so the hardware hasn't failed.  I've even tried rebooting the router and external hard drive, and disconnecting everything but the router and everything but the external hard drive.  Whatever I plug in to the other end of the ethernet cable is just not being seen.

Any ideas?  I can post any other info that may help.

Thanks.

---

### Post by bmartin on 2007-08-09
What program are you using to retrieve you IP address and set your network settings? Do you use static or dynamic (DHCP) routing? What is the output of **sudo dhclient eth0**? Have you messed around with your **/etc/network/interfaces** file at all?

---

### Post by darrenc on 2007-08-09
> **bmartin said:**
> What program are you using to retrieve you IP address and set your network settings? Do you use static or dynamic (DHCP) routing? What is the output of **sudo dhclient eth0**? Have you messed around with your **/etc/network/interfaces** file at all?

I use static addresses throughout my local network.  Normally I have 3 systems and an external harddrive connected by cables to a D-Link wireless router.  One of the systems (not the one with the problem) connects to a Wi-Fi system and functions as my gateway.  The router has the ability to assign ip addresses via DHCP and normally does so for any system that asks for one.

If I change to DHCP, it still fails - as it apparently can't even see the router.

dhclient outputs:

> dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:2c:xx:xx:xx
Sending on   LPF/eth0/00:50:2c:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I've made no changes to my interfaces file, and it reads as follows:

> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface rausb0 inet dhcp
wireless-essid Fair Harbor WiFi4

auto rausb0


iface eth0 inet static
address 192.168.1.151
netmask 255.255.255.0
gateway 192.168.1.99

auto eth0

Note that rausb0 is not normally active on this system.  This is the Wi-Fi connection that is normally handled by the gateway system, with the problem system (which is my main desktop system) accessing the internet through that gateway system - I had to move it to this system for now since I can't get to the gateway via eth0.

---

### Post by bmartin on 2007-08-09
It appears that your system can't lease the given IP from your gateway. Try removing the following lines (back up your file first):
```
iface eth0 inet static
address 192.168.1.151
netmask 255.255.255.0
gateway 192.168.1.99
```

And adding the following lines:
```
auto eth0
iface eth0 inet dhcp
```

Then restart your computer.

Even if you have static IPs set at your router, DHCP should lease the correct IP address.

---

### Post by darrenc on 2007-08-09
Still no connection with those changes.

ifconfig shows:

> eth0      Link encap:Ethernet  HWaddr 00:50:2C:xx:xx:xx 
          inet6 addr: fe80::250:2cff:fe06:1b0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:2C:xx:xx:xx  
          inet addr:169.254.1.99  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe000 

and dhclient is still the same:

> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:2c:xx:xx:xx
Sending on   LPF/eth0/00:50:2c:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Where it got the ip address 169.254.1.99 I have no clue.  That had to be done internally, as it's not even in the range (or netmask) that my router is set to give out.

And one more thing that I noticed in the process here, even the light on my router corresponding to the socket it's plugged into isn't on.  Just to check I rebooted into Windows to check the light and it promptly lights right up and the network in intact.  Back to Ubuntu - dead again.

---

### Post by darrenc on 2007-08-09
Problem solved.

I did a windows update at the same time I did my Ubuntu update, and when I checked what was updated by windows I found it had put in a new driver for my nic.  I rolled that driver back and booted back into Ubuntu and my network is working again.

So that fixed it, but how on earth did a new *windows* driver (supposedly not a rom flash, just a driver) kill the network when it's booted in Ubuntu???

I know windows has the power to kill computers on a whim, but I've never heard of it being able to kill one when windows is not even running!

Thanks for your help anyway, bmartin.

---

### Post by bmartin on 2007-08-09
The Windows driver and Linux driver don't have any effect on one another, unless the firmware was modified (that's a different story). I don't know what the problem was.

---

### Post by clive_pearce on 2007-08-09
I have just replied to another post with the same problem.

I had installed Ubuntu with Wubi. I rolled back my driver & it fixed the problem for me. 

Perhaps someone needs to make this fix a sticky?

---


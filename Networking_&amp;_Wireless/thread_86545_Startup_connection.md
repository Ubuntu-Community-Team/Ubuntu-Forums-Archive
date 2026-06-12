---
title: "Startup connection"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by Pyrocuror on 2005-11-05
I am having trouble trying to tell Ubuntu to use connection eth2 at startup instead of the default (per installation) eth1.  Here is what /etc/network/interfaces looks like:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth2

# The primary network interface
iface eth2 inet dhcp
wireless-essid any

auto eth2

---

### Post by Pyrocuror on 2005-11-12
bump

Nobody can help me have eth2 ready to go when the laptop turns on?  There must be a way instead of going into the Networking utility and activating eth2 every time I turn it on.

---

### Post by Lambert on 2005-11-12
Open the networking utility system>admin>networking, choose eth1, click properties.

The line that says "enable this connection" is it checked? If so you can uncheck it and it shouldn't use eth1 at all.

If not, sorry I couldn't offer any more.

---

### Post by Pyrocuror on 2005-11-12
Yup tried that.  eth1 is disabled.

---

### Post by darth_vector on 2005-11-13
can you post the output of ifconfig please.

---

### Post by Pyrocuror on 2005-11-15
eth2      Link encap:Ethernet  HWaddr 00:40:96:28:F8:9D
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:96ff:fe28:f89d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228 errors:75 dropped:0 overruns:0 frame:75
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:9 txqueuelen:1000
          RX bytes:117227 (114.4 KiB)  TX bytes:43781 (42.7 KiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:676304 (660.4 KiB)  TX bytes:676304 (660.4 KiB)

---

### Post by Pyrocuror on 2005-12-03
Bumping this as I still haven't figured out a solution.  Anyone?

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=Pyrocuror]eth2      Link encap:Ethernet  HWaddr 00:40:96:28:F8:9D
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:96ff:fe28:f89d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228 errors:75 dropped:0 overruns:0 frame:75
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:9 txqueuelen:1000
          RX bytes:117227 (114.4 KiB)  TX bytes:43781 (42.7 KiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:676304 (660.4 KiB)  TX bytes:676304 (660.4 KiB)[/QUOTE]

Was this the output right after you booted up?  Because it looks like eth2 is configured with an IP address.  What symptoms exactly are you experiencing that makes you think it isn't working?

---

### Post by Pyrocuror on 2005-12-04
No not right after booting up.  The problem isn't getting eth2 to work, the problem is I want Ubuntu to start eth2 automatically upon booting up.  Currently it starts eth1 up during the bootup.

---


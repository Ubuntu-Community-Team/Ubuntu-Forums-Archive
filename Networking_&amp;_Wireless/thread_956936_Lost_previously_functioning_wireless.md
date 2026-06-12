---
title: "Lost previously functioning wireless"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by owlcroft on 2008-10-23
On a Thinkpad T61, I have had satisfactory wireless from the outset.  The other day, I took the laptop away from home for the first time; when I came back, I had no wireless.  Fortunately, I have a wired connection, but I need the wireless back.

I know little of Ubuntu or Linux in general, and less (if possible) about wireless.  Here is as much data as I have now--if anyoine has suggestions, I'd be grateful.

Ubuntu 8.04.1

System -> Administration -> Network shows:

Wired Connection (Roaming mode enabled)
Point-to-point connection (This network configuration is not enabled)

Clicking the toolbar Network icon and selecting "Edit Wireless Networks" brings up a window in which, under "Networks", my existing connection (named "walker") appears: clicking on it brings up a set of properties that I do not understand but which look familiar, with "bssids" = 00:1C:10:27:AA:1D

I also used a few tools that a few Googles suggested; here are the results.

```
lshw -C network
---------------

  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:18:b7:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 ip=192.168.200.105 latency=0 module=e1000 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945


lspci
-----

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)


/etc/network/interfaces
-----------------------
auto lo
iface lo inet loopback
```

So, as best I can see, I have a working Ethernet card with a properly installed standard driver, but it doesn't show in the Network manager window and doesn't work.

Any ideas, please?

---

### Post by owlcroft on 2008-10-26
(bump)

Pretty please?

---

### Post by owlcroft on 2008-10-27
Here is a more complete set of data read from various info commands:

```
lshw -C network
===============

        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1e:37:18:b7:dc
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 ip=192.168.200.105 latency=0 module=e1000 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945


lsmod | grep e1000
==================

e1000                 126016  0


lsmod | grep iwl3945
====================
iwl3945                89844  0 
iwlwifi_mac80211      218980  1 iwl3945
 

iwconfig
========

lo        no wireless extensions.
eth0      no wireless extensions.


dhclient -r eth0
================

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:37:18:b7:dc
Sending on   LPF/eth0/00:1e:37:18:b7:dc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.200.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.


ifconfig
========

eth0      Link encap:Ethernet  HWaddr 00:1e:37:18:b7:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1922708 (1.8 MB)  TX bytes:322035 (314.4 KB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131900 (128.8 KB)  TX bytes:131900 (128.8 KB)


iwlist
======

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.


lspci -nn
=========

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)


cat /etc/resolv.config
======================

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5546
#
### END INFO

search http://192.168.200.1/index.asp

nameserver 199.3.239.6
nameserver 208.67.222.222

```

I'm beginning to wonder if the hardware broke.

Doesn't *anyone* have any ideas?

---

### Post by owlcroft on 2008-10-27
Solved.

In a way, it *was* a hardware "failure".

It turns out that unbeknownst to me (and, I gather, from the page where I finally found the answer, a large number of other owners of the T61 Thinkpad laptop), there is a small, nearly invisible physical slide switch just under the front edge of the clamshell, and that switch can turn off the radio!

Obviously, in both the other fellow's and my cases, the switch got bumped over during transportation of the unit.  Apparently, none of the usual software is smart enough to notify a user that the radio is physically disabled by the laptop itself.

(The clue turned up in a couple of lines of dmesg output--I myself had never even heard of the command, but this other fellow ran it and extracted the radio-related output, after which someone was able to tie it back to that nealy invisible switch.)

Gaahhh!!

---

